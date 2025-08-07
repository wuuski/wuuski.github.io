<script lang="ts">
	import '../app.css';
	import './navbar.svelte'; 
	import Navbar from './Navbar.svelte';
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
	 
    h1 {
        color:rgb(54, 57, 78);
        font-family:'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
        font-size:50px;
    }
    p { 
        font-family:Cambria, Cochin, Georgia, Times, 'Times New Roman', serif
    }
    .stylized { 
        text-align: center;
        padding: 10px;
        background-color: rgb(173, 230, 210);
        margin: 5px;
        border-radius: 30px;
    }


    .flex-container {
        border-radius: 20px;
        display: flex;
        justify-content: space-around;
        align-items: column;
        
      }

      .flex-item {
        border-radius: 20px;
        padding: 10px;
        background-color: lightblue;
        margin: 5px;
      }
	</style>