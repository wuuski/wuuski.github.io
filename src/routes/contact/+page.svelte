<script>
	import { slide } from 'svelte/transition';

	const contactEmail = 'angela_wu@berkeley.edu';
	const linkedInUrl = 'https://www.linkedin.com/in/angelawu07';

	const contactMethods = [
		// {
		// 	label: 'Email',
		// 	value: contactEmail,
		// 	href: `mailto:${contactEmail}`,
		// 	description: 'The best way to reach me directly.',
		// 	external: false
		// },
		{
			label: 'LinkedIn',
			value: 'Connect with me',
			href: linkedInUrl,
			description: 'For professional updates and experience.',
			external: true
		},
		{
			label: 'GitHub',
			value: '@wuuski',
			href: 'https://github.com/wuuski',
			description: 'Projects, experiments, and things I’m building.',
			external: true
		},
		{
			label: 'Instagram',
			value: '@angelaisbig',
			href: 'https://www.instagram.com/angelaisbig/',
			description: 'always eating',
			external: true
		}
	];
</script>

<svelte:head>
	<title>Contact | Angela Wu</title>

	<meta
		name="description"
		content="Get in touch with Angela Wu about projects, research, creative work, and collaboration."
	/>
</svelte:head>

<main class="contact-page">
	<section
		class="contact-panel"
		in:slide={{
			duration: 850,
			delay: 120
		}}
	>
		<header class="page-header">
			<p class="eyebrow">Say hello</p>

			<h1>Contact</h1>

			<p class="intro">
				Have an interesting idea, opportunity, or project in mind? I’d love to
				hear about it.
			</p>
		</header>

		<div class="contact-layout">
			<div class="note-area">
				<div class="blob blob-main" aria-hidden="true"></div>
				<div class="blob blob-shadow" aria-hidden="true"></div>

				<a
					class="contact-note"
					href={`mailto:${contactEmail}`}
					aria-label={`Email Angela at ${contactEmail}`}
				>
					<img
						src="/paper-planes.png"
						alt="Hand-drawn note from Angela introducing herself and inviting visitors to email her"
					/>
					
				</a>
				<img
						class="letter-doodle"
						src="/letters.png"
						alt=""
						aria-hidden="true"
					/>

				<!-- <div class="doodle doodle-one" aria-hidden="true">♡</div>
				<div class="doodle doodle-two" aria-hidden="true">✦</div> -->
				<div class="doodle doodle-three" aria-hidden="true">⋆</div>
			</div>

			<div class="methods-area">
				<div class="blob blob-right" aria-hidden="true"></div>

				<div class="contact-methods">
					{#each contactMethods as method, index}
						<a
							class="contact-card"
							href={method.href}
							target={method.external ? '_blank' : undefined}
							rel={method.external ? 'noopener noreferrer' : undefined}
							in:slide={{
								duration: 550,
								delay: 240 + index * 90
							}}
						>
							<div class="contact-card-top">
								<p class="contact-label">{method.label}</p>
								<span aria-hidden="true">↗</span>
							</div>

							<h2>{method.value}</h2>
							<p>{method.description}</p>
						</a>
					{/each}
				</div>
			</div>
		</div>
	</section>
</main>

<style>
	:global(body) {
		margin: 0;
	}

	.contact-page {
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

	.contact-panel {
		position: relative;
		isolation: isolate;

		width: min(1240px, 100%);
		margin: 0 auto;
		box-sizing: border-box;

		padding: clamp(1.2rem, 2.8vw, 2.3rem);

		background: rgba(76, 96, 82, 0.5);

		backdrop-filter: blur(9px);
		-webkit-backdrop-filter: blur(9px);

		border: 2px solid rgba(69, 63, 49, 0.5);
		border-radius: 28px;

		box-shadow: 0 18px 45px rgba(35, 49, 42, 0.18);

		overflow: hidden;
	}

	.page-header {
		position: relative;
		z-index: 5;

		max-width: 700px;
		margin: 0 auto clamp(1.8rem, 4vw, 2.6rem);

		text-align: center;
		color: #fff8ea;
	}

	.eyebrow {
		margin: 0 0 0.35rem;
		font-family: SmileySans;
		/* font-family:
			'Segoe UI',
			Tahoma,
			Geneva,
			Verdana,
			sans-serif; */

		font-size: 0.82rem;
		font-weight: 750;
		letter-spacing: 0.15em;
		text-transform: uppercase;

		color: #dce9bd;
	}

	h1 {
		margin: 0;
		font-family: SmileySans;
		/* font-family:
			'Gill Sans',
			'Gill Sans MT',
			Calibri,
			'Trebuchet MS',
			sans-serif; */

		font-size: clamp(2.8rem, 5vw, 4.25rem);
		line-height: 1;

		color: #fff8ea;
	}

	.intro {
		max-width: 620px;
		margin: 0.75rem auto 0;
		font-family: SmileySans;

		/* font-family:
			'Segoe UI',
			Tahoma,
			Geneva,
			Verdana,
			sans-serif; */

		font-size: clamp(1rem, 1.5vw, 1.16rem);
		line-height: 1.55;

		color: rgba(255, 248, 234, 0.88);
	}

	.contact-layout {
		position: relative;
		z-index: 2;

		display: grid;
		grid-template-columns: minmax(0, 1.45fr) minmax(280px, 0.55fr);
		gap: clamp(1.4rem, 3vw, 2.25rem);
		align-items: center;
	}

	.note-area {
		position: relative;
		isolation: isolate;

		display: flex;
		align-items: center;
		justify-content: center;

		min-width: 0;
		min-height: 570px;
	}

	.contact-note {
		position: relative;
		z-index: 4;

		display: flex;
		align-items: center;
		justify-content: center;

		width: 100%;
		min-width: 0;
		padding: clamp(0.25rem, 1vw, 0.75rem);

		border-radius: 28px;

		text-decoration: none;

		transition:
			transform 0.2s ease,
			filter 0.2s ease;
	}

	.contact-note img {
		display: block;

		width: 100%;
		height: auto;
		max-height: 680px;

		object-fit: contain;

		filter: drop-shadow(0 14px 22px rgba(29, 39, 42, 0.2));
	}

	.contact-note:hover {
		transform: translateY(-4px) rotate(-0.3deg);
		filter: brightness(1.025);
	}

	.contact-note:focus-visible {
		outline: 4px solid white;
		outline-offset: 6px;
	}

	.letter-doodle {
		position: absolute;
		z-index: 7;

		width: clamp(145px, 18vw, 230px);
		height: auto;

		right: -3rem;
		bottom: -0.75rem;

		transform: rotate(25deg);
		transform-origin: center;

		filter: drop-shadow(0 10px 16px rgba(29, 39, 42, 0.15));

		pointer-events: none;
		user-select: none;

		transition: transform 0.25s ease;
	}
	@media (max-width: 1100px) {
	.letter-doodle {
		width: clamp(130px, 17vw, 190px);
		right: -0.5rem;
		bottom: 0;
	}
}

@media (max-width: 900px) {
	.letter-doodle {
		position: relative;

		width: min(190px, 42vw);

		right: auto;
		bottom: auto;

		margin: -3.5rem 1rem 0 auto;

		display: block;

		transform: rotate(6deg);
	}
}

@media (max-width: 500px) {
	.letter-doodle {
		width: min(150px, 40vw);
		margin-top: -2rem;
		margin-right: 0.5rem;
	}
}

	.blob {
		position: absolute;

		pointer-events: none;
		user-select: none;
	}

	.blob-main {
		z-index: 1;

		left: 1%;
		top: 3%;

		width: 82%;
		height: 83%;

		background: rgba(255, 241, 194, 0.76);

		border-radius:
			42% 58% 57% 43% /
			38% 39% 61% 62%;

		transform: rotate(7deg);

		box-shadow:
			inset 0 0 0 1px rgba(105, 94, 67, 0.08),
			0 16px 34px rgba(42, 54, 44, 0.08);
	}

	.blob-shadow {
		z-index: 0;

		right: 0;
		bottom: 2%;

		width: 62%;
		height: 48%;

		background: rgba(195, 194, 137, 0.48);

		border-radius:
			57% 43% 39% 61% /
			47% 58% 42% 53%;

		transform: rotate(-10deg);
	}

	.methods-area {
		position: relative;
		isolation: isolate;
	}

	.blob-right {
		z-index: 0;

		top: -12%;
		right: -28%;

		width: 115%;
		height: 48%;

		background: rgba(218, 163, 151, 0.56);

		border-radius:
			57% 43% 62% 38% /
			45% 58% 42% 55%;

		transform: rotate(28deg);
	}

	.doodle {
		position: absolute;
		z-index: 5;

		pointer-events: none;

		font-family:
			'Gill Sans',
			'Gill Sans MT',
			Calibri,
			'Trebuchet MS',
			sans-serif;

		color: rgba(119, 78, 86, 0.78);
	}

	/* .doodle-one {
		left: 44%;
		bottom: 5%;

		font-size: 2.2rem;
		transform: rotate(-14deg);
	} */

	/* .doodle-two {
		right: 7%;
		top: 19%;

		font-size: 2.1rem;
		transform: rotate(13deg);
	} */

	.doodle-three {
		left: 7%;
		bottom: 2%;

		font-size: 2.2rem;
		color: rgba(225, 188, 102, 0.9);
	}

	.contact-methods {
		position: relative;
		z-index: 2;

		display: grid;
		gap: 1rem;
	}

	.contact-card {
		display: flex;
		flex-direction: column;

		padding: 1.25rem 1.35rem;

		background: rgba(247, 238, 227, 0.97);
		border: 2px solid rgba(91, 72, 61, 0.72);
		border-radius: 20px;

		color: #3f4253;
		text-decoration: none;

		box-shadow: 0 8px 22px rgba(29, 39, 42, 0.11);

		transition:
			transform 0.2s ease,
			box-shadow 0.2s ease,
			background 0.2s ease;
	}

	.contact-card:hover {
		transform: translateY(-3px);
		background: #fff5eb;
		box-shadow: 0 13px 28px rgba(29, 39, 42, 0.17);
	}

	.contact-card-top {
		display: flex;
		align-items: center;
		justify-content: space-between;
		gap: 1rem;
	}

	.contact-label {
		margin: 0 0 0.3rem;
		font-family: SmileySans;

		font-size: 0.76rem;
		font-weight: 750;
		letter-spacing: 0.1em;
		text-transform: uppercase;

		color: #9a6878;
	}

	.contact-card-top > span {
		color: #9a6878;
		font-size: 1.15rem;
	}

	h2 {
		margin: 0;
		font-family: SmileySans;

		/* font-family:
			'Gill Sans',
			'Gill Sans MT',
			Calibri,
			'Trebuchet MS',
			sans-serif; */

		color: #3f4253;
	}

	.contact-card h2 {
		font-size: clamp(1.25rem, 2vw, 1.6rem);
		line-height: 1.15;
		overflow-wrap: anywhere;
	}

	.contact-card > p {
		margin: 0.55rem 0 0;
		font-family: SmileySans;
		
		font-size: 0.9rem;
		line-height: 1.45;

		color: #65636a;
	}

	.contact-card:focus-visible {
		outline: 4px solid white;
		outline-offset: 4px;
	}

	@media (max-width: 900px) {
		.contact-page {
			padding-top: 7rem;
			background-attachment: scroll;
		}

		.contact-panel {
			padding: 1rem;
			border-radius: 22px;
		}

		.contact-layout {
			grid-template-columns: 1fr;
		}

		.note-area {
			min-height: auto;
			padding: 2rem 0;
		}

		.contact-note {
			padding: 0;
		}

		.contact-note img {
			width: min(100%, 780px);
			max-height: none;
		}

		.blob-main {
			left: 4%;
			top: 6%;

			width: 90%;
			height: 84%;
		}

		.blob-shadow {
			right: 3%;
			bottom: 1%;

			width: 65%;
			height: 44%;
		}

		.blob-right {
			top: -7%;
			right: -12%;

			width: 80%;
			height: 35%;
		}

		.contact-methods {
			grid-template-columns: repeat(2, minmax(0, 1fr));
		}
	}

	@media (max-width: 600px) {
		.contact-methods {
			grid-template-columns: 1fr;
		}

		.blob-right {
			top: -3%;
			right: -25%;

			width: 105%;
			height: 27%;
		}
	}

	@media (max-width: 500px) {
		.contact-page {
			padding-right: 0.65rem;
			padding-left: 0.65rem;
			padding-bottom: 2rem;
		}

		.page-header {
			margin-bottom: 1.4rem;
		}

		.note-area {
			padding: 1rem 0 1.5rem;
		}

		.blob-main {
			left: 1%;
			top: 2%;

			width: 98%;
			height: 88%;
		}

		.blob-shadow {
			right: 0;
			bottom: 0;

			width: 70%;
			height: 38%;
		}

		.doodle-one {
			font-size: 1.5rem;
		}

		.doodle-two {
			font-size: 1.4rem;
		}

		.doodle-three {
			font-size: 1.5rem;
		}

		.contact-card {
			padding: 1.05rem;
		}
	}

	@media (prefers-reduced-motion: reduce) {
		.contact-note,
		.contact-card {
			transition: none;
		}
	}
</style>