<script>
	let links = [
		
        { name: "Projects", href: "/projects" },
		{ name: "Art", href: "/portfolio" },
        { name: "Photo", href: "/photos" },
        { name: "Blog", href: "https://grippyslide.bearblog.dev", external: true },
        { name: "Resume", href: "/resume.pdf"},
        { name: "Contact", href: "/contact" },
		
		// { name: "Contact", href: "/contact" }
	];
</script>

<nav class="navbar">
   
    <a href="/">
	<div class="logo">
        <img src="/favicon.png" alt="pixel art moon">  Angela Wu
    </div>
    </a>
	<ul class="nav-links">
		{#each links as link}
			<li><a href={link.href}
            target={link.external ? "_blank" : undefined}
            rel={link.external ? "noopener noreferrer" : undefined}>{link.name}</a></li>
		{/each}
	</ul>
</nav>

<style>
    .navbar {
        position: fixed;
        top: 1.5rem;
        left: 50%;
        transform: translateX(-50%);
    
        width: min(94vw, 1500px);
        box-sizing: border-box;
    
        display: flex;
        justify-content: space-between;
        align-items: center;
    
        padding: 0.75rem 1.5rem;
    
        background: rgba(76, 85, 110, 0.28);
        backdrop-filter: blur(6px);
        -webkit-backdrop-filter: blur(6px);
    
        border: 2px solid rgba(59, 51, 38, 0.45);
        border-radius: 20px;
    
        z-index: 100;
    }
    
    .logo {
        display: flex;
        align-items: center;
        gap: 0.9rem;
    
        font-size: clamp(1.4rem, 2vw, 2.2rem);
        font-weight: bold;
    
        color: white;
        text-decoration: none;
    
        transition: color 0.2s ease;
    }
    
    .logo:hover {
        color: #f0a500;
    }
    
    .logo img {
        height: clamp(38px, 3.5vw, 56px);
        width: auto;
        display: block;
    }
    
    .nav-links {
        list-style: none;
        display: flex;
        align-items: center;
        gap: 1.5rem;
    
        margin: 0;
        padding: 0;
    }
    
    .nav-links a {
        color: white;
        text-decoration: none;
        font-size: clamp(1rem, 1.1vw, 1.25rem);
    
        transition: color 0.2s ease;
    }
    
    .nav-links a:hover {
        color: #f0a500;
    }
    
    /* ---------- Tablet ---------- */
    
    @media (max-width: 900px) {
    
        .navbar {
            padding: 0.65rem 1rem;
            width: 96vw;
        }
    
        .logo {
            font-size: 1.5rem;
        }
    
        .logo img {
            height: 42px;
        }
    
        .nav-links {
            gap: 1rem;
        }
    
        .nav-links a {
            font-size: 0.95rem;
        }
    }
    
    /* ---------- Phone ---------- */
    
    @media (max-width: 650px) {
    
        .navbar {
            padding: 0.6rem 0.9rem;
        }
    
        .logo {
            font-size: 1.2rem;
        }
    
        .logo img {
            height: 34px;
        }
    
        .nav-links {
            display: none;
        }
    }
    
    /* ---------- Extremely small viewport
       (very small window OR massive browser zoom)
    ----------------------------------------- */
    
    @media (max-width: 450px), (max-height: 450px) {
    
        .navbar {
            top: 0.4rem;
            width: 96vw;
            padding: 0.45rem 0.7rem;
            border-radius: 14px;
        }
    
        .logo {
            font-size: 0.95rem;
        }
    
        .logo img {
            height: 26px;
        }
    
        .nav-links {
            display: none;
        }
    }
    
    </style>