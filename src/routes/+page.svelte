<section class="hero">
	<div class="scene">
		<img
			class="blanket"
			src="/blanket_scene.png"
			alt="Interactive picnic blanket portfolio"
		/>

		<!-- Decorative hover outlines -->
		<img
			class="item-outline now-outline"
			src="/now-outline.png"
			alt=""
			aria-hidden="true"
		/>

		<img
			class="item-outline blog-outline"
			src="/blog-outline.png"
			alt=""
			aria-hidden="true"
		/>

		<img
			class="item-outline work-outline"
			src="/work-outline.png"
			alt=""
			aria-hidden="true"
		/>

		<img
			class="item-outline art-outline"
			src="/art-outline.png"
			alt=""
			aria-hidden="true"
		/>

		<img
			class="item-outline contact-outline"
			src="/contact-outline.png"
			alt=""
			aria-hidden="true"
		/>

		<img
			class="item-outline resume-outline"
			src="/resume-outline.png"
			alt=""
			aria-hidden="true"
		/>

		<img
			class="item-outline reads-outline"
			src="/reads-outline.png"
			alt=""
			aria-hidden="true"
		/>

		<img
			class="item-outline photos-outline"
			src="/photos-outline.png"
			alt=""
			aria-hidden="true"
		/>

		<!-- Blog -->
		<a
			class="hotspot blog"
			href="https://grippyslide.bearblog.dev"
			target="_blank"
			rel="noopener noreferrer"
			aria-label="Open Angela's blog"
		></a>

		<!-- Projects -->
		<a
			class="hotspot projects"
			href="/projects"
			aria-label="Open projects page"
		></a>

		<!-- Art portfolio -->
		<a
			class="hotspot portfolio"
			href="/portfolio"
			aria-label="Open art portfolio"
		></a>

		<!-- Contact -->
		<a
			class="hotspot contact"
			href="/contact"
			aria-label="Open contact page"
		></a>

		<!-- Resume -->
		<a
			class="hotspot resume"
			href="/resume.pdf"
			aria-label="Open resume"
		></a>

		<!-- Upper half of character -->
		<a
			class="hotspot now"
			href="/now"
			aria-label="Open now page"
		></a>

		<!-- Lower half of character -->
		<a
			class="hotspot now2"
			href="/now"
			aria-label="Open now page"
		></a>

		<!-- Reads -->
		<a
			class="hotspot reads"
			href="/reads"
			aria-label="Open books and reading page"
		></a>

		<!-- Photos -->
		<a
			class="hotspot photo"
			href="/photos"
			aria-label="Open photo page"
		></a>
	</div>
	<div class="cal-webring">
		<a
			class="webring-arrow"
			href="https://calwebring.com/prev?current=https%3A%2F%2Fangelawu.dev"
			aria-label="Previous site in Cal Webring"
		>
			←
		</a>

		<a
			href="https://calwebring.com/"
			>
		<img
			src="https://calwebring.com/badge.png"
			alt=""
			aria-hidden="true"
		/></a>
		
	
		<!-- <span>Cal Webring</span> -->
	
		<!-- <a
			class="webring-random"
			href="https://cal-webring.vercel.app/random?current=https%3A%2F%2Fangelawu.dev"
			aria-label="Visit a random site in Cal Webring"
		>
			🎲
		</a> -->
	
		<a
			class="webring-arrow"
			href="https://calwebring.com/next?current=https%3A%2F%2Fangelawu.dev"
			aria-label="Next site in Cal Webring"
		>
			→
		</a>
	</div>
</section>

