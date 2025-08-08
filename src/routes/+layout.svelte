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
        background-color:rgb(58,73,50);
        /*background-image: url('picnicblanket.png');*/
        background-repeat: no-repeat;
        
        background-position: center;  
        background-size: contain;
        padding:50px;
        image-rendering: crisp-edges;
        image-rendering: pixelated;
        background-attachment: fixed;
    }
	
	
	
	:global(.flex-item) {
        border-radius: 20px;
        padding: 10px;
        background-color: rgb(176,181,158);
        margin: 5px;
        border-color: rgb(76, 68, 54);
        border-width: 2px;
		align-items: row; 

      }
      
      :global(.flex-item:hover) { 
        transform: translateY(-5px);
        box-shadow: 0 4px 12px rgba(0, 0, 0, 0.2);
        transition: all 0.2s ease-in-out;
      }
	</style>