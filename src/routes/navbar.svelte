<script>
	let links = [
		{ name: "Home", href: "/" },
		{ name: "Portfolio", href: "/portfolio" },
		{ name: "Projects", href: "/projects" },
		{ name: "Contact", href: "/contact" }
	];
</script>

<nav class="navbar">
    <a href="/">
	<div class="logo">Veridiplo.com</div>
    </a>
	<ul class="nav-links">
		{#each links as link}
			<li><a href={link.href}>{link.name}</a></li>
		{/each}
	</ul>
</nav>

<style>
	.navbar {
		display: flex;
		justify-content: space-between;
		align-items: center;
		padding: 1rem 2rem;
		background-color: #4c6e56;
		color: white;
        margin-bottom: 20px;
        border-radius:20px;
	}

	.logo {
		font-size: 1.5rem;
		font-weight: bold;
        transition: color 0.2s ease;
	}

  

	.nav-links {
		list-style: none;
		display: flex;
		gap: 1.5rem;
	}

	.nav-links a {
		color: white;
		text-decoration: none;
		transition: color 0.2s ease;
	}

	.nav-links a:hover {
		color: #f0a500;
	}
</style>
