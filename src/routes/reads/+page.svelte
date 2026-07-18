<script>
	import { slide } from 'svelte/transition';

	const currentReads = [
		{
			title: 'Walden',
			author: 'Henry David Thoreau',
			genre: 'Nature · Philosophy',
			note:
				'A reflection on simplicity, nature, solitude, and what it means to live deliberately.',
			progress: 'Currently reading',
			coverClass: 'walden'
		},
		{
			title: 'Neuromancer',
			author: 'William Gibson',
			genre: 'Science fiction · Cyberpunk',
			note:
				'A strange, atmospheric cyberpunk classic about hackers, artificial intelligence, and the digital future.',
			progress: 'Currently reading',
			coverClass: 'neuromancer'
		}
	];

	const pastReads = [
		{
			title: 'Snow Crash',
			author: 'Neal Stephenson',
			genre: 'Science fiction · Cyberpunk',
			note:
				'Wild, funny, and incredibly imaginative. The metaverse before the term became unavoidable.',
			coverClass: 'snow-crash'
		},
		{
			title: 'The Art of Charlie Chan Hock Chye',
			author: 'Sonny Liew',
			genre: 'Graphic novel · Historical fiction',
			note:
				'A graphic biography that blends humor, politics, history, and visual experimentation beautifully.',
			coverClass: 'charlie'
		},
		{
			title: 'Norwegian Wood',
			author: 'Haruki Murakami',
			genre: 'Literary fiction',
			note:
				'A quiet, melancholic story about memory, loneliness, love, and growing into adulthood.',
			coverClass: 'norwegian'
		}
	];
</script>

<svelte:head>
	<title>Reads | Angela Wu</title>

	<meta
		name="description"
		content="Books Angela Wu is currently reading and a selection of past favorites."
	/>
</svelte:head>

