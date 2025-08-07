<script lang="ts">
	import '../app.css';
	import './navbar.svelte'; 
	import Navbar from './navbar.svelte';
	let { children } = $props();
</script>
<Navbar />
{@render children()}

<style>
    :global(body) {
        /* display: flex; */
        height: 100vh;
        background-color:rgb(111, 145, 135);
        /*background-image: url('picnicblanket.png');*/
        background-repeat: no-repeat;
        
        background-position: center;  
        background-size: contain;
        padding:50px;
        image-rendering: crisp-edges;
        image-rendering: pixelated;
        background-attachment: fixed;
    }
	
	</style>