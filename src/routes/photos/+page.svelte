<script>
	import { slide } from 'svelte/transition';

	const photos = [
		{
			title: 'Artist’s Corner',
			image: '/artstation.jpg',
			alt: 'A warmly lit artist workspace beside an open blue window',
			orientation: 'portrait'
		},
		{
			title: 'Takeoff',
			image: '/birdfountain.jpg',
			alt: 'A small bird lifting away from a fountain with water splashing beneath it',
			orientation: 'landscape'
		},
		{
			title: 'In Motion',
			image: '/dancers.jpg',
			alt: 'Traditional dancers performing in colorful embroidered clothing',
			orientation: 'landscape'
		},
		{
			title: 'Gulls',
			image: '/gulls.jpg',
			alt: 'Two gulls standing near the water, one holding a crab',
			orientation: 'landscape'
		},
		{
			title: 'Old Town',
			image: '/oldtown.jpg',
			alt: 'A sunlit old-town street lined with shops and hanging signs',
			orientation: 'landscape'
		},
		{
			title: 'Do You Remember?',
			image: '/porter.jpg',
			alt: 'A concert stage illuminated in blue light with text projected behind the performers',
			orientation: 'landscape'
		},
		{
			title: 'After Hours',
			image: '/shop.jpg',
			alt: 'A dimly lit shop interior with colorful papel picado decorations',
			orientation: 'landscape'
		},
		{
			title: 'Terracotta',
			image: '/terracotta.jpg',
			alt: 'Rows of Terracotta Army figures viewed from above',
			orientation: 'landscape'
		},
		{
			title: 'Village View',
			image: '/village.jpg',
			alt: 'A balcony overlooking a mountain village under a blue sky',
			orientation: 'landscape'
		},
		{
			title: 'Waterfall',
			image: '/waterfall.jpg',
			alt: 'A small waterfall surrounded by dense greenery and lily pads',
			orientation: 'landscape'
		}
	];
</script>

<svelte:head>
	<title>Photography | Angela Wu</title>

	<meta
		name="description"
		content="A collection of photographs by Angela Wu capturing quiet moments, movement, wildlife, and places."
	/>
</svelte:head>