<main class="reads-page">
	<section
		class="reads-panel"
		in:slide={{
			duration: 850,
			delay: 120
		}}
	>
		<header class="page-header">
			<p class="eyebrow">My bookshelf</p>

			<h1>Reads</h1>

			<p class="intro">
				“these have Made me” — emerson or something
			</p>
		</header>

		<div class="bookshelf">
			<section class="shelf-section current-section">
				<div class="shelf-label">
					<span aria-hidden="true">⌁</span>
					<h2>Currently reading</h2>
					<span aria-hidden="true">⌁</span>
				</div>

				<div class="books-row current-row">
					{#each currentReads as book, index}
						<article
							class="book-entry"
							in:slide={{
								duration: 580,
								delay: 240 + index * 120
							}}
						>
							<div class={`book-cover ${book.coverClass}`} aria-hidden="true">
								<div class="book-cover-inner">
									<p class="cover-title">{book.title}</p>
									<p class="cover-author">{book.author}</p>
								</div>
							</div>

							<div class="book-note">
								<div class="tape" aria-hidden="true"></div>

								<p class="book-status">{book.progress}</p>
								<h3>{book.title}</h3>
								<p class="author">{book.author}</p>
								<p class="genre">{book.genre}</p>
								<p class="description">{book.note}</p>

								<div class="note-doodle" aria-hidden="true">✦</div>
							</div>
						</article>
					{/each}
				</div>

				<div class="wood-shelf">
					<div class="wood-edge"></div>
				</div>
			</section>

			<section class="shelf-section past-section">
				<div class="shelf-label">
					<span aria-hidden="true">⌁</span>
					<h2>Past reads</h2>
					<span aria-hidden="true">⌁</span>
				</div>

				<div class="books-row past-row">
					{#each pastReads as book, index}
						<article
							class="book-entry past-entry"
							in:slide={{
								duration: 580,
								delay: 430 + index * 110
							}}
						>
							<div class={`book-cover ${book.coverClass}`} aria-hidden="true">
								<div class="book-cover-inner">
									<p class="cover-title">{book.title}</p>
									<p class="cover-author">{book.author}</p>
								</div>
							</div>

							<div class="book-note">
								<div class="tape" aria-hidden="true"></div>

								<p class="book-status">Finished</p>
								<h3>{book.title}</h3>
								<p class="author">{book.author}</p>
								<p class="genre">{book.genre}</p>
								<p class="description">{book.note}</p>

								<div class="note-doodle" aria-hidden="true">❀</div>
							</div>
						</article>
					{/each}
				</div>

				<div class="wood-shelf">
					<div class="wood-edge"></div>
				</div>
			</section>

			<div class="bottom-decor" aria-hidden="true">
				<div class="stacked-books">
					<div class="stack-book stack-green"></div>
					<div class="stack-book stack-brown"></div>
					<div class="stack-book stack-blue"></div>
				</div>

				<div class="plant">
					<div class="plant-leaf leaf-one"></div>
					<div class="plant-leaf leaf-two"></div>
					<div class="plant-leaf leaf-three"></div>
					<div class="plant-pot"></div>
				</div>

				<div class="tiny-paper">
					more books<br />
					to come ♡
				</div>
			</div>
		</div>
	</section>
</main>

<style>
	:global(body) {
		margin: 0;
	}

	:global(*) {
		box-sizing: border-box;
	}

	.reads-page {
		min-height: 100vh;

		padding:
			clamp(7.25rem, 10vw, 8.5rem)
			clamp(1rem, 2.5vw, 2rem)
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

	.reads-panel {
		width: min(1460px, 100%);
		margin: 0 auto;
		padding: clamp(1.2rem, 2.5vw, 2.4rem);

		background: rgba(76, 96, 82, 0.5);

		backdrop-filter: blur(9px);
		-webkit-backdrop-filter: blur(9px);

		border: 2px solid rgba(69, 63, 49, 0.5);
		border-radius: 28px;

		box-shadow: 0 18px 45px rgba(35, 49, 42, 0.18);
	}

	.page-header {
		max-width: 760px;
		margin: 0 auto clamp(2.4rem, 5vw, 3.5rem);

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

	.bookshelf {
		position: relative;

		padding:
			clamp(2rem, 4vw, 3.25rem)
			clamp(1rem, 2.5vw, 2.3rem)
			clamp(2rem, 4vw, 3.25rem);

		background:
			linear-gradient(
				rgba(60, 49, 35, 0.76),
				rgba(60, 49, 35, 0.76)
			),
			repeating-linear-gradient(
				90deg,
				#4d3d2d 0,
				#4d3d2d 26px,
				#594634 27px,
				#594634 54px
			);

		border: clamp(12px, 2vw, 22px) solid #6f5339;
		border-radius: 18px 18px 10px 10px;

		box-shadow:
			inset 0 0 0 3px rgba(255, 235, 195, 0.08),
			inset 0 18px 28px rgba(0, 0, 0, 0.25),
			0 18px 35px rgba(35, 42, 32, 0.2);
	}

	.shelf-section {
		position: relative;
		padding-top: 3.8rem;
	}

	.past-section {
		margin-top: clamp(4.5rem, 7vw, 6rem);
	}

	.shelf-label {
		position: absolute;
		top: 0;
		left: 50%;
		z-index: 10;

		display: flex;
		align-items: center;
		gap: 0.7rem;

		padding: 0.65rem 1.35rem;

		background: #748465;
		border: 2px solid rgba(55, 51, 39, 0.55);
		border-radius: 8px;

		box-shadow: 4px 6px 0 rgba(31, 29, 24, 0.24);

		color: #f9f0da;

		transform: translateX(-50%) rotate(-1deg);
	}

	.shelf-label::before,
	.shelf-label::after {
		content: '';

		position: absolute;
		top: -10px;

		width: 58px;
		height: 20px;

		background: rgba(229, 209, 162, 0.77);
		border: 1px solid rgba(103, 83, 54, 0.16);
	}

	.shelf-label::before {
		left: -28px;
		transform: rotate(-8deg);
	}

	.shelf-label::after {
		right: -28px;
		transform: rotate(7deg);
	}

	.shelf-label h2 {
		margin: 0;

		font-family:
			'Gill Sans',
			'Gill Sans MT',
			Calibri,
			'Trebuchet MS',
			sans-serif;

		font-size: clamp(1.25rem, 2.2vw, 1.75rem);
		font-weight: 600;
		white-space: nowrap;
	}

	.shelf-label span {
		font-size: 1.2rem;
	}

	.books-row {
		display: grid;
		align-items: end;
		gap: clamp(1.25rem, 2.5vw, 2rem);
	}

	.current-row {
		grid-template-columns: repeat(2, minmax(0, 1fr));
	}

	/*
		Each past-read entry gets enough horizontal space for
		both the book cover and its note.
	*/
	.past-row {
		grid-template-columns: repeat(3, minmax(330px, 1fr));
		gap: clamp(1.15rem, 2vw, 1.8rem);
	}

	.book-entry {
		display: grid;
		grid-template-columns: minmax(145px, 0.72fr) minmax(190px, 1fr);
		align-items: end;
		gap: clamp(0.85rem, 1.5vw, 1.2rem);

		min-width: 0;
	}

	.past-entry {
		grid-template-columns: minmax(125px, 0.72fr) minmax(175px, 1fr);
	}

	.book-cover {
		position: relative;

		width: 100%;
		aspect-ratio: 2 / 3;
		min-width: 0;
		min-height: 250px;

		display: flex;
		align-items: center;
		justify-content: center;

		padding: 1rem;

		border: 2px solid rgba(30, 27, 22, 0.75);
		border-radius: 3px 8px 8px 3px;

		box-shadow:
			-7px 7px 0 rgba(25, 22, 18, 0.28),
			0 15px 28px rgba(12, 12, 10, 0.25);

		overflow: hidden;

		transform: rotate(-1.2deg);

		transition:
			transform 0.22s ease,
			box-shadow 0.22s ease;
	}

	.book-entry:nth-child(even) .book-cover {
		transform: rotate(1.2deg);
	}

	.book-entry:hover .book-cover {
		transform: translateY(-7px) rotate(-0.5deg);

		box-shadow:
			-7px 11px 0 rgba(25, 22, 18, 0.26),
			0 20px 34px rgba(12, 12, 10, 0.3);
	}

	.book-cover::before {
		content: '';

		position: absolute;
		inset: 0 auto 0 0;

		width: 10px;

		background: rgba(20, 20, 17, 0.28);
		border-right: 1px solid rgba(255, 255, 255, 0.1);
	}

	.book-cover::after {
		content: '';

		position: absolute;
		inset: 0;

		background:
			linear-gradient(
				135deg,
				rgba(255, 255, 255, 0.13),
				transparent 35%
			),
			repeating-linear-gradient(
				0deg,
				transparent,
				transparent 12px,
				rgba(255, 255, 255, 0.025) 13px
			);

		pointer-events: none;
	}

	.book-cover-inner {
		position: relative;
		z-index: 2;

		width: 100%;
		min-width: 0;

		text-align: center;
	}

	.cover-title {
		max-width: 100%;
		margin: 0;

		font-family: Georgia, 'Times New Roman', serif;

		font-size: clamp(0.9rem, 1.35vw, 1.4rem);
		font-weight: 700;
		line-height: 1.08;

		text-transform: uppercase;
		letter-spacing: 0.025em;

		overflow-wrap: anywhere;
		word-break: normal;
		hyphens: auto;
	}

	.cover-author {
		max-width: 100%;
		margin: 1.1rem 0 0;

		font-family:
			'Segoe UI',
			Tahoma,
			Geneva,
			Verdana,
			sans-serif;

		font-size: clamp(0.58rem, 0.8vw, 0.75rem);
		font-weight: 650;
		line-height: 1.35;
		letter-spacing: 0.045em;
		text-transform: uppercase;

		overflow-wrap: anywhere;
	}

	/*
		Individual adjustments for titles that are wider or longer.
	*/
	.neuromancer .cover-title {
		font-size: clamp(0.72rem, 1.05vw, 1.05rem);
		letter-spacing: 0.005em;
	}

	.charlie .cover-title {
		font-size: clamp(0.68rem, 0.9vw, 0.95rem);
		line-height: 1.02;
		letter-spacing: 0.01em;
	}

	.norwegian .cover-title {
		font-size: clamp(0.70rem, 1.00vw, 1.00rem);
	}

	.walden {
		background:
			linear-gradient(
				rgba(242, 234, 203, 0.76),
				rgba(161, 180, 128, 0.35)
			),
			linear-gradient(155deg, #e2dcc0 0%, #879d72 100%);

		color: #3e513e;
	}

	.neuromancer {
		background:
			linear-gradient(150deg, rgba(12, 18, 27, 0.4), transparent),
			linear-gradient(145deg, #0f1720, #152f39 58%, #8c3b70);

		color: #dfeae7;
	}

	.snow-crash {
		background: linear-gradient(
			150deg,
			#151a27,
			#24364a 60%,
			#9f4661
		);

		color: #f2eee2;
	}

	.charlie {
		background: linear-gradient(145deg, #e2c798, #c77a54);
		color: #542f28;
	}

	.norwegian {
		background:
			linear-gradient(
				rgba(42, 55, 38, 0.35),
				rgba(29, 34, 27, 0.48)
			),
			linear-gradient(145deg, #7b876b, #29372e);

		color: #eee5ca;
	}

	.book-note {
		position: relative;

		width: 100%;
		min-width: 0;
		min-height: 245px;

		padding: 1.3rem 1.15rem 1.1rem;

		background: #f2e8cf;

		border: 1px solid rgba(105, 83, 58, 0.35);
		border-radius: 3px 9px 5px 8px;

		box-shadow: 5px 7px 0 rgba(25, 22, 18, 0.18);

		color: #4c453b;

		transform: rotate(1.2deg);
	}

	.book-entry:nth-child(even) .book-note {
		transform: rotate(-1.3deg);
	}

	.tape {
		position: absolute;
		top: -10px;
		left: 50%;

		width: 68px;
		height: 21px;

		background: rgba(224, 204, 158, 0.76);
		border: 1px solid rgba(112, 91, 60, 0.12);

		transform: translateX(-50%) rotate(-3deg);
	}

	.book-status,
	.genre {
		font-family:
			'Segoe UI',
			Tahoma,
			Geneva,
			Verdana,
			sans-serif;

		text-transform: uppercase;
		letter-spacing: 0.08em;
	}

	.book-status {
		margin: 0 0 0.35rem;

		font-size: 0.66rem;
		font-weight: 800;

		color: #9a6878;
	}

	.book-note h3 {
		max-width: 100%;
		margin: 0;

		font-family:
			'Gill Sans',
			'Gill Sans MT',
			Calibri,
			'Trebuchet MS',
			sans-serif;

		font-size: clamp(1rem, 1.35vw, 1.4rem);
		line-height: 1.08;

		color: #41434f;

		overflow-wrap: anywhere;
		word-break: normal;
		hyphens: auto;
	}

	.author {
		margin: 0.3rem 0 0;

		font-family:
			'Segoe UI',
			Tahoma,
			Geneva,
			Verdana,
			sans-serif;

		font-size: 0.8rem;
		font-weight: 650;

		color: #666052;
	}

	.genre {
		margin: 0.8rem 0 0;

		font-size: 0.61rem;
		font-weight: 750;
		line-height: 1.4;

		color: #6d8062;

		overflow-wrap: anywhere;
	}

	.description {
		margin: 0.55rem 0 0;

		font-family:
			'Segoe UI',
			Tahoma,
			Geneva,
			Verdana,
			sans-serif;

		font-size: clamp(0.78rem, 0.9vw, 0.88rem);
		line-height: 1.5;

		overflow-wrap: anywhere;
	}

	.note-doodle {
		position: absolute;
		right: 0.8rem;
		bottom: 0.55rem;

		font-size: 1.2rem;
		color: #8c735f;

		transform: rotate(8deg);
	}

	.wood-shelf {
		position: absolute;
		z-index: 8;

		right: -1.2rem;
		bottom: -2rem;
		left: -1.2rem;

		height: 33px;

		background:
			linear-gradient(
				rgba(255, 255, 255, 0.07),
				rgba(0, 0, 0, 0.14)
			),
			repeating-linear-gradient(
				90deg,
				#745437 0,
				#745437 42px,
				#694a31 43px,
				#694a31 85px
			);

		border: 2px solid #3f3023;
		border-radius: 4px;

		box-shadow:
			0 8px 0 #4b3626,
			0 14px 17px rgba(12, 10, 8, 0.38);
	}

	.wood-edge {
		position: absolute;
		inset: 5px 0 auto;

		height: 2px;
		background: rgba(255, 238, 200, 0.12);
	}

	.bottom-decor {
		display: flex;
		align-items: flex-end;
		justify-content: space-between;
		gap: 2rem;

		margin-top: clamp(5rem, 8vw, 7rem);
		padding: 0 clamp(0.5rem, 3vw, 2rem);
	}

	.stacked-books {
		width: 180px;
	}

	.stack-book {
		height: 27px;
		margin-top: 5px;

		border: 2px solid rgba(41, 34, 26, 0.6);
		border-radius: 4px;

		box-shadow: 4px 4px 0 rgba(27, 23, 18, 0.18);
	}

	.stack-green {
		width: 85%;
		margin-left: 12%;

		background: #5e7356;
		transform: rotate(2deg);
	}

	.stack-brown {
		width: 100%;

		background: #8a6845;
		transform: rotate(-1deg);
	}

	.stack-blue {
		width: 90%;
		margin-left: 5%;

		background: #445867;
		transform: rotate(1deg);
	}

	.plant {
		position: relative;

		width: 110px;
		height: 125px;
	}

	.plant-pot {
		position: absolute;
		right: 25px;
		bottom: 0;

		width: 62px;
		height: 48px;

		background: #9a7353;
		border: 2px solid #554333;
		border-radius: 5px 5px 20px 20px;
	}

	.plant-leaf {
		position: absolute;
		z-index: 2;

		width: 34px;
		height: 70px;

		background: #5d7a50;
		border: 2px solid #40563b;
		border-radius: 100% 0 100% 0;
	}

	.leaf-one {
		left: 24px;
		top: 10px;

		transform: rotate(-28deg);
	}

	.leaf-two {
		left: 48px;
		top: 2px;

		transform: rotate(9deg);
	}

	.leaf-three {
		right: 7px;
		top: 18px;

		transform: rotate(38deg);
	}

	.tiny-paper {
		padding: 0.85rem 1rem;

		background: #ead8aa;
		border: 1px solid rgba(92, 72, 47, 0.35);

		box-shadow: 4px 5px 0 rgba(28, 24, 19, 0.18);

		font-family:
			'Segoe UI',
			Tahoma,
			Geneva,
			Verdana,
			sans-serif;

		font-size: 0.8rem;
		font-weight: 650;
		line-height: 1.4;
		text-align: center;

		color: #65533e;

		transform: rotate(3deg);
	}

	/*
		Three past reads become two columns before the text gets cramped.
	*/
	@media (max-width: 1320px) {
		.past-row {
			grid-template-columns: repeat(2, minmax(330px, 1fr));
		}
	}

	@media (max-width: 1050px) {
		.current-row,
		.past-row {
			grid-template-columns: 1fr;
		}

		.book-entry,
		.past-entry {
			grid-template-columns: minmax(155px, 0.55fr) minmax(230px, 1fr);

			width: min(760px, 100%);
			margin-right: auto;
			margin-left: auto;
		}

		.book-entry + .book-entry {
			margin-top: 2rem;
		}
	}

	@media (max-width: 800px) {
		.reads-page {
			padding-top: 7rem;
			background-attachment: scroll;
		}

		.reads-panel {
			padding: 1rem;
			border-radius: 22px;
		}

		.bookshelf {
			border-width: 12px;
		}
	}

	@media (max-width: 620px) {
		.book-entry,
		.past-entry {
			grid-template-columns: 1fr;
			align-items: start;
		}

		.book-cover {
			width: min(250px, 78%);
			min-height: 0;
			margin: 0 auto;
		}

		.book-note {
			width: 100%;
			min-height: 0;
		}

		.wood-shelf {
			right: -0.5rem;
			left: -0.5rem;
		}

		.bottom-decor {
			flex-wrap: wrap;
			justify-content: center;
		}
	}

	@media (max-width: 500px) {
		.reads-page {
			padding-right: 0.65rem;
			padding-left: 0.65rem;
			padding-bottom: 2rem;
		}

		.page-header {
			margin-bottom: 2rem;
		}

		.bookshelf {
			padding-right: 0.75rem;
			padding-left: 0.75rem;
		}

		.shelf-label {
			padding: 0.55rem 0.85rem;
		}

		.shelf-label::before,
		.shelf-label::after {
			width: 35px;
		}

		.book-note {
			padding: 1.15rem 1rem;
		}
	}

	@media (prefers-reduced-motion: reduce) {
		.book-cover {
			transition: none;
		}

		.book-entry:hover .book-cover,
		.book-entry:nth-child(even) .book-cover {
			transform: none;
		}
	}
</style>