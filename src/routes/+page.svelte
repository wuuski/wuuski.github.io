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

<div class="flex-container first">
    <div class ="flex-item myface">
        <img src="myface.png" alt="my face">
    </div>
    <div class ="flex-item info">
        
        
    <p>
        I’m a Data Science student @ UC Berkeley interested in machine learning, computer vision, and data-driven product design. I enjoy working end-to-end from data extraction and feature engineering to interpretable models and usable outputs.


    </p>
    </div>

</div>


<div class="flex-container">
    <div class="flex-item-color hobby-box">
        <p class="hobby-title">
            Outside of Data Science, I love ... 
        </p>
            <ul class="hobby-list">
            <li>Drawing, illustration, and visual design  </li>
            <li>Reading novels! Current: <i>The Count of Monte Cristo</i></li>
            <li>Crochet & fiber arts projects  </li>
            <li>Rock climbing at Mosaic (Berkeley)</li>
            <li>Exploring SF & Bay Area day trips  </li>
            <li>Listening to music!! My lofi playlist is linked to the right! you can play it right here in the browser.</li> 
           </ul>
           
       
    </div>
    <div class="flex-item playlist">
       
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
            src="https://lanyard-profile-readme.vercel.app/api/696197741788921969?bg=ab9b8c&borderRadius=15px"
            alt="Discord Presence"
            style=" border-radius: 20px; margin-top: 20px; width:150%; width: 100%; max-width: 500px; border-width:2px;borderColor=4b5448"
          />
          </a>
       </div>
       <div class="flex-item">
        <p>
            what I'm listening to::
            live update of my spotify! 
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
        background: linear-gradient(-45deg, #8690a2, #d2c296, #35495d, #e0decd);
        background-size: 400% 400%;
        animation: gradient 8s ease infinite;
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
    li { 
        font-family:'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        font-size: 20px;
        margin-left:20px;
    }
    /* .diplocaulus { 
        color: rgb(66, 97, 66);
        text-decoration: underline;
    }
    .diplocaulus:hover { 
        color: rgb(97, 125, 97);
    } */
    .stylized { 
        text-align: center;
        padding: 10px;
        background-color: #e0d0cd;
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
        transition: opacity 0.3s ease;
      }
      .flex-item-color { 
        border-radius: 20px;
        padding: 10px;
        background-color: #e0d0cd;
        margin: 5px;
        border-color: rgb(76, 68, 54);
        border-width: 2px;
		align-items: row; 
      }
      :global(.flex-item-color:hover) { 
        transform: translateY(-5px);
        box-shadow: 0 4px 12px rgba(0, 0, 0, 0.2);
        transition: all 0.2s ease-in-out;
      }
      .flex-item:hover { 
        transform: translateY(-5px);
        box-shadow: 0 4px 12px rgba(0, 0, 0, 0.2);
        transition: all 0.2s ease-in-out;
        
      }
      .hobby-box {
        display: flex;
  flex-direction: column;
  justify-content: flex-start; /* not space-between */
  gap: 1rem;  
}
.hobby-list {
    margin: 0;
  padding-left: 1.2rem;
  list-style: disc;
  display: flex;
  flex-direction: column;
  gap: 0.6rem;
  flex: 1;
  display: flex;
  
}
.hobby-title { margin: 0; }
@media (max-width: 1450px) {
    .myface {
    opacity: 0;
    pointer-events: none;
    height: 0;
    overflow: hidden;
  }
  .first{
    flex-direction: column;
    align-items: center;
  }
/*   
  .info{
    flex: none;
    width: 100%;
    max-width: 520px;   
  } */
}
/* .myface, .playlist{
    transition: opacity 0.5s ease;
} */
@media (max-width: 1200px) {
    .myface,
    .playlist {
    opacity: 0;
    pointer-events: none;
    height: 0;
    overflow: hidden;
  }
  .flex-container{
    flex-direction: column;
    align-items: center;
  }
  
  /* .flex-item{
    flex: none;
    width: 100%;
    max-width: 520px;   
  } */
}
/*       
      .flex-item.right { 
        flex:2;
        
      } */
</style>