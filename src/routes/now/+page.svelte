<script lang="ts">
	import { slide } from 'svelte/transition';

	const currently = [
		'Cofounder at Nook',
		'Studying Data Science at UC Berkeley',
		'Building stronger foundations in algorithms, math, and machine learning'
	];

	const work = [
		'Modeling avian botulism risk with the National Park Service',
		'Integrating ecological, weather, satellite, and bird-observation data',
		'Exploring thoughtful productivity tools through Nook'
	];

	const hobbies = [
		'Drawing and painting',
		'Photography',
		'Reading and blogging',
		'Rock climbing',
		'Running'
	];

	const recently = [
		'Learning SvelteKit by rebuilding this website',
		'Climbing mostly at Mosaic Boulders',
		'Trying to make more things instead of endlessly planning them'
	];
</script>

<svelte:head>
	<title>Now | Angela Wu</title>
	<meta
		name="description"
		content="What Angela Wu is currently building, studying, reading, and enjoying."
	/>
</svelte:head>

<main class="now-page">
	<section
		class="scrapbook"
		in:slide={{
			duration: 850,
			delay: 120
		}}
	>
		<header class="page-header">
            <div class="header-paper">
                <p class="eyebrow">Updated July 2026</p>
        
                <h1>/now</h1>
        
                <p class="intro">
                    A little snapshot of what I’m working on, thinking about, and enjoying
                    right now.
                </p>
            </div>
        </header>

		<div class="scrapbook-layout">
			<div class="illustration-area">
				<div class="paint-swatch swatch-blue" aria-hidden="true"></div>
				<div class="paint-swatch swatch-cream" aria-hidden="true"></div>

				<img
					class="now-illustration"
					src="/now_scene.png"
					alt="Illustration of Angela working at a desk with a drawing tablet, laptop, and plush dinosaur"
				/>

				<div class="tiny-note note-making">
					<span>currently making</span>
					<strong>this website!</strong>
				</div>
			</div>

			<article class="paper paper-currently">
				<div class="tape tape-top" aria-hidden="true"></div>

				<p class="paper-label">Right now</p>
				<h2>Currently</h2>

				<ul>
					{#each currently as item}
						<li>{item}</li>
					{/each}
				</ul>
			</article>

			<article class="paper paper-movement">
				<div class="pin" aria-hidden="true"></div>

				<div class="movement-heading">
					<div>
						<p class="paper-label">Movement</p>
						<h2>Climbing & running</h2>
					</div>

					<div class="shoe-doodle" aria-hidden="true">
						<span>🥾</span>
					</div>
				</div>

				<p>
					I’m into rock climbing—mostly bouldering—and I’m slowly getting back
					into running.
				</p>

				<p class="scribble">Mythos Ecos ♡</p>
			</article>

			<article class="paper paper-hobbies">
				<div class="tape tape-corner" aria-hidden="true"></div>

				<p class="paper-label">Outside work</p>
				<h2>Things I keep returning to</h2>

				<ul class="checklist">
					{#each hobbies as hobby}
						<li>{hobby}</li>
					{/each}
				</ul>
			</article>

			<article class="paper paper-work">
				<div class="paperclip" aria-hidden="true"></div>

				<p class="paper-label">Research & building</p>
				<h2>What I’m working on</h2>

				<ul>
					{#each work as item}
						<li>{item}</li>
					{/each}
				</ul>
			</article>

			<article class="paper paper-recently">
				<div class="tape tape-bottom" aria-hidden="true"></div>

				<p class="paper-label">Recently</p>
				<h2>Small updates</h2>

				<ul>
					{#each recently as item}
						<li>{item}</li>
					{/each}
				</ul>
			</article>

			<div class="doodle doodle-arrow" aria-hidden="true">↝</div>
			<div class="doodle doodle-star" aria-hidden="true">✦</div>
			<div class="doodle doodle-flower" aria-hidden="true">❀</div>
		</div>

		<footer class="now-footer">
			<p>
				Inspired by the <a
					href="https://nownownow.com/about"
					target="_blank"
					rel="noopener noreferrer">/now page movement</a
				>.
			</p>
		</footer>
	</section>
</main>

<style>
	:global(body) {
		margin: 0;
	}

	.now-page {
		min-height: 100vh;
		box-sizing: border-box;

		padding:
			clamp(7.25rem, 10vw, 8.5rem)
			clamp(1rem, 3vw, 2.5rem)
			4rem;

		background-image:
			linear-gradient(
				rgba(164, 202, 116, 0.05),
				rgba(164, 202, 116, 0.05)
			),
			url('/grass_bg.png');

		background-size: cover;
		background-position: center;
		background-attachment: fixed;
	}

	.scrapbook {
		width: min(1280px, 100%);
		margin: 0 auto;
		box-sizing: border-box;

		padding: clamp(1.4rem, 3vw, 2.6rem);

		background:
			linear-gradient(rgba(168, 211, 154, 0.88), rgba(168, 211, 154, 0.88)),
			repeating-linear-gradient(
				0deg,
				transparent,
				transparent 29px,
				rgba(90, 108, 77, 0.08) 30px
			);

		border: 2px solid rgba(69, 63, 49, 0.5);
		border-radius: 28px;

		box-shadow: 0 18px 45px rgba(35, 49, 42, 0.18);

		overflow: hidden;
	}

	.page-header {
        max-width: 760px;
        margin: 0 auto clamp(2rem, 5vw, 3rem);
        padding: 0 1rem;

        text-align: center;
    }

    .header-paper {
        position: relative;

        padding: clamp(1.4rem, 3vw, 2rem)
            clamp(1.25rem, 4vw, 3rem);

        background: rgba(247, 238, 227, 0.88);

        border: 2px solid rgba(91, 72, 61, 0.45);
        border-radius: 18px 10px 20px 12px;

        box-shadow:
            7px 9px 0 rgba(73, 84, 66, 0.11),
            0 14px 28px rgba(48, 58, 44, 0.08);

        transform: rotate(-0.7deg);
    }
    .header-paper::before {
        content: '';

        position: absolute;
        top: -12px;
        left: 50%;

        width: 105px;
        height: 25px;

        background: rgba(238, 218, 174, 0.75);
        border: 1px solid rgba(117, 99, 67, 0.14);

        transform: translateX(-50%) rotate(2deg);
    }


	.eyebrow {
        margin: 0 0 0.35rem;

        font-family:
            'Segoe UI',
            Tahoma,
            Geneva,
            Verdana,
            sans-serif;

        font-size: 0.78rem;
        font-weight: 750;
        letter-spacing: 0.13em;
        text-transform: uppercase;

        color: #9a6878;
    }

	.paper-label {
		margin: 0 0 0.35rem;

		font-family:
			'Segoe UI',
			Tahoma,
			Geneva,
			Verdana,
			sans-serif;

		font-size: 0.78rem;
		font-weight: 750;
		letter-spacing: 0.13em;
		text-transform: uppercase;
	}

	.eyebrow {
		color: #627558;
	}

	.page-header {
	max-width: 760px;
	margin: 0 auto clamp(2rem, 5vw, 3rem);
	padding: 0 1rem;

	text-align: center;
}

.header-paper {
	position: relative;

	padding: clamp(1.4rem, 3vw, 2rem)
		clamp(1.25rem, 4vw, 3rem);

	background: rgba(247, 238, 227, 0.88);

	border: 2px solid rgba(91, 72, 61, 0.45);
	border-radius: 18px 10px 20px 12px;

	box-shadow:
		7px 9px 0 rgba(73, 84, 66, 0.11),
		0 14px 28px rgba(48, 58, 44, 0.08);

	transform: rotate(-0.7deg);
}

.header-paper::before {
	content: '';

	position: absolute;
	top: -12px;
	left: 50%;

	width: 105px;
	height: 25px;

	background: rgba(238, 218, 174, 0.75);
	border: 1px solid rgba(117, 99, 67, 0.14);

	transform: translateX(-50%) rotate(2deg);
}

.eyebrow {
	margin: 0 0 0.35rem;

	font-family:
		'Segoe UI',
		Tahoma,
		Geneva,
		Verdana,
		sans-serif;

	font-size: 0.78rem;
	font-weight: 750;
	letter-spacing: 0.13em;
	text-transform: uppercase;

	color: #9a6878;
}

    h1 {
        margin: 0;

        font-family:
            'Gill Sans',
            'Gill Sans MT',
            Calibri,
            'Trebuchet MS',
            sans-serif;

        font-size: clamp(3rem, 6vw, 5rem);
        line-height: 1;

        color: #4a4b59;

        transform: none;
    }

    .intro {
        max-width: 610px;
        margin: 0.8rem auto 0;

        font-family:
            'Segoe UI',
            Tahoma,
            Geneva,
            Verdana,
            sans-serif;

        font-size: clamp(1rem, 1.5vw, 1.15rem);
        line-height: 1.55;

        color: #5b5b62;
    }

	.scrapbook-layout {
		position: relative;

		display: grid;
		grid-template-columns: repeat(12, minmax(0, 1fr));
		grid-auto-rows: minmax(70px, auto);
		gap: clamp(1rem, 2.2vw, 1.8rem);

		padding: clamp(0.5rem, 2vw, 1.5rem);
	}

	.illustration-area {
		position: relative;
		grid-column: 1 / 7;
		grid-row: 2 / 8;

		min-height: 530px;

		display: flex;
		align-items: flex-end;
		justify-content: center;

		z-index: 3;
	}

	.now-illustration {
		position: relative;
		z-index: 3;

		width: min(590px, 115%);
		height: auto;
		display: block;

		filter: drop-shadow(0 18px 16px rgba(57, 65, 50, 0.16));

		transform: rotate(-2.5deg) translate(-2%, 2%);
	}

	.paint-swatch {
		position: absolute;

		border-radius: 48% 52% 45% 55% / 58% 44% 56% 42%;

		opacity: 0.85;
	}

	.swatch-blue {
		width: 68%;
		height: 62%;

		left: -2%;
		bottom: 7%;

		background: #c5e5eb;
		transform: rotate(-7deg);
	}

	.swatch-cream {
		width: 70%;
		height: 56%;

		left: 16%;
		bottom: 3%;

		background: #f7eee3;
		transform: rotate(5deg);
	}

	.tiny-note {
		position: absolute;
		z-index: 6;

		display: flex;
		flex-direction: column;

		padding: 0.75rem 0.9rem;

		background: #f3d7a5;
		border: 1px solid rgba(104, 83, 57, 0.35);
		box-shadow: 3px 5px 0 rgba(85, 76, 59, 0.15);

		font-family:
			'Segoe UI',
			Tahoma,
			Geneva,
			Verdana,
			sans-serif;

		color: #645340;
	}

	.note-making {
		right: 3%;
		bottom: 5%;

		transform: rotate(4deg);
	}

	.tiny-note span {
		font-size: 0.68rem;
		text-transform: uppercase;
		letter-spacing: 0.08em;
	}

	.tiny-note strong {
		margin-top: 0.15rem;
		font-size: 0.92rem;
	}

	.paper {
		position: relative;
		z-index: 4;

		box-sizing: border-box;
		padding: clamp(1.25rem, 2.5vw, 1.8rem);

		background: #f7eee3;
		border: 2px solid rgba(91, 72, 61, 0.48);
		border-radius: 7px 18px 10px 15px;

		box-shadow:
			6px 8px 0 rgba(73, 84, 66, 0.13),
			0 15px 28px rgba(48, 58, 44, 0.08);

		color: #454655;
	}

	.paper::after {
		content: '';
		position: absolute;
		inset: 7px;

		border: 1px dashed rgba(147, 102, 118, 0.16);
		border-radius: inherit;

		pointer-events: none;
	}

	.paper h2 {
		position: relative;
		z-index: 2;

		margin: 0;

		font-family:
			'Gill Sans',
			'Gill Sans MT',
			Calibri,
			'Trebuchet MS',
			sans-serif;

		font-size: clamp(1.45rem, 2.4vw, 2rem);
		line-height: 1.12;
	}

	.paper p,
	.paper li {
		position: relative;
		z-index: 2;

		font-family:
			'Segoe UI',
			Tahoma,
			Geneva,
			Verdana,
			sans-serif;

		font-size: 0.98rem;
		line-height: 1.55;
	}

	.paper ul {
		margin: 1rem 0 0;
		padding-left: 1.2rem;
	}

	.paper li + li {
		margin-top: 0.45rem;
	}

	.paper li::marker {
		color: #9a6878;
	}

	.paper-label {
		position: relative;
		z-index: 2;

		color: #9a6878;
	}

	.paper-currently {
		grid-column: 7 / 13;
		grid-row: 1 / 4;

		transform: rotate(1.3deg);
	}

	.paper-movement {
		grid-column: 8 / 13;
		grid-row: 4 / 7;

		transform: rotate(-1.5deg);
	}

	.paper-hobbies {
		grid-column: 7 / 12;
		grid-row: 7 / 10;

		transform: rotate(1deg);
	}

	.paper-recently {
        grid-column: 1 / 6;
        grid-row: 9 / 11;

        transform: rotate(1.2deg);
    }

    .paper-work {
        grid-column: 6 / 13;
        grid-row: 10 / 13;

        transform: rotate(-0.8deg);
    }

	.movement-heading {
		display: flex;
		align-items: center;
		justify-content: space-between;
		gap: 1rem;
	}
    .paper-recently,
    .paper-work {
        padding: clamp(1.2rem, 2.2vw, 1.6rem);
    }

	.shoe-doodle {
		flex-shrink: 0;

		display: grid;
		place-items: center;

		width: 68px;
		height: 68px;

		background: #d8e7c3;
		border: 2px solid rgba(89, 107, 80, 0.35);
		border-radius: 50%;

		transform: rotate(8deg);
	}

	.shoe-doodle span {
		font-size: 2rem;
	}

	.scribble {
		margin: 0.8rem 0 0;

		font-style: italic;
		color: #9a6878;

		transform: rotate(-2deg);
	}

	.checklist {
		list-style: none;
		padding-left: 0 !important;
	}

	.checklist li::before {
		content: '☐';
		margin-right: 0.55rem;
		color: #6a805f;
	}

	.tape {
		position: absolute;
		z-index: 8;

		width: 92px;
		height: 25px;

		background: rgba(238, 218, 174, 0.72);
		border: 1px solid rgba(117, 99, 67, 0.15);

		box-shadow: 0 2px 5px rgba(66, 55, 41, 0.08);
	}

	.tape-top {
		top: -12px;
		left: 45%;

		transform: rotate(-3deg);
	}

	.tape-corner {
		top: -8px;
		right: 22px;

		transform: rotate(7deg);
	}

	.tape-bottom {
		right: 30px;
		bottom: -10px;

		transform: rotate(-5deg);
	}

	.pin {
		position: absolute;
		z-index: 8;

		top: 12px;
		right: 18px;

		width: 14px;
		height: 14px;

		background: #b85e67;
		border: 2px solid #8e464f;
		border-radius: 50%;

		box-shadow: 0 4px 4px rgba(71, 48, 52, 0.2);
	}

	.paperclip {
		position: absolute;
		z-index: 8;

		top: -20px;
		left: 22px;

		width: 19px;
		height: 54px;

		border: 4px solid #8a8a82;
		border-bottom-color: transparent;
		border-radius: 14px;

		transform: rotate(8deg);
	}

	.doodle {
		position: absolute;
		z-index: 2;

		font-family:
			'Gill Sans',
			'Gill Sans MT',
			Calibri,
			'Trebuchet MS',
			sans-serif;

		color: rgba(84, 103, 77, 0.65);

		pointer-events: none;
	}

	.doodle-arrow {
		top: 9%;
		left: 43%;

		font-size: 4rem;
		transform: rotate(18deg);
	}

	.doodle-star {
		top: 1%;
		bottom: 20%;

		font-size: 3rem;
		transform: rotate(12deg);
	}

	.doodle-flower {
		left: 4%;
		bottom: 8%;

		font-size: 3.2rem;
		transform: rotate(-8deg);
	}

	.now-footer {
		margin: 2rem auto 0;
		text-align: center;
	}

	.now-footer p {
		margin: 0;

		font-family:
			'Segoe UI',
			Tahoma,
			Geneva,
			Verdana,
			sans-serif;

		font-size: 0.85rem;
		color: #53604f;
	}

	.now-footer a {
		color: #715d65;
		font-weight: 700;
	}

	@media (max-width: 900px) {
		.now-page {
			padding-top: 7rem;
			background-attachment: scroll;
		}

		.scrapbook-layout {
			grid-template-columns: 1fr;
			display: flex;
			flex-direction: column;
            padding-bottom: 2rem;
		}

		.illustration-area,
		.paper-currently,
		.paper-movement,
		.paper-hobbies,
		.paper-work,
		.paper-recently {
			grid-column: auto;
			grid-row: auto;
			width: 100%;
		}

		.illustration-area {
			order: 2;
			min-height: 430px;
		}

		.paper-currently {
			order: 1;
		}

		.paper-movement {
			order: 3;
		}

		.paper-hobbies {
			order: 4;
		}

		.paper-work {
			order: 5;
		}

		.paper-recently {
			order: 6;
		}

		.paper {
			transform: none;
		}

		.doodle {
			display: none;
		}
	}

	@media (max-width: 520px) {
		.now-page {
			padding-right: 0.65rem;
			padding-left: 0.65rem;
			padding-bottom: 2rem;
		}

		.scrapbook {
			padding: 0.85rem;
			border-radius: 22px;
		}

		.illustration-area {
			min-height: 340px;
		}

		.now-illustration {
			width: 115%;
		}

		.note-making {
			right: 0;
			bottom: 0;
		}

		.paper {
			padding: 1.15rem;
		}

		.movement-heading {
			align-items: flex-start;
		}

		.shoe-doodle {
			width: 54px;
			height: 54px;
		}
	}

	@media (prefers-reduced-motion: reduce) {
		.now-illustration,
		.paper,
		.tiny-note {
			transform: none;
		}
	}
</style>