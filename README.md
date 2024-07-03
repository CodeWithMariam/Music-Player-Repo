# Music Player App

This project is a simple music player app that allows users to play, pause, and seek through a song. The app displays the song's progress and updates it in real time.

## Features
- Play and pause functionality.
- Displays song progress.
- Allows seeking through the song.
- Updates the progress bar in real time.

## How It Works
The JavaScript code controls the play/pause functionality, updates the song progress, and handles seeking through the song. The `setInterval` function is used to update the progress bar every 300 milliseconds when the song is playing.

## Code Explanation
```javascript
let progress = document.getElementById("progress");
let song = document.getElementById("song");
let ctrlIcon = document.getElementById("ctrlIcon");

function playPause() {
    if (ctrlIcon.classList.contains("fa-pause")) {
        song.pause();
        ctrlIcon.classList.remove("fa-pause");
        ctrlIcon.classList.add("fa-play");
    } else {
        song.play();
        ctrlIcon.classList.add("fa-pause");
        ctrlIcon.classList.remove("fa-play");
    }
}

song.onloadedmetadata = function() {
    progress.max = song.duration;
    progress.value = song.currentTime;

    setInterval(() => {
        if (!song.paused) {
            progress.value = song.currentTime;
        }
    }, 300);
}

progress.onchange = function() {
    song.currentTime = progress.value;
    if (song.paused) {
        song.play();
        ctrlIcon.classList.add("fa-pause");
        ctrlIcon.classList.remove("fa-play");
    }
}
```
## Explanation
This section provides a detailed explanation of how the code works:

- The playPause function toggles between playing and pausing the song and updates the control icon accordingly.
- The onloadedmetadata event sets the maximum value of the progress bar to the song's duration and updates the progress bar every 300 milliseconds using setInterval.
- The onchange event allows the user to seek through the song by updating the song's current time and resuming playback if paused.
## Additional Resources
Here are some articles that might help you understand the concepts used in this project:

# Additional Resources

Here are some articles that might help you understand the concepts used in this project:

- [Building a Music Player in JavaScript](https://www.geeksforgeeks.org/create-a-music-player-using-javascript/)
- [Using the HTML5 Audio Element](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/audio)
- [JavaScript setInterval and clearInterval](https://developer.mozilla.org/en-US/docs/Web/API/WindowOrWorkerGlobalScope/setInterval)
- [HTML DOM classList Property](https://developer.mozilla.org/en-US/docs/Web/API/Element/classList)
- [HTML5 Audio API Basics](https://developer.mozilla.org/en-US/docs/Web/API/Web_Audio_API)


## Contributing
If you'd like to contribute to this project, please fork the repository and submit a pull request.

## License
This project is licensed under the MIT License. See the LICENSE file for details.

