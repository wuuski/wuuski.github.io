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
	delay: 400,
}}> <h1 class="stylized">Portfolio</h1>

<div class="flex-container">
    
    <div class ="flex-item" style="padding-left:30%; padding-right:30%;">
        I've loved doing visual art all my life, here's a snippet of some of my favorite art pieces I've made!!
    
    </div>

</div>
<div class="flex-container">
    <div class ="flex-item">
        <a href = "https://itch.io/jam/gmtk-2025/rate/3778108">
        <img src="grandpapatio.png" alt="A watercolor painting of a cat" >
    </a>
    </div>
   

</div>
<div class="flex-container">
    <div class ="flex-item">
        <a href = "https://itch.io/jam/gmtk-2025/rate/3778108">
        <img src="/Edgar.png" alt="A watercolor painting of a cat" >
    </a>
    </div>
    <div class ="flex-item">
        <a href = "https://itch.io/jam/gmtk-2025/rate/3778108">
            <img src="/The Cozy Hole-in-the-Tree.png" alt="digital painting of a magical forest" >
        </a>
    </div>

</div>
<div class="flex-container">
    <div class ="flex-item">
        <a href = "https://itch.io/jam/gmtk-2025/rate/3778108">
        <img src="Scientists' Refuge.png" alt="A watercolor painting of a cat" >
    </a>
    </div>
   

</div>
<div class="flex-container">
    <div class ="flex-item">
        <a href = "https://itch.io/jam/gmtk-2025/rate/3778108">
        <img src="/Betty.png" alt="A watercolor painting of a cat" >
    </a>
    </div>
    <div class ="flex-item">
        <a href = "https://itch.io/jam/gmtk-2025/rate/3778108">
            <img src="/Angela.png" alt="digital painting of a magical forest" >
        </a>
    </div>

</div>
<div class="flex-container">
    <div class ="flex-item">
        <a href = "https://itch.io/jam/gmtk-2025/rate/3778108">
        <img src="/The Shell.png" alt="A watercolor painting of a cat" >
    </a>
    </div>
    

</div>
<div class="flex-container">
    <div class ="flex-item">
        <a href = "https://itch.io/jam/gmtk-2025/rate/3778108">
        <img src="/girlpainting.png" alt="A watercolor painting of a cat" >
    </a>
    </div>
    <div class ="flex-item">
        <a href = "https://itch.io/jam/gmtk-2025/rate/3778108">
            <img src="/mishpainting.png" alt="digital painting of a magical forest" >
        </a>
    </div>

</div>
</div>
<style>
   /* body { 
    background-color:rgb(111, 145, 135);
   } */
   .gradientbg {
        background: linear-gradient(-45deg, #544d48, #9ccc85, #708d6d, rgb(175, 224, 213));
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
    h1 {
        color:rgb(54, 57, 78);
        font-family:'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
        font-size:50px;
    }
   
    .stylized { 
        text-align: center;
        padding: 10px;
        background-color: rgb(213,208,186);
        margin: 5px;
        border-radius: 30px;
        margin-left: 10%;
        margin-right: 10%;
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
        background-color: rgb(176,181,158);
        margin: 5px;
        border-color: rgb(76, 68, 54);
        border-width: 2px;
      } 

</style>