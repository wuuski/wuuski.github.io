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
        <a href = "https://image-popularity-yolo.streamlit.app/" target="_blank">
        <img src="/yolo2.png" alt="yolo" >
    </a>
    </div>
    <div class ="flex-item project-text">

        <p>
    Image Popularity Prediction

    <li>I built an end-to-end machine learning system that predicts whether an image will be popular based on visual features.</li>
	<li>Used YOLOv11 to detect objects and compute spatial distributions across a 3×3 grid</li>
	<li>Engineered color statistics (RGB mean / variance) from raw pixels</li>
    <li> Trained and compared Random Forest and LightGBM models </li>
    <li> Deployed an interactive Streamlit web app for real-time inference and model interpretability</li>
    <li>Tech: Python, OpenCV, YOLO, LightGBM, scikit-learn, Streamlit</li>
        </p>
    </div>

</div>
<div class="flex-container">
    
    <div class ="flex-item-projects">
        <a href = "https://itch.io/jam/gmtk-2025/rate/3778108" target="_blank">
        <img src="/itchtitle.png" alt="itch banner" >
    </a>
    </div>
    <div class ="flex-item project-text">
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
    <div class ="flex-item project-text">
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
        font-size: 20px;
        text-align: center;
        padding: 10px;
    }
    li { 
        font-family:'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        font-size: 20px;
        margin-left:20px;
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
        display: flex;
        align-items: center;        /* vertical alignment */
        justify-content: center;    /* center the whole row */
        gap: 40px;                  /* space between image + text */
        margin: 20px auto;
        max-width: 1100px;
        }
    /* .flex-container {
        border-radius: 20px;
        display: flex;
        justify-content: space-around;
        align-items: column;
        margin-left: 10%;
        margin-right: 10%;
        margin-top: 10px;
        margin-bottom: 10px;
      } */
      .flex-item-p {
        border-radius: 20px;
        padding: 10px;
        /* margin-left: 500px; */
        /* margin-right: 10%; */
        background-color: #fcedd3;
        margin: 5px;
        border-color: rgb(76, 68, 54);
        border-width: 2px;
		align-items: row; 
        
        
      }
      .project-text {
  transition: opacity 0.3s ease;
}

@media (max-width: 900px) {
    .flex-container{
    flex-direction: column;
    align-items: center;
  }
  .flex-item-projects,
  .flex-item{
    flex: none;
    width: 100%;
    max-width: 520px;   /* tweak: 480–600 */
  }
  .project-text {
    opacity: 0;
    pointer-events: none;
    height: 0;
    overflow: hidden;
  }
}
      /* .flex-item {
        border-radius: 20px;
        padding: 10px; */
        /* margin-left: 500px; */
        /* margin-right: 10%; */
        /* background-color: #fcedd3;
        margin: 5px;
        border-color: rgb(76, 68, 54);
        border-width: 2px;
		align-items: row; 
        max-width: 600px;
        
      } */
      /* .flex-item {
        flex: 1;           
        max-width: 600px;
        background-color: #fcedd3;
        } */
        .flex-item,
.flex-item-p {
  background-color: #fcedd3;
  border-radius: 20px;
  border: 2px solid rgb(76, 68, 54);
  padding: 20px;
  flex:1;
}
.flex-item-projects img {
  width: 100%;
  
  height: auto;
  display: block;
  border-radius: 12px; /* optional inner softness */
}
      /* .flex-item-projects {
        border-radius: 20px;
        padding: 10px;
        background-color: rgb(176,181,158);
        margin: 5px;
        border-color: rgb(76, 68, 54);
        border-width: 2px;
		align-items: row; 
        text-align: center;
      } */
      .flex-item-projects {
        background-color: rgb(176, 181, 158); /* green card */
        border-radius: 20px;
        border: 2px solid rgb(76, 68, 54);
        padding: 15px;
        overflow: hidden;
        flex:1.6;
        }

      .flex-item-projects {
        flex: 0 0 320px;   /* fixed image column */
        text-align: center;
        }
   
      .flex-item-projects:hover { 
        transform: translateY(-5px);
        box-shadow: 0 4px 12px rgba(0, 0, 0, 0.2);
        transition: all 0.2s ease-in-out;
        background-color: #7f998b;
      }
      .flex-item-projects { flex: 0 0 45%; }
      .flex-item         { flex: 0 0 55%; }

</style>