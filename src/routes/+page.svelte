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

<!-- <Navbar /> -->
 <div class="gradientbg"  in:slide={{
	duration: 1500,
	delay: 300,
}}> 
<h1 class="stylized">Hi! I'm Angela</h1>

<div class="flex-container">
    <div class ="flex-item">
        <img src="myface.png" alt="my face">
    </div>
    <div class ="flex-item">
        
        
    <p>
        Hello!! I’m Angela.
        I like making things — games, painting, going outside. Current rising freshman @ UC Berkeley. Big fan of playing video games, matcha, reading, and quiet mornings.
    </p>
    </div>

</div>


<div class="flex-container">
    <div class="flex-item-color">
        <p>
            I love music!!! I love music!!! I love music!!! I love music!!! I love music!!! I love music!!! 
            I love music!!! I love music!!! I love music!!! I love music!!! 
            I love music!!! 
            vI love music!!! 
        </p>
    </div>
    <div class="flex-item">
       
    <iframe 
        title="myplaylist"
        data-testid="embed-iframe" 
        style="border-radius:12px" 
        src="https://open.spotify.com/embed/playlist/0YZIIA1habXmMmVAqh1QxW?utm_source=generator" 
        width=400rem 
        height=400px 
        
        frameBorder="0" 
        allowfullscreen="" 
        allow="autoplay; clipboard-write; encrypted-media; fullscreen; picture-in-picture" 
        loading="lazy">
    </iframe>


   
  </div>
  
</div>
<div class="flex-container">
    <div class="discordbox">
        <a href="https:discord.gg/j3vkCSTTfr" class="discordbox">
            <img
            src="https://lanyard-profile-readme.vercel.app/api/696197741788921969?bg=556618&borderRadius=15px"
            alt="Discord Presence"
            style=" border-radius: 20px; margin-top: 20px; width:150%; width: 100%; max-width: 500px; border-width:2px;borderColor=4b5448"
          />
          </a>
       </div>
       <div class="flex-item">
        <p>
            Why Veridiplo? 
            Combination of Veridis Quo, my favorite Daft Punk song, and my favorite fossil: diplocaulus
        </p>
       </div>
</div>
</div>
<style>
    .discordbox { 
        /* display: flex; */
        justify-content: space-around;
        align-items: row; 
        /* width: fit-content; */
        height: fit-content;
        min-width: 30%;
        min-height: 30%;
        
    }
    .discordbox:hover { 
        transform: translateY(-5px);
        box-shadow: 0 4px 12px rgba(0, 0, 0, 0.2);
        transition: all 0.2s ease-in-out;
        
    }
    .gradientbg {
        background: linear-gradient(-45deg, #4b5448, #8cb8a6, #708d6d, #d9e0af);
        background-size: 400% 400%;
        animation: gradient 15s ease infinite;
        padding-bottom: 100px; /* so content doesn't get cut off */
        border-radius: 20px;
        margin: 3rem;
        padding: 3rem;
        border-width: 4px;
        border-color: #46352e;
        border-color: color-mix(in srgb-linear, color 40%, color 30%);
}
    

/* Your existing keyframes */
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
        font-size: 25px;
    }

    .stylized { 
        text-align: center;
        padding: 10px;
        background-color: rgb(213,208,186);
        margin: 5px;
        border-radius: 30px;
        margin-left: 10%;
        margin-right: 10%;
        border-color: rgb(59, 50, 50);
        border-width: 2px;
    }
    .stylized:hover { 
        transform: translateY(-5px);
        box-shadow: 0 4px 12px rgba(0, 0, 0, 0.2);
        transition: all 0.2s ease-in-out;
        
    }


    .flex-container {
        border-radius: 20px;
        display: flex;
        justify-content: flex-start;
        align-items: column;
        margin-left: 10%;
        margin-right: 10%;
        margin-top:1%;
        
      }
      .flex-item-color { 
        border-radius: 20px;
        padding: 10px;
        background-color: rgb(198, 195, 179);
        margin: 5px;
        border-color: rgb(76, 68, 54);
        border-width: 2px;
		align-items: row; 
      }
      .flex-item:hover { 
        transform: translateY(-5px);
        box-shadow: 0 4px 12px rgba(0, 0, 0, 0.2);
        transition: all 0.2s ease-in-out;
        
      }
      .flex-item.right { 
        flex:2;
        
      }
</style>