<style>
	
	.hero {
		min-height: 100vh;

		background-image: url('/grass_bg.png');
		background-size: cover;
		background-position: center;

		display: flex;
		flex-direction: column;   /* <-- add this */
		align-items: center;
		gap: 1.2rem;

		padding-top: 80px;
		box-sizing: border-box;
		overflow: hidden;
	}	

	.scene {
		position: relative;
		width: clamp(700px, 70vw, 1200px);
		/* margin-bottom: 1.5rem; */
	}

	@media (max-width: 800px) {
		.scene {
			width: 92vw;
		}
	}

	.blanket {
		position: relative;
		z-index: 1;

		display: block;
		width: 100%;
		height: auto;
	}

	/* ================================= */
	/* Shared outline styling            */
	/* ================================= */

	.item-outline {
		position: absolute;
		z-index: 4;

		height: auto;
		opacity: 0;

		pointer-events: none;
		user-select: none;

		transform: scale(0.99);
		transform-origin: center;

		transition:
			opacity 160ms ease,
			transform 160ms ease;
	}

	/* ================================= */
	/* Individual outline positioning    */
	/* ================================= */

	/*
		If an outline is slightly misaligned, adjust only its
		left, top, and width values in this section.
	*/

	.now-outline {
		left: 11.2%;
		top: 14%;
		width: 36%;
	}

	.blog-outline {
		left: 40.5%;
		top: 43%;
		width: 10.5%;
	}

	.work-outline {
		left: 55%;
		top: 39.5%;
		width: 16%;
	}

	.art-outline {
		left: 41%;
		top: 58%;
		width: 17%;
	}

	.contact-outline {
		left: 71%;
		top: 30.25%;
		width: 15.5%;
	}

	.resume-outline {
		left: 65%;
		top: 55.75%;
		width: 16.75%;
	}

	.reads-outline {
		left: 48%;
		top: 22.5%;
		width: 13%;
	}

	.photos-outline {
		left: 64%;
		top: 16%;
		width: 14%;
	}

	/* ================================= */
	/* Reveal outlines on hover/focus    */
	/* ================================= */

	/* Either character hotspot reveals the full character outline. */
	.scene:has(.now:hover) .now-outline,
	.scene:has(.now2:hover) .now-outline,
	.scene:has(.now:focus-visible) .now-outline,
	.scene:has(.now2:focus-visible) .now-outline,

	/* Blog */
	.scene:has(.blog:hover) .blog-outline,
	.scene:has(.blog:focus-visible) .blog-outline,

	/* Projects */
	.scene:has(.projects:hover) .work-outline,
	.scene:has(.projects:focus-visible) .work-outline,

	/* Art */
	.scene:has(.portfolio:hover) .art-outline,
	.scene:has(.portfolio:focus-visible) .art-outline,

	/* Contact */
	.scene:has(.contact:hover) .contact-outline,
	.scene:has(.contact:focus-visible) .contact-outline,

	/* Resume */
	.scene:has(.resume:hover) .resume-outline,
	.scene:has(.resume:focus-visible) .resume-outline,

	/* Reads */
	.scene:has(.reads:hover) .reads-outline,
	.scene:has(.reads:focus-visible) .reads-outline,

	/* Photos */
	.scene:has(.photo:hover) .photos-outline,
	.scene:has(.photo:focus-visible) .photos-outline {
		opacity: 1;
		transform: scale(1);
	}

	/* ================================= */
	/* Hotspot base styling              */
	/* ================================= */

	.hotspot {
		position: absolute;
		z-index: 5;

		display: block;

		background: transparent;
		border: none;
		border-radius: 12px;

		cursor: pointer;
		-webkit-tap-highlight-color: transparent;
	}

	/*
		Temporarily uncomment this while adjusting click areas:

	.hotspot {
		background: rgba(255, 0, 0, 0.35);
		border: 2px solid red;
	}
	*/

	/* ================================= */
	/* Character / Now hotspots          */
	/* ================================= */

	.now {
		left: 23%;
		top: 20%;
		width: 17%;
		height: 30%;
	}

	.now2 {
		left: 17%;
		top: 50%;
		width: 17%;
		height: 30%;
	}

	/* ================================= */
	/* Object hotspots                   */
	/* ================================= */

	.blog {
		left: 42%;
		top: 45%;
		width: 8%;
		height: 11%;
	}

	.projects {
		left: 56%;
		top: 40%;
		width: 13%;
		height: 16%;
	}

	.portfolio {
		left: 44%;
		top: 62%;
		width: 13%;
		height: 14%;
	}

	.contact {
		left: 72%;
		top: 34%;
		width: 13%;
		height: 12%;
	}

	.resume {
		left: 67%;
		top: 58%;
		width: 12%;
		height: 12%;
	}

	.reads {
		left: 49%;
		top: 25%;
		width: 10%;
		height: 12%;
	}

	.photo {
		left: 65%;
		top: 16%;
		width: 11.5%;
		height: 12%;
	}

	/* ================================= */
	/* Keyboard focus                    */
	/* ================================= */

	/*
		The imported PNG outlines act as the visible keyboard-focus
		indicators, so the browser's rectangular outlines are removed.
	*/

	.now:focus-visible,
	.now2:focus-visible,
	.blog:focus-visible,
	.projects:focus-visible,
	.portfolio:focus-visible,
	.contact:focus-visible,
	.resume:focus-visible,
	.reads:focus-visible,
	.photo:focus-visible {
		outline: none;
	}

	/* Respect reduced-motion preferences. */
	@media (prefers-reduced-motion: reduce) {
		.item-outline {
			transition: none;
			transform: none;
		}

		.scene:has(.now:hover) .now-outline,
		.scene:has(.now2:hover) .now-outline,
		.scene:has(.now:focus-visible) .now-outline,
		.scene:has(.now2:focus-visible) .now-outline,
		.scene:has(.blog:hover) .blog-outline,
		.scene:has(.blog:focus-visible) .blog-outline,
		.scene:has(.projects:hover) .work-outline,
		.scene:has(.projects:focus-visible) .work-outline,
		.scene:has(.portfolio:hover) .art-outline,
		.scene:has(.portfolio:focus-visible) .art-outline,
		.scene:has(.contact:hover) .contact-outline,
		.scene:has(.contact:focus-visible) .contact-outline,
		.scene:has(.resume:hover) .resume-outline,
		.scene:has(.resume:focus-visible) .resume-outline,
		.scene:has(.reads:hover) .reads-outline,
		.scene:has(.reads:focus-visible) .reads-outline,
		.scene:has(.photo:hover) .photos-outline,
		.scene:has(.photo:focus-visible) .photos-outline {
			transform: none;
		}
	}
	.cal-webring {
		display: inline-flex;
		align-items: center;
		justify-content: center;
		gap: 0.8rem;
		z-index: 20;

		width: max-content;
		max-width: calc(100vw - 2rem);

		margin: -2rem auto 2rem;
		transform: translateY(-7rem);

		padding: 0.65rem 1rem;

		/* background: rgba(255, 248, 234, 0.82); */

		backdrop-filter: blur(2px);
		-webkit-backdrop-filter: blur(2px);

		/* border: 2px solid rgba(91, 72, 61, 0.45); */
		border-radius: 999px;

		box-shadow: 0 5px 14px rgba(39, 50, 38, 0.14);

		font-family: monospace;
		font-size: 0.8rem;
		color: #4f5347;
		

		white-space: nowrap;
}

	@media (max-width: 1100px) {
		.cal-webring {
			margin: -0.5rem auto 0;
			transform: translateY(-1rem);
		}
	}

	.cal-webring img {
		width: 36px;
		height: 36px;
		display: block;
		object-fit: contain;
	}

	.cal-webring a {
		display: inline-flex;
		align-items: center;
		justify-content: center;

		color: inherit;
		text-decoration: none;

		transition:
			transform 0.15s ease,
			opacity 0.15s ease;
	}

	.cal-webring a:hover {
		transform: translateY(-1px);
		opacity: 0.7;
	}

	
</style>