<main class="photo-page">
	<section
		class="photo-panel"
		in:slide={{
			duration: 850,
			delay: 120
		}}
	>
		<header class="page-header">
			<p class="eyebrow">Selected photographs</p>

			<h1>Photos</h1>

			<p class="intro">
				A collection of moments, places, and little details that made me stop
				and look twice.
			</p>
		</header>

		<div class="photo-gallery">
			{#each photos as photo, index}
				<figure
					class="photo-card"
					class:portrait={photo.orientation === 'portrait'}
					in:slide={{
						duration: 600,
						delay: 220 + index * 80
					}}
				>
					<a
						class="photo-image"
						href={photo.image}
						target="_blank"
						rel="noopener noreferrer"
						aria-label={`View ${photo.title} at full size`}
					>
						<img
							src={photo.image}
							alt={photo.alt}
							loading={index > 2 ? 'lazy' : 'eager'}
						/>

						<div class="photo-overlay">
							<span>{photo.title}</span>
							<span aria-hidden="true">↗</span>
						</div>
					</a>
				</figure>
			{/each}
		</div>
	</section>
</main>

<style>
	:global(body) {
		margin: 0;
	}

	.photo-page {
		min-height: 100vh;
		box-sizing: border-box;

		padding:
			clamp(7.25rem, 10vw, 8.5rem)
			clamp(1rem, 3vw, 2.5rem)
			4rem;

		background-image:
			linear-gradient(
				rgba(164, 202, 116, 0.06),
				rgba(164, 202, 116, 0.06)
			),
			url('/grass_bg.png');

		background-size: cover;
		background-position: center;
		background-attachment: fixed;
	}

	.photo-panel {
		width: min(1320px, 100%);
		margin: 0 auto;
		box-sizing: border-box;

		padding: clamp(1.2rem, 2.8vw, 2.3rem);

		background: rgba(76, 96, 82, 0.5);

		backdrop-filter: blur(9px);
		-webkit-backdrop-filter: blur(9px);

		border: 2px solid rgba(69, 63, 49, 0.5);
		border-radius: 28px;

		box-shadow: 0 18px 45px rgba(35, 49, 42, 0.18);
	}

	.page-header {
		max-width: 760px;
		margin: 0 auto clamp(1.8rem, 4vw, 2.6rem);

		text-align: center;
		color: #fff8ea;
	}

	.eyebrow {
		margin: 0 0 0.35rem;

		font-family:
			'Segoe UI',
			Tahoma,
			Geneva,
			Verdana,
			sans-serif;

		font-size: 0.82rem;
		font-weight: 750;
		letter-spacing: 0.15em;
		text-transform: uppercase;

		color: #dce9bd;
	}

	h1 {
		margin: 0;

		font-family:
			'Gill Sans',
			'Gill Sans MT',
			Calibri,
			'Trebuchet MS',
			sans-serif;

		font-size: clamp(2.8rem, 5vw, 4.25rem);
		line-height: 1;

		color: #fff8ea;
	}

	.intro {
		max-width: 680px;
		margin: 0.75rem auto 0;

		font-family:
			'Segoe UI',
			Tahoma,
			Geneva,
			Verdana,
			sans-serif;

		font-size: clamp(1rem, 1.5vw, 1.16rem);
		line-height: 1.55;

		color: rgba(255, 248, 234, 0.88);
	}

	.photo-gallery {
		columns: 3;
		column-gap: clamp(1rem, 2.5vw, 1.75rem);
	}

	.photo-card {
		width: 100%;
		box-sizing: border-box;

		display: inline-block;
		vertical-align: top;

		margin: 0 0 clamp(1rem, 2.5vw, 1.75rem);

		break-inside: avoid;
		overflow: hidden;

		background: #f7eee3;
		border: 2px solid rgba(91, 72, 61, 0.72);
		border-radius: 22px;

		box-shadow: 0 10px 28px rgba(29, 39, 42, 0.13);

		transition:
			transform 0.2s ease,
			box-shadow 0.2s ease;
	}

	.photo-card:hover {
		transform: translateY(-4px);
		box-shadow: 0 16px 34px rgba(29, 39, 42, 0.2);
	}

	.photo-image {
		position: relative;

		display: block;
		overflow: hidden;

		background: #c4cdb2;
		text-decoration: none;
	}

	.photo-image img {
		width: 100%;
		height: auto;
		display: block;

		transition:
			transform 0.35s ease,
			filter 0.35s ease;
	}

	.photo-overlay {
		position: absolute;
		inset: auto 0 0;

		display: flex;
		align-items: center;
		justify-content: space-between;
		gap: 1rem;

		padding: 1.15rem 1.2rem;

		background: linear-gradient(
			to top,
			rgba(34, 38, 40, 0.8),
			rgba(34, 38, 40, 0)
		);

		font-family:
			'Segoe UI',
			Tahoma,
			Geneva,
			Verdana,
			sans-serif;

		font-size: 0.95rem;
		font-weight: 700;

		color: white;

		opacity: 0;
		transform: translateY(8px);

		transition:
			opacity 0.25s ease,
			transform 0.25s ease;
	}

	.photo-overlay > span:last-child {
		flex-shrink: 0;
		font-size: 1.1rem;
	}

	.photo-card:hover img {
		transform: scale(1.025);
		filter: brightness(0.92);
	}

	.photo-card:hover .photo-overlay,
	.photo-image:focus-visible .photo-overlay {
		opacity: 1;
		transform: translateY(0);
	}

	.photo-image:focus-visible {
		outline: 4px solid white;
		outline-offset: 4px;
	}

	@media (max-width: 1000px) {
		.photo-gallery {
			columns: 2;
		}
	}

	@media (max-width: 800px) {
		.photo-page {
			padding-top: 7rem;
			background-attachment: scroll;
		}

		.photo-panel {
			padding: 1rem;
			border-radius: 22px;
		}
	}

	@media (max-width: 600px) {
		.photo-gallery {
			columns: 1;
		}
	}

	@media (max-width: 500px) {
		.photo-page {
			padding-right: 0.65rem;
			padding-left: 0.65rem;
			padding-bottom: 2rem;
		}

		.page-header {
			margin-bottom: 1.4rem;
		}

		.photo-card {
			margin-bottom: 1.2rem;
		}

		.photo-overlay {
			padding: 1rem;
			font-size: 0.88rem;
		}
	}

	@media (hover: none) {
		.photo-overlay {
			opacity: 1;
			transform: translateY(0);
		}
	}

	@media (prefers-reduced-motion: reduce) {
		.photo-card,
		.photo-image img,
		.photo-overlay {
			transition: none;
		}
	}
</style>