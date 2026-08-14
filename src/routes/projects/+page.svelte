<script>
	import { slide } from 'svelte/transition';

	const projects = [
		{
			title: 'Image Popularity Prediction',
			category: 'Machine learning · Computer vision',
			image: '/yolo2.png',
			alt: 'Image Popularity Prediction Streamlit interface',
			href: 'https://image-popularity-yolo.streamlit.app/',
			summary:
				'An end-to-end computer-vision pipeline that predicts image popularity using object detections, spatial features, and color statistics.',
			highlights: [
				'Processed roughly 20,000 images with YOLOv11',
				'Compared Random Forest and LightGBM models',
				'Deployed an interactive Streamlit application'
			],
			tags: ['Python', 'YOLOv11', 'LightGBM', 'OpenCV', 'Streamlit'],
			linkText: 'Try the app'
		},
		{
			title: 'S.S. Catnip',
			category: 'Creative coding · Game development',
			image: '/itchtitle.png',
			alt: 'Terry’s Fishing Adventure game banner',
			href: 'https://itch.io/jam/gmtk-2025/rate/3778108',
			summary:
				'A silly fishing game where Terry the cat captain and his crew use rope nets to catch fish, created for the 2025 GMTK Game Jam.',
			highlights: [
				'Designed and built under a game-jam deadline',
				'Combined programming, illustration, and interaction design',
				'Published as a playable game on itch.io'
			],
			tags: ['Game Jam', 'Godot', 'GDScript', 'Illustration'],
			linkText: 'Play the game'
		},
		{
			title: 'Dawn Runner Rocket Engine',
			category: 'Engineering · Technical documentation',
			image: '/StaticFirePicture.jpg',
			alt: 'Dawn Runner hybrid rocket engine during a static fire test',
			href:
				'https://drive.google.com/file/d/1QkYQZWJ6dqt-i1KgiO_hFSaXbRsxEP2X/view?usp=drive_link',
			summary:
				'Documentation of Dawn Runner, a hybrid rocket engine designed and constructed by our six-person student team.',
			highlights: [
				'Contributed to engine design, construction, and testing',
				'Documented performance calculations and subsystem decisions',
				'Completed a successful static-fire test'
			],
			tags: ['Rocketry', 'Engineering', 'Technical Writing', 'Team Project'],
			linkText: 'Read the report'
		}
	];
</script>

<svelte:head>
	<title>Projects | Angela Wu</title>
	<meta
		name="description"
		content="Selected projects by Angela Wu across machine learning, creative coding, and engineering."
	/>
</svelte:head>

