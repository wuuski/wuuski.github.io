<script>
	import { browser } from '$app/environment';
	import { onDestroy } from 'svelte';
	import { fade, scale, slide } from 'svelte/transition';

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
			title: 'Terracotta',
			image: '/terracotta.jpg',
			alt: 'Rows of Terracotta Army figures viewed from above',
			orientation: 'landscape'
		},
		{
			title: 'Drifting',
			image: '/drifting.jpg',
			alt: 'A person drifting in the ocean on an inflatable device at night',
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
		},
		{
			title: 'After Hours',
			image: '/shop.jpg',
			alt: 'A dimly lit shop interior with colorful papel picado decorations',
			orientation: 'landscape'
		}
	];

	let selectedIndex = null;

	$: selectedPhoto =
		selectedIndex === null ? null : photos[selectedIndex];

	$: if (browser) {
		document.body.style.overflow =
			selectedIndex === null ? '' : 'hidden';
	}

	onDestroy(() => {
		if (browser) {
			document.body.style.overflow = '';
		}
	});

	function openPhoto(index) {
		selectedIndex = index;
	}

	function closePhoto() {
		selectedIndex = null;
	}

	function showPrevious() {
		if (selectedIndex === null) return;

		selectedIndex =
			(selectedIndex - 1 + photos.length) % photos.length;
	}

	function showNext() {
		if (selectedIndex === null) return;

		selectedIndex = (selectedIndex + 1) % photos.length;
	}

	function handleKeydown(event) {
		if (selectedIndex === null) return;

		if (event.key === 'Escape') {
			closePhoto();
		}

		if (event.key === 'ArrowLeft') {
			showPrevious();
		}

		if (event.key === 'ArrowRight') {
			showNext();
		}
	}
</script>

<svelte:window on:keydown={handleKeydown} />

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
					<button
						class="photo-image"
						type="button"
						on:click={() => openPhoto(index)}
						aria-label={`Open ${photo.title} in gallery`}
					>
						<img
							src={photo.image}
							alt={photo.alt}
							loading={index > 2 ? 'lazy' : 'eager'}
						/>

						<span class="photo-overlay">
							<span>{photo.title}</span>
							<span aria-hidden="true">↗</span>
						</span>
					</button>
				</figure>
			{/each}
		</div>
	</section>
</main>

