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

<h1 class="stylized">Recent Projects</h1>
<div class ="flex-item-p">
    <p>
    Still a work in progress, more projects to come soon! Click on the images to learn more
    </p>
</div>
<div class="flex-container">
    <div class ="flex-item-projects">
        <a href = "https://itch.io/jam/gmtk-2025/rate/3778108" target="_blank">
        <img src="/itchtitle.png" alt="itch banner" >
    </a>
    </div>
    <div class ="flex-item">
        <p>
            A silly fishing game where Terry the cat captain and his crew use rope nets to catch fish! Made for the 2025 GMTK Game Jam.
        </p>
    </div>

</div>
<div class="flex-container">
    <div class ="flex-item-projects">
        <a href = "https://drive.google.com/file/d/1QkYQZWJ6dqt-i1KgiO_hFSaXbRsxEP2X/view?usp=drive_link" target="_blank">
        <img src="/StaticFirePicture.jpg" width= 315px alt="Dawn Runner Rocket Engine Firing" >
    </a>
    </div>
    <div class ="flex-item">
        <p>
            Documentation of Dawn Runner, a hybrid rocket engine developed by our student team of six, including design overview, engine performance, and construction details.
        </p>
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
        font-family:'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        font-size: 25px;
        text-align: center;
        padding: 10px;
    }
   
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
        margin-top: 10px;
        margin-bottom: 10px;
      }
      .flex-item-p {
        border-radius: 20px;
        padding: 10px;
        margin-left: 500px;
        margin-right: 10%;
        background-color: #fcedd3;
        margin: 5px;
        border-color: rgb(76, 68, 54);
        border-width: 2px;
		align-items: row; 
        
        
      }
      .flex-item {
        border-radius: 20px;
        padding: 10px;
        margin-left: 500px;
        margin-right: 10%;
        background-color: #fcedd3;
        margin: 5px;
        border-color: rgb(76, 68, 54);
        border-width: 2px;
		align-items: row; 
        max-width: 600px;
        
      }
      .flex-item-projects {
        border-radius: 20px;
        padding: 10px;
        background-color: rgb(176,181,158);
        margin: 5px;
        border-color: rgb(76, 68, 54);
        border-width: 2px;
		align-items: row; 
        text-align: center;
      }

      .flex-item-projects:hover { 
        transform: translateY(-5px);
        box-shadow: 0 4px 12px rgba(0, 0, 0, 0.2);
        transition: all 0.2s ease-in-out;
        background-color: #7f998b;
      }
    

</style>