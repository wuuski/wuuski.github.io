<script>
	import { slide } from 'svelte/transition';

	const artworks = [
		{
			title: 'Grandpas Garden',
			image: '/grandpapatio.png',
			alt: 'Artwork titled Grandpa Patio'
		},
		{
			title: 'Edgar',
			image: '/Edgar.png',
			alt: 'Watercolor painting of an orange cat lying beside a person'
		},
		{
			title: 'The Cozy Hole-in-the-Tree',
			image: '/The Cozy Hole-in-the-Tree.png',
			alt: 'Digital painting of a magical home built into a forest tree'
		},
		{
			title: 'Scientists’ Refuge',
			image: "/Scientists' Refuge.png",
			alt: 'Artwork titled Scientists’ Refuge'
		},
		{
			title: 'Betty',
			image: '/Betty.png',
			alt: 'Artwork titled Betty'
		},
		{
			title: 'Angela',
			image: '/Angela.png',
			alt: 'Artwork titled Angela'
		},
		{
			title: 'The Shell',
			image: '/The Shell.png',
			alt: 'Artwork titled The Shell'
		},
		{
			title: 'Memory Project',
			image: '/girlpainting.png',
			alt: 'Painting of a girl'
		},
		{
			title: 'Misha',
			image: '/mishpainting.png',
			alt: 'Artwork titled Mish Painting'
		}
	];
</script>

<svelte:head>
	<title>Art | Angela Wu</title>
	<meta
		name="description"
		content="A selection of artwork and illustrations created by Angela Wu."
	/>
</svelte:head>

<main class="art-page">
	<section
		class="art-panel"
		in:slide={{
			duration: 850,
			delay: 120
		}}
	>
		<header class="page-header">
			<p class="eyebrow">Selected work</p>

			<h1>Art</h1>

			<p class="intro">
				I’ve loved making visual art for as long as I can remember. Here are
				some of my favorite paintings and illustrations from over the years.
			</p>
		</header>

		<div class="art-gallery">
			{#each artworks as artwork, index}
				<figure
					class="art-card"
					in:slide={{
						duration: 600,
						delay: 220 + index * 90
					}}
				>
					<a
						class="art-image"
						href={artwork.image}
						target="_blank"
						rel="noopener noreferrer"
						aria-label={`View ${artwork.title} at full size`}
					>
						<img
							src={artwork.image}
							alt={artwork.alt}
							loading={index > 1 ? 'lazy' : 'eager'}
						/>
					</a>

					<figcaption class="art-caption">
						<div>
							<p class="art-category">Selected artwork</p>
							<h2>{artwork.title}</h2>
						</div>

						<a
							class="art-link"
							href={artwork.image}
							target="_blank"
							rel="noopener noreferrer"
						>
							View full size
							<span aria-hidden="true">↗</span>
						</a>
					</figcaption>
				</figure>
			{/each}
		</div>
	</section>
</main>

<style>
	:global(body) {
		margin: 0;
	}

	.art-page {
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

	.art-panel {
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

	.art-gallery {
		columns: 2;
		column-gap: clamp(1.4rem, 3vw, 2.25rem);
	}

	.art-card {
		width: 100%;
		box-sizing: border-box;

		display: inline-flex;
		flex-direction: column;
		vertical-align: top;

		margin: 0 0 clamp(1.4rem, 3vw, 2.25rem);

		break-inside: avoid;
		overflow: hidden;

		background: #f7eee3;

		border: 2px solid rgba(91, 72, 61, 0.72);
		border-radius: 24px;

		box-shadow: 0 10px 28px rgba(29, 39, 42, 0.13);

		transition:
			transform 0.2s ease,
			box-shadow 0.2s ease;
	}

	.art-card:hover {
		transform: translateY(-4px);
		box-shadow: 0 16px 34px rgba(29, 39, 42, 0.19);
	}

	.art-image {
		display: flex;
		align-items: center;
		justify-content: center;

		padding: clamp(0.8rem, 2vw, 1.2rem);

		background: #c4cdb2;
		border-bottom: 2px solid rgba(91, 72, 61, 0.52);

		overflow: hidden;
	}

	.art-image img {
		width: 100%;
		height: auto;
		display: block;

		object-fit: contain;
		border-radius: 14px;

		transition: transform 0.3s ease;
	}

	.art-card:hover .art-image img {
		transform: scale(1.012);
	}

	.art-image:focus-visible,
	.art-link:focus-visible {
		outline: 4px solid white;
		outline-offset: 4px;
	}

	.art-caption {
		display: flex;
		align-items: center;
		justify-content: space-between;
		gap: 1.25rem;

		padding: 1.2rem 1.4rem;

		color: #3f4253;
	}

	.art-category {
		margin: 0 0 0.25rem;

		font-family:
			'Segoe UI',
			Tahoma,
			Geneva,
			Verdana,
			sans-serif;

		font-size: 0.75rem;
		font-weight: 750;
		letter-spacing: 0.09em;
		text-transform: uppercase;

		color: #9a6878;
	}

	h2 {
		margin: 0;

		font-family:
			'Gill Sans',
			'Gill Sans MT',
			Calibri,
			'Trebuchet MS',
			sans-serif;

		font-size: clamp(1.4rem, 2.4vw, 2rem);
		line-height: 1.15;

		color: #3f4253;
	}

	.art-link {
		flex-shrink: 0;

		display: inline-flex;
		align-items: center;
		gap: 0.4rem;

		padding: 0.6rem 0.85rem;

		background: #596b50;
		border: 2px solid #465540;
		border-radius: 999px;

		font-family:
			'Segoe UI',
			Tahoma,
			Geneva,
			Verdana,
			sans-serif;

		font-size: 0.82rem;
		font-weight: 750;

		color: white;
		text-decoration: none;

		transition:
			transform 0.18s ease,
			background 0.18s ease;
	}

	.art-link:hover {
		background: #6b7d61;
		transform: translateY(-2px);
	}

	@media (max-width: 800px) {
		.art-page {
			padding-top: 7rem;
			background-attachment: scroll;
		}

		.art-panel {
			padding: 1rem;
			border-radius: 22px;
		}

		.art-gallery {
			columns: 1;
		}
	}

	@media (max-width: 500px) {
		.art-page {
			padding-right: 0.65rem;
			padding-left: 0.65rem;
			padding-bottom: 2rem;
		}

		.page-header {
			margin-bottom: 1.4rem;
		}

		.art-card {
			margin-bottom: 1.2rem;
		}

		.art-image {
			padding: 0.65rem;
		}

		.art-caption {
			align-items: flex-start;
			flex-direction: column;
			gap: 0.85rem;

			padding: 1rem;
		}

		.art-link {
			font-size: 0.78rem;
		}
	}

	@media (prefers-reduced-motion: reduce) {
		.art-card,
		.art-image img,
		.art-link {
			transition: none;
		}
	}
</style>