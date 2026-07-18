<script>
	import { slide } from 'svelte/transition';

	/*
		Replace these two values with your real contact information.
	*/
	const contactEmail = 'angela_wu@berkeley.edu';
	const linkedInUrl = 'https://www.linkedin.com/in/angelawu07';

	const contactMethods = [
		{
			label: 'Email',
			value: contactEmail,
			href: `mailto:${contactEmail}`,
			description: 'The best way to reach me directly.',
			external: false
		},
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
			label: 'Blog',
			value: 'Grippy Slide',
			href: 'https://grippyslide.bearblog.dev',
			description: 'Writing, reflections, and miscellaneous thoughts.',
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
			<article class="letter-card">
				<div class="letter-heading">
					<div class="envelope-icon" aria-hidden="true">✉</div>

					<div>
						<p class="card-label">A note from me</p>
						<h2>Thanks for stopping by!</h2>
					</div>
				</div>

				<div class="letter-copy">
					<p>
						I’m Angela, a Data Science student at UC Berkeley interested in
						machine learning, computer vision, visual design, and building
						thoughtful digital experiences.
					</p>

					<p>
						I’m always excited to meet people working on meaningful research,
						creative technology, education, and whimsy internet projects.
					</p>
				</div>

				<div class="interests">
					<p class="card-label">I’m especially happy to hear about</p>

					<ul>
						<li>Machine learning and data science opportunities</li>
						<li>Research and interdisciplinary collaborations</li>
						<li>Creative coding, design, and art projects</li>
						<li>Startups and tools that help people do meaningful work</li>
					</ul>
				</div>

				<a class="primary-button" href={`mailto:${contactEmail}`}>
					Send me an email
					<span aria-hidden="true">↗</span>
				</a>
			</article>

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

		<footer class="contact-footer">
			<p>
				Thanks for visiting my little corner of the internet. I’ll try to respond
				as soon as I can ☕️
			</p>
		</footer>
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
		width: min(1180px, 100%);
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
		max-width: 700px;
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
		max-width: 620px;
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

	.contact-layout {
		display: grid;
		grid-template-columns: minmax(0, 1.15fr) minmax(300px, 0.85fr);
		gap: clamp(1.4rem, 3vw, 2.25rem);
		align-items: stretch;
	}

	.letter-card {
		display: flex;
		flex-direction: column;
		align-items: flex-start;

		padding: clamp(1.5rem, 4vw, 2.6rem);

		background: #f7eee3;
		border: 2px solid rgba(91, 72, 61, 0.72);
		border-radius: 24px;

		color: #3f4253;

		box-shadow: 0 10px 28px rgba(29, 39, 42, 0.13);
	}

	.letter-heading {
		display: flex;
		align-items: center;
		gap: 1.1rem;

		margin-bottom: 1.2rem;
	}

	.envelope-icon {
		flex-shrink: 0;

		display: grid;
		place-items: center;

		width: 58px;
		height: 58px;

		background: rgba(216, 169, 182, 0.3);
		border: 2px solid rgba(125, 91, 99, 0.32);
		border-radius: 18px;

		font-size: 1.7rem;
		color: #68565c;
	}

	.card-label,
	.contact-label {
		margin: 0 0 0.3rem;

		font-family:
			'Segoe UI',
			Tahoma,
			Geneva,
			Verdana,
			sans-serif;

		font-size: 0.76rem;
		font-weight: 750;
		letter-spacing: 0.1em;
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

		color: #3f4253;
	}

	.letter-heading h2 {
		font-size: clamp(1.7rem, 3vw, 2.35rem);
		line-height: 1.1;
	}

	.letter-copy {
		font-family:
			'Segoe UI',
			Tahoma,
			Geneva,
			Verdana,
			sans-serif;

		font-size: 1.03rem;
		line-height: 1.65;

		color: #51505a;
	}

	.letter-copy p {
		margin: 0;
	}

	.letter-copy p + p {
		margin-top: 1rem;
	}

	.interests {
		width: 100%;
		margin: 1.6rem 0;
		padding-top: 1.4rem;

		border-top: 1px solid rgba(91, 72, 61, 0.25);
	}

	.interests ul {
		margin: 0.8rem 0 0;
		padding-left: 1.25rem;

		font-family:
			'Segoe UI',
			Tahoma,
			Geneva,
			Verdana,
			sans-serif;

		font-size: 0.98rem;
		line-height: 1.55;

		color: #51505a;
	}

	.interests li + li {
		margin-top: 0.45rem;
	}

	.interests li::marker {
		color: #9a6878;
	}

	.primary-button {
		display: inline-flex;
		align-items: center;
		gap: 0.45rem;

		margin-top: auto;
		padding: 0.72rem 1rem;

		background: #596b50;
		border: 2px solid #465540;
		border-radius: 999px;

		font-family:
			'Segoe UI',
			Tahoma,
			Geneva,
			Verdana,
			sans-serif;

		font-size: 0.92rem;
		font-weight: 750;

		color: white;
		text-decoration: none;

		transition:
			transform 0.18s ease,
			background 0.18s ease;
	}

	.primary-button:hover {
		background: #6b7d61;
		transform: translateY(-2px);
	}

	.contact-methods {
		display: grid;
		gap: 1rem;
	}

	.contact-card {
		display: flex;
		flex-direction: column;

		padding: 1.25rem 1.35rem;

		background: #f7eee3;
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

	.contact-card-top > span {
		color: #9a6878;
		font-size: 1.15rem;
	}

	.contact-card h2 {
		font-size: clamp(1.25rem, 2vw, 1.6rem);
		line-height: 1.15;
		overflow-wrap: anywhere;
	}

	.contact-card > p {
		margin: 0.55rem 0 0;

		font-family:
			'Segoe UI',
			Tahoma,
			Geneva,
			Verdana,
			sans-serif;

		font-size: 0.9rem;
		line-height: 1.45;

		color: #65636a;
	}

	.contact-card:focus-visible,
	.primary-button:focus-visible {
		outline: 4px solid white;
		outline-offset: 4px;
	}

	.contact-footer {
		margin-top: clamp(1.4rem, 3vw, 2.25rem);
		padding: 1.15rem 1.3rem;

		background: rgba(247, 238, 227, 0.82);
		border: 2px solid rgba(91, 72, 61, 0.45);
		border-radius: 18px;

		text-align: center;
	}

	.contact-footer p {
		margin: 0;

		font-family:
			'Segoe UI',
			Tahoma,
			Geneva,
			Verdana,
			sans-serif;

		font-size: 0.92rem;
		line-height: 1.5;

		color: #51505a;
	}

	@media (max-width: 850px) {
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

		.letter-card {
			padding: 1.25rem;
		}

		.letter-heading {
			align-items: flex-start;
		}

		.envelope-icon {
			width: 48px;
			height: 48px;
			border-radius: 15px;
			font-size: 1.4rem;
		}

		.contact-card {
			padding: 1.05rem;
		}
	}

	@media (prefers-reduced-motion: reduce) {
		.primary-button,
		.contact-card {
			transition: none;
		}
	}
</style>