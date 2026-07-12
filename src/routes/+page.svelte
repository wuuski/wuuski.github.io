<section class="hero">
	<div class="scene">
		<img
			class="blanket"
			src="/blanket_scene.png"
			alt="Interactive picnic blanket portfolio"
		/>

		<a
			class="hotspot blog"
			href="https://grippyslide.bearblog.dev"
			target="_blank"
			rel="noopener noreferrer"
			aria-label="Open Angela's blog"
		></a>

		<a
			class="hotspot projects"
			href="/projects"
			aria-label="Open projects page"
		></a>

		<a
			class="hotspot portfolio"
			href="/portfolio"
			aria-label="Open portfolio page"
		></a>

    <a
    class="hotspot contact"
    href="/contact"
    aria-label="Open contact page"
    ></a>

    <a
    class="hotspot resume"
    href="/resume.pdf"
    aria-label="Open resume page"
    ></a>

    <a
    class="hotspot now"
    href="/now"
    aria-label="Open now page"
    ></a>

    <a
    class="hotspot now2"
    href="/now"
    aria-label="Open now page"
    ></a>

    <a
    class="hotspot reads"
    href="/now"
    aria-label="Open books page"
    ></a>

    <a
    class="hotspot photo"
    href="/photos"
    aria-label="Open photo page"
    ></a>

    <a
    class="hotspot guestbook"
    href="/now"
    aria-label="Open guestbook"
    ></a>
	</div>
</section>

<style>
	.hero {
		min-height: 100vh;

		background-image: url('/grass_bg.png');
		background-size: cover;
		background-position: center;

		display: flex;
		justify-content: center;
		align-items: center;

		padding-top: 80px;
		box-sizing: border-box;
		overflow: hidden;
	}

	.scene {
		position: relative;
		width: clamp(700px, 70vw, 1200px);
	}

	.blanket {
		width: 100%;
		height: auto;
		display: block;
	}

	.hotspot {
		position: absolute;
		display: block;
		z-index: 5;
		cursor: pointer;

    /* background: rgba(255, 0, 0, 0.4);
	  border: 2px solid red; */

		background: transparent;
		border: none;
		border-radius: 12px;
	}

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
		left: 46%;
		top: 25%;
		width: 9%;
		height: 12%;
	}

  .photo {
		left: 58%;
		top: 16%;
		width: 11%;
		height: 12%;
	}

  .guestbook {
		left: 74%;
		top: 16%;
		width: 11%;
		height: 12%;
	}


	.hotspot:hover,
	.hotspot:focus-visible {
		outline: 3px solid white;
		outline-offset: 4px;
	}
</style>