<main class="projects-page">
	<section
		class="projects-panel"
		in:slide={{
			duration: 850,
			delay: 120
		}}
	>
		<header class="page-header">
			<p class="eyebrow">Selected work</p>
			<h1>Projects</h1>

			<p class="intro">
				A selection of things I’ve built across machine learning, creative coding,
				and engineering.
			</p>
		</header>

		<div class="project-list">
			{#each projects as project, index}
				<article
					class="project-card"
					in:slide={{
						duration: 600,
						delay: 220 + index * 110
					}}
				>
					<a
						class="project-image"
						href={project.href}
						target="_blank"
						rel="noopener noreferrer"
						aria-label={`Open ${project.title}`}
					>
						<img src={project.image} alt={project.alt} />
					</a>

					<div class="project-copy">
						<p class="project-category">{project.category}</p>

						<h2>{project.title}</h2>

						<p class="summary">
							{project.summary}
						</p>

						<ul class="highlights">
							{#each project.highlights as highlight}
								<li>{highlight}</li>
							{/each}
						</ul>

						<div class="tags" aria-label="Technologies and project categories">
							{#each project.tags as tag}
								<span>{tag}</span>
							{/each}
						</div>

						<a
							class="project-link"
							href={project.href}
							target="_blank"
							rel="noopener noreferrer"
						>
							{project.linkText}
							<span aria-hidden="true">↗</span>
						</a>
					</div>
				</article>
			{/each}
		</div>
	</section>
</main>

<style>
	:global(body) {
		margin: 0;
	}

	.projects-page {
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

	.projects-panel {
		width: min(1320px, 100%);
		margin: 0 auto;
		box-sizing: border-box;

		padding: clamp(1.2rem, 2.8vw, 2.3rem);

		background: rgba(76, 96, 82, 0.50);

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
	}

	.intro {
		max-width: 650px;
		margin: 0.75rem auto 0;

		font-family: SmileySans;

		font-size: clamp(1rem, 1.5vw, 1.16rem);
		line-height: 1.55;

		color: rgba(255, 248, 234, 0.88);
	}

	.project-list {
		display: grid;
		gap: clamp(1.4rem, 3vw, 2.25rem);
	}

	.project-card {
		display: grid;
		grid-template-columns: minmax(0, 0.92fr) minmax(0, 1.08fr);

		overflow: hidden;

		background: #f7eee3;

		border: 2px solid rgba(91, 72, 61, 0.72);
		border-radius: 24px;

		box-shadow: 0 10px 28px rgba(29, 39, 42, 0.13);

		transition:
			transform 0.2s ease,
			box-shadow 0.2s ease;
	}

	.project-card:hover {
		transform: translateY(-4px);
		box-shadow: 0 16px 34px rgba(29, 39, 42, 0.19);
	}

	.project-image {
		display: flex;
		align-items: center;
		justify-content: center;

		min-height: 310px;
		padding: clamp(0.9rem, 2vw, 1.2rem);

		background: #c4cdb2;

		border-right: 2px solid rgba(91, 72, 61, 0.52);
	}

	.project-image img {
		width: 100%;
		height: 100%;
		max-height: 430px;

		display: block;
		object-fit: contain;

		border-radius: 14px;
	}

	.project-image:focus-visible,
	.project-link:focus-visible {
		outline: 4px solid white;
		outline-offset: 4px;
	}

	.project-copy {
		display: flex;
		flex-direction: column;
		align-items: flex-start;

		padding: clamp(1.4rem, 3vw, 2.25rem);

		color: #3f4253;
	}

	.project-category {
		margin: 0 0 0.45rem;

		font-family: SmileySans;

		font-size: 0.78rem;
		font-weight: 750;
		letter-spacing: 0.09em;
		text-transform: uppercase;

		color: #9a6878;
	}

	h2 {
		margin: 0;

		font-family: SmileySans;

		font-size: clamp(1.75rem, 2.8vw, 2.4rem);
		line-height: 1.1;

		color: #3f4253;
	}

	.summary {
		margin: 0.9rem 0;

		font-family: SmileySans;

		font-size: 1.03rem;
		line-height: 1.6;

		color: #51505a;
	}

	.highlights {
		margin: 0 0 1.15rem;
		padding-left: 1.2rem;

		font-family: SmileySans;

		font-size: 1rem;
		line-height: 1.5;

		color: #51505a;
	}

	.highlights li + li {
		margin-top: 0.35rem;
	}

	.tags {
		display: flex;
		flex-wrap: wrap;
		gap: 0.5rem;

		margin-top: auto;
		margin-bottom: 1.25rem;
	}

	.tags span {
		padding: 0.4rem 0.7rem;

		background: rgba(216, 169, 182, 0.24);
		border: 1px solid rgba(125, 91, 99, 0.3);
		border-radius: 999px;

		font-family: SmileySans;

		font-size: 0.77rem;
		font-weight: 650;

		color: #68565c;
	}

	.project-link {
		display: inline-flex;
		align-items: center;
		gap: 0.45rem;

		padding: 0.68rem 1rem;

		background: #596b50;
		border: 2px solid #465540;
		border-radius: 999px;

		font-family: SmileySans;

		font-size: 0.9rem;
		font-weight: 750;

		color: white;
		text-decoration: none;

		transition:
			transform 0.18s ease,
			background 0.18s ease;
	}

	.project-link:hover {
		background: #6b7d61;
		transform: translateY(-2px);
	}

	@media (max-width: 800px) {
		.projects-page {
			padding-top: 7rem;
			background-attachment: scroll;
		}

		.projects-panel {
			padding: 1rem;
			border-radius: 22px;
		}

		.project-card {
			grid-template-columns: 1fr;
		}

		.project-image {
			min-height: auto;
			aspect-ratio: 4 / 3;

			border-right: none;
			border-bottom: 2px solid rgba(91, 72, 61, 0.52);
		}

		.project-copy {
			padding: 1.35rem;
		}
	}

	@media (max-width: 500px) {
		.projects-page {
			padding-right: 0.65rem;
			padding-left: 0.65rem;
			padding-bottom: 2rem;
		}

		.page-header {
			margin-bottom: 1.4rem;
		}

		.project-list {
			gap: 1.2rem;
		}

		.project-image {
			padding: 0.75rem;
		}

		.summary {
			font-size: 0.98rem;
		}

		.highlights {
			font-size: 0.92rem;
		}
	}
</style>