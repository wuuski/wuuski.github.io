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
    
    <div class ="flex-item" >
        <p>
        I've loved doing visual art all my life, here's a snippet of some of my favorite art pieces I've made!!
      </p>
    </div>

</div>
<div class="flex-container">
    <div class ="flex-item">
        <img src="grandpapatio.png" alt="A watercolor painting of a cat" >
    </div>
   

</div>
<div class="flex-container">
    <div class ="flex-item">
        <img src="/Edgar.png" alt="A watercolor painting of a cat" >
    </div>
    <div class ="flex-item">
            <img src="/The Cozy Hole-in-the-Tree.png" alt="digital painting of a magical forest" >
    </div>

</div>
<div class="flex-container">
    <div class ="flex-item">
        <img src="Scientists' Refuge.png" alt="A watercolor painting of a cat" >
    </div>
   

</div>
<div class="flex-container">
    <div class ="flex-item">
        <img src="/Betty.png" alt="A watercolor painting of a cat" >
    </div>
    <div class ="flex-item">
            <img src="/Angela.png" alt="digital painting of a magical forest" >
    </div>

</div>
<div class="flex-container">
    <div class ="flex-item">
        <img src="/The Shell.png" alt="A watercolor painting of a cat" >
    </div>
    

</div>
<div class="flex-container">
    <div class ="flex-item">
        <img src="/girlpainting.png" alt="A watercolor painting of a cat" >
    </div>
    <div class ="flex-item">
            <img src="/mishpainting.png" alt="digital painting of a magical forest" >
    </div>

</div>
</div>
<style>
   /* body { 
    background-color:rgb(111, 145, 135);
   } */
   .gradientbg {
        background: linear-gradient(-45deg, #8690a2, #d2c296, #35495d, #e0decd);
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
    p { 
        font-family:'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            font-size: 30px;
        text-align: center;
   }
    .stylized { 
        text-align: center;
        padding: 10px;
        background-color: #e0d0cd;
        margin: 5px;
        border-radius: 30px;
        margin-left: 10%;
        margin-right: 10%;
        border-color: rgb(59, 50, 50);
        border-width: 3px;
    }


    .flex-container {
        border-radius: 20px;
        display: flex;
        justify-content: space-around;
        align-items: column;
        margin-left: 10%;
        margin-right: 10%;
      }

</style>