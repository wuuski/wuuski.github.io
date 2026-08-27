<script>
	import { browser } from '$app/environment';
	import { onDestroy } from 'svelte';
	import { fade, scale, slide } from 'svelte/transition';

	const artworks = [
		{
			title: 'Grandpas Garden',
			image: '/grandpapatio.png',
			alt: 'A colorful painting of a sunlit garden and wooden patio'
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
			alt: 'Digital painting titled Scientists’ Refuge'
		},
		{
			title: 'Betty',
			image: '/Betty.png',
			alt: 'Painted portrait titled Betty'
		},
		{
			title: 'Angela (2021)',
			image: '/Angela.png',
			alt: 'Graphite portrait titled Angela'
		},
		{
			title: 'The Shell',
			image: '/The Shell.png',
			alt: 'Digital painting of a restaurant inside a giant shell'
		},
		{
			title: 'Memory Project',
			image: '/girlpainting.png',
			alt: 'Painted portrait of a girl'
		},
		{
			title: 'rolling ball',
			image: '/rollingball.png',
			alt: 'Berkeley campus study from a photo I took'
		}, 
		{
			title: 'Angela (2026)',
			image: '/realisticselfportrait.png',
			alt: 'recent self portrait'
		}
	];

	let selectedIndex = null;

	$: selectedArtwork =
		selectedIndex === null ? null : artworks[selectedIndex];

	/*
		Prevent the page behind the lightbox from scrolling.
	*/
	$: if (browser) {
		document.body.style.overflow =
			selectedIndex === null ? '' : 'hidden';
	}

	onDestroy(() => {
		if (browser) {
			document.body.style.overflow = '';
		}
	});

	function openArtwork(index) {
		selectedIndex = index;
	}

	function closeArtwork() {
		selectedIndex = null;
	}

	function showPrevious() {
		if (selectedIndex === null) return;

		selectedIndex =
			(selectedIndex - 1 + artworks.length) % artworks.length;
	}

	function showNext() {
		if (selectedIndex === null) return;

		selectedIndex = (selectedIndex + 1) % artworks.length;
	}

	function handleKeydown(event) {
		if (selectedIndex === null) return;

		if (event.key === 'Escape') {
			closeArtwork();
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
					<button
						class="art-image"
						type="button"
						on:click={() => openArtwork(index)}
						aria-label={`Open ${artwork.title} in gallery`}
					>
						<img
							src={artwork.image}
							alt={artwork.alt}
							loading={index > 1 ? 'lazy' : 'eager'}
						/>

						<span class="art-overlay">
							<span>{artwork.title}</span>
							<span aria-hidden="true">↗</span>
						</span>
					</button>
				</figure>
			{/each}
		</div>
	</section>
</main>

{#if selectedArtwork}
	<div
		class="lightbox"
		role="dialog"
		aria-modal="true"
		aria-label={`Viewing ${selectedArtwork.title}`}
		on:click={closeArtwork}
		in:fade={{ duration: 180 }}
		out:fade={{ duration: 150 }}
	>
		<button
			class="close-button"
			type="button"
			on:click|stopPropagation={closeArtwork}
			aria-label="Close gallery"
		>
			<span aria-hidden="true">×</span>
		</button>

		<button
			class="gallery-arrow previous"
			type="button"
			on:click|stopPropagation={showPrevious}
			aria-label="View previous artwork"
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
				src={selectedArtwork.image}
				alt={selectedArtwork.alt}
			/>

			<div class="lightbox-footer">
				<div>
					<p class="lightbox-label">Selected artwork</p>
					<h2>{selectedArtwork.title}</h2>
				</div>

				<p class="counter">
					{selectedIndex + 1} / {artworks.length}
				</p>
			</div>
		</div>

		<button
			class="gallery-arrow next"
			type="button"
			on:click|stopPropagation={showNext}
			aria-label="View next artwork"
		>
			<span aria-hidden="true">›</span>
		</button>
	</div>
{/if}

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

		font-family: SmileySans;

		font-size: 0.82rem;
		font-weight: 750;
		letter-spacing: 0.15em;
		text-transform: uppercase;

		color: #dce9bd;
	}

	h1 {
		margin: 0;

		font-family: SmileySans;

		font-size: clamp(2.8rem, 5vw, 4.25rem);
		line-height: 1;

		color: #fff8ea;
	}

	.intro {
		max-width: 680px;
		margin: 0.75rem auto 0;

		font-family: SmileySans;

		font-size: clamp(1rem, 1.5vw, 1.16rem);
		line-height: 1.55;

		color: rgba(255, 248, 234, 0.88);
	}

	/*
		Masonry gallery.
	*/
	.art-gallery {
		columns: 2;
		column-gap: clamp(1.4rem, 3vw, 2.25rem);
	}

	/*
		No green backing behind individual pieces.

		The thin cream frame separates each piece from the outer panel.
	*/
	.art-card {
		width: 100%;
		box-sizing: border-box;

		display: inline-block;
		vertical-align: top;

		margin: 0 0 clamp(1.4rem, 3vw, 2.25rem);

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

	.art-card:hover {
		transform: translateY(-4px);
		box-shadow: 0 15px 32px rgba(29, 39, 42, 0.22);
	}

	.art-image {
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

	.art-image img {
		width: 100%;
		height: auto;
		display: block;

		transition:
			transform 0.35s ease,
			filter 0.35s ease;
	}

	.art-overlay {
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

		font-family: SmileySans;

		font-size: 0.95rem;
		font-weight: 700;

		color: white;

		opacity: 0;
		transform: translateY(8px);

		transition:
			opacity 0.25s ease,
			transform 0.25s ease;
	}

	.art-overlay > span:last-child {
		flex-shrink: 0;
		font-size: 1.1rem;
	}

	.art-card:hover img {
		transform: scale(1.025);
		filter: brightness(0.91);
	}

	.art-card:hover .art-overlay,
	.art-image:focus-visible .art-overlay {
		opacity: 1;
		transform: translateY(0);
	}

	.art-image:focus-visible {
		outline: 4px solid white;
		outline-offset: 4px;
	}

	/*
		Fullscreen gallery.
	*/
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
		width: min(1100px, calc(100vw - 10rem));
		height: min(88vh, 900px);

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
		width: min(900px, 100%);

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

		font-family: SmileySans;

		font-size: 0.68rem;
		font-weight: 750;
		letter-spacing: 0.13em;
		text-transform: uppercase;

		color: rgba(255, 255, 255, 0.55);
	}

	.lightbox-footer h2 {
		margin: 0;

		font-family: SmileySans;

		font-size: clamp(1.15rem, 2vw, 1.65rem);
		font-weight: 500;

		color: rgba(255, 255, 255, 0.92);
	}

	.counter {
		flex-shrink: 0;
		margin: 0;

		font-family: SmileySans;

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

		font-family: SmileySans;
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
			border-radius: 16px;
		}

		.art-overlay {
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
		.art-overlay {
			opacity: 1;
			transform: translateY(0);
		}
	}

	@media (prefers-reduced-motion: reduce) {
		.art-card,
		.art-image img,
		.art-overlay,
		.close-button,
		.gallery-arrow {
			transition: none;
		}
	}
</style>