{#if selectedPhoto}
	<div
		class="lightbox"
		role="dialog"
		aria-modal="true"
		aria-label={`Viewing ${selectedPhoto.title}`}
		on:click={closePhoto}
		in:fade={{ duration: 180 }}
		out:fade={{ duration: 150 }}
	>
		<button
			class="close-button"
			type="button"
			on:click|stopPropagation={closePhoto}
			aria-label="Close gallery"
		>
			<span aria-hidden="true">×</span>
		</button>

		<button
			class="gallery-arrow previous"
			type="button"
			on:click|stopPropagation={showPrevious}
			aria-label="View previous photo"
		>
			<span aria-hidden="true">‹</span>
		</button>

		<div
			class="lightbox-content"
			on:click|stopPropagation
			in:scale={{
				duration: 220,
				start: 0.96
			}}
		>
			<img
				class="lightbox-image"
				src={selectedPhoto.image}
				alt={selectedPhoto.alt}
			/>

			<div class="lightbox-footer">
				<div>
					<p class="lightbox-label">Selected photograph</p>
					<h2>{selectedPhoto.title}</h2>
				</div>

				<p class="counter">
					{selectedIndex + 1} / {photos.length}
				</p>
			</div>
		</div>

		<button
			class="gallery-arrow next"
			type="button"
			on:click|stopPropagation={showNext}
			aria-label="View next photo"
		>
			<span aria-hidden="true">›</span>
		</button>
	</div>
{/if}

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
		border: 2px solid rgba(247, 238, 227, 0.92);
		border-radius: 20px;

		box-shadow: 0 9px 24px rgba(29, 39, 42, 0.15);

		transition:
			transform 0.2s ease,
			box-shadow 0.2s ease;
	}

	.photo-card:hover {
		transform: translateY(-4px);
		box-shadow: 0 15px 32px rgba(29, 39, 42, 0.22);
	}

	.photo-image {
		position: relative;

		width: 100%;
		display: block;

		margin: 0;
		padding: 0;

		background: transparent;
		border: 0;

		color: inherit;
		text-align: left;

		overflow: hidden;
		cursor: pointer;
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

		box-sizing: border-box;
		width: 100%;

		padding: 2.6rem 1.15rem 1rem;

		background: linear-gradient(
			to top,
			rgba(26, 28, 27, 0.82),
			rgba(26, 28, 27, 0)
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
		filter: brightness(0.91);
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

	.lightbox {
		position: fixed;
		inset: 0;
		z-index: 1000;

		display: flex;
		align-items: center;
		justify-content: center;

		box-sizing: border-box;
		padding: clamp(1rem, 4vw, 3rem);

		background: rgba(10, 11, 10, 0.94);
		backdrop-filter: blur(12px);
		-webkit-backdrop-filter: blur(12px);
	}

	.lightbox-content {
		width: min(1200px, calc(100vw - 10rem));
		height: min(88vh, 920px);

		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;

		min-width: 0;
	}

	.lightbox-image {
		max-width: 100%;
		max-height: calc(100% - 82px);

		width: auto;
		height: auto;

		display: block;
		object-fit: contain;

		border-radius: 5px;

		box-shadow: 0 22px 70px rgba(0, 0, 0, 0.5);
	}

	.lightbox-footer {
		width: min(1000px, 100%);

		display: flex;
		align-items: flex-end;
		justify-content: space-between;
		gap: 2rem;

		box-sizing: border-box;
		padding-top: 1.1rem;

		color: white;
	}

	.lightbox-label {
		margin: 0 0 0.18rem;

		font-family:
			'Segoe UI',
			Tahoma,
			Geneva,
			Verdana,
			sans-serif;

		font-size: 0.68rem;
		font-weight: 750;
		letter-spacing: 0.13em;
		text-transform: uppercase;

		color: rgba(255, 255, 255, 0.55);
	}

	.lightbox-footer h2 {
		margin: 0;

		font-family:
			'Gill Sans',
			'Gill Sans MT',
			Calibri,
			'Trebuchet MS',
			sans-serif;

		font-size: clamp(1.15rem, 2vw, 1.65rem);
		font-weight: 500;

		color: rgba(255, 255, 255, 0.92);
	}

	.counter {
		flex-shrink: 0;
		margin: 0;

		font-family:
			'Segoe UI',
			Tahoma,
			Geneva,
			Verdana,
			sans-serif;

		font-size: 0.85rem;
		letter-spacing: 0.08em;

		color: rgba(255, 255, 255, 0.65);
	}

	.close-button,
	.gallery-arrow {
		position: fixed;
		z-index: 1002;

		display: grid;
		place-items: center;

		margin: 0;
		padding: 0;

		background: rgba(255, 255, 255, 0.045);
		border: 1px solid rgba(255, 255, 255, 0.15);
		border-radius: 999px;

		color: rgba(255, 255, 255, 0.82);

		cursor: pointer;

		transition:
			background 0.18s ease,
			color 0.18s ease,
			transform 0.18s ease;
	}

	.close-button:hover,
	.gallery-arrow:hover {
		background: rgba(255, 255, 255, 0.12);
		color: white;
	}

	.close-button:focus-visible,
	.gallery-arrow:focus-visible {
		outline: 3px solid white;
		outline-offset: 4px;
	}

	.close-button {
		top: 1.25rem;
		right: 1.25rem;

		width: 44px;
		height: 44px;

		font-size: 1.9rem;
		font-weight: 200;
		line-height: 1;
	}

	.close-button:hover {
		transform: rotate(3deg) scale(1.04);
	}

	.gallery-arrow {
		top: 50%;
		transform: translateY(-50%);

		width: 52px;
		height: 52px;

		font-family: Georgia, serif;
		font-size: 2.25rem;
		line-height: 1;
	}

	.gallery-arrow:hover {
		transform: translateY(-50%) scale(1.05);
	}

	.previous {
		left: 1.25rem;
	}

	.next {
		right: 1.25rem;
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

		.lightbox {
			padding: 4.5rem 1rem 1.25rem;
		}

		.lightbox-content {
			width: 100%;
			height: 100%;
		}

		.lightbox-image {
			max-height: calc(100% - 95px);
		}

		.gallery-arrow {
			top: auto;
			bottom: 1.2rem;

			width: 46px;
			height: 46px;

			transform: none;
		}

		.gallery-arrow:hover {
			transform: scale(1.05);
		}

		.previous {
			left: 1rem;
		}

		.next {
			right: 1rem;
		}

		.lightbox-footer {
			padding-right: 4rem;
			padding-left: 4rem;
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
			border-radius: 16px;
		}

		.photo-overlay {
			padding: 2.25rem 1rem 0.85rem;
			font-size: 0.88rem;
		}

		.lightbox-footer {
			padding-right: 3.7rem;
			padding-left: 3.7rem;
		}

		.lightbox-footer h2 {
			font-size: 1.05rem;
		}

		.counter {
			font-size: 0.76rem;
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
		.photo-overlay,
		.close-button,
		.gallery-arrow {
			transition: none;
		}
	}
</style>