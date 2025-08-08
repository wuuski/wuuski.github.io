<script>
	import {
	blur,
	crossfade,
	draw,
	fade,
	fly,
	scale,
	slide
} from 'svelte/transition';
</script>
<div class="gradientbg"  in:slide={{
	duration: 1500,
	delay: 300,
}}> 

<h1 class="stylized">Projects</h1>

<div class="flex-container">
    <div class ="flex-item">
        <a href = "https://itch.io/jam/gmtk-2025/rate/3778108">
        <img src="/itchtitle.png" alt="itch banner" >
    </a>
    </div>
    <div class ="flex-item">A game my friends and I released on Aug 3rd for the 2025 GMTK Game Jam!!

    </div>

</div>
</div>
<style>
   /* body { 
    background-color:rgb(111, 145, 135);
   } */
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
        margin-left: 10%;
        margin-right: 10%;
    }
    .gradientbg {
        background: linear-gradient(-45deg, #4b5448, #8cb8a6, #708d6d, rgb(194, 224, 175));
        background-size: 400% 400%;
        animation: gradient 5s ease infinite;
        padding-bottom: 100px; /* so content doesn't get cut off */
        border-radius: 20px;
        margin: 2rem;
        padding: 2rem;
        border-width: 4px;
        border-color: #46352e;
        border-color: color-mix(in srgb-linear, color 40%, color 30%);
    }
        @keyframes gradient {
        0% {
            background-position: 0% 50%;
        }
        50% {
            background-position: 100% 50%;
        }
        100% {
            background-position: 0% 50%;
        }
    }
    .flex-container {
        border-radius: 20px;
        display: flex;
        justify-content: space-around;
        align-items: column;
        margin-left: 10%;
        margin-right: 10%;
      }

      .flex-item {
        border-radius: 20px;
        padding: 10px;
        background-color: lightblue;
        margin: 5px;
      }

</style>