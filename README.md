<!-- # Music-Player -->
<!-- First Project on GitHub. This is a project of a music player as based on HTML , CSS , JavaScript.  -->

<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Music Player Design - Easy Tutorials</title>
    <link rel="stylesheet" href="style.css">
    <script src="https://kit.fontawesome.com/d33f4078ae.js" crossorigin="anonymous"></script>
</head>

<body>
    <div class="container"></div>
    <div class="music-player">
        <nav>
            <div class="circle">
                <i class="fa-solid fa-angle-left"></i>
            </div>
            <div class="circle">
                <i class="fa-solid fa-bars"></i>
            </div>
        </nav>
        <img src="thumbnail.png" alt="" class="song-img">
        <h1>Despacito</h1>
        <p>Luis fonsi Ft. Puerto Rican</p>

        <audio id="song">
            <source src="/Go-NEFFEX.mp3" type="audio/mpeg">
        </audio>
        <input type="range" value="0" id="progress">

        <div class="controls">
            <div><i class="fa-solid fa-backward"></i></div>
            <div onclick="playPause()"> <i class="fa-solid fa-play" id="ctrlIcon"></i></div>
            <div><i class="fa-solid fa-forward"></i></div>

        </div>

    </div>
 
    <script>

        let progress = document.getElementById("progress");
        let song = document.getElementById("song");
        let ctrlIcon = document.getElementById("ctrlIcon");

        song.onloadedmetadata = function () {
            progress.max = song.duration;
            progress.value = song.curentTime;
        }

        function playPause() {
            if (ctrlIcon.classList.contains("fa-pause")) {
                song.pause();
                ctrlIcon.classList.remove("fa-pause");
                ctrlIcon.classList.add("fa-play");

            }
            else {
                song.play();
                ctrlIcon.classList.add("fa-pause");
                ctrlIcon.classList.remove("fa-play");

            }
        }

        if (song.play) {
            setInterval(() => {
                progress.value = song.currentTime;
            }, 500);

        }

        progress.onchange = function () {
            song.play();
            song.currentTime = progress.value;
            ctrlIcon.classList.add("fa-pause");
            ctrlIcon.classList.remove("fa-play");
        }



    </script>
</body>

</html>





<!-- css file as style.css -->

* {
  margin: 0;
  padding: 0;
  font-family: "poppins", sans-serif;
  box-sizing: border-box;
  align-items: center;
}

.container {
  width: 100%;
  height: 100%;
  background: #fff;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-wrap: wrap;
}

.music-player {
  background: #333;
  width: 400px;
  padding: 25px 35px;
  text-align: center;
}

nav {
  display: flex;
  justify-content: space-between;
  margin-bottom: 30px;
}

nav .circle {
  border-radius: 50%;
  width: 40px;
  height: 40px;
  line-height: 40px;
  background: #fff;
  color: #f53192;
  box-shadow: 0 5px 10px rgba(255, 26, 26, 0.22);
}

.song-img {
  width: 220px;
  border-radius: 50%;
  border: 8px solid #fff;
  box-shadow: 0 10px 60px rgba(255, 26, 26, 0.22);
}

.music-player h1 {
  font-size: 20px;
  font-weight: 400;
  color: #fff;
  margin-top: 20px;
}

.music-player p {
  font-size: 14px;
  color: #fff;
}

#progress {
  -webkit-appearance: none;
  width: 100%;
  height: 6px;
  background: #f53192;
  border-radius: 4px;
  cursor: pointer;
  margin: 40px 0;
}

#progress::-webkit-slider-thumb {
  -webkit-appearance: none;
  background: #f53192;
  width: 30px;
  height: 30px;
  border-radius: 50%;
  border: 8px solid #fff;
  box-shadow: 0 5px 5px rgba(255, 26, 26, 0.22);
}

.controls {
  display: flex;
  justify-content: center;
  align-items: center;
}

.controls div {
  width: 60px;
  height: 60px;
  margin: 20px;
  background: #fff;
  display: inline-flex;
  align-items: center;
  justify-content: center;
  border-radius: 50%;
  color: #f53192;
  box-shadow: 0 10px 20px rgba(255, 26, 26, 0.22);
  cursor: pointer;
}

.controls div:nth-child(2) {
  transform: scale(1.5);
  background-color: #f53192;
  color: #fff;
}
