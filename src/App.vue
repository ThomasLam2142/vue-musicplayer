<script setup lang="ts">
import { ref } from 'vue';
const songs = ref([
  { name: 'Gods Plan', location: 'https://audio.jukehost.co.uk/5X0oisXZVYaUIhNV8jfQoN0mSPeaFpiS' },
  { name: 'Life is Good', location: 'https://audio.jukehost.co.uk/VclVDhAHUzqduMfogz8xJcssa5vycNcm' },
  { name: 'Sticky', location: 'https://audio.jukehost.co.uk/cuP9VS4ulcEsjGfaXQoXY3Ho41hpFmIm' },
  { name: 'Search & Rescue', location: 'https://audio.jukehost.co.uk/R26lKM0xugVb5ghjtx61hPw1L0FIOM99' },
  { name: 'Currents', location: 'https://audio.jukehost.co.uk/i4Y7diJX9qqAhOJVDiUkvyp88xJyQ6cP' },
]);

const currentSong = ref({
  name: 'Gods Plan',
  location: 'https://audio.jukehost.co.uk/5X0oisXZVYaUIhNV8jfQoN0mSPeaFpiS3'
});

const audioRef = ref(null);

function playTrack(songLocation: string,songName: string) {
  currentSong.value.location = songLocation;
  currentSong.value.name = songName;
  audioRef.value.load();
  audioRef.value.play();
}



</script>

<template>
  <header>
    <nav id="pageNav">
      <ul>
        <li>
          <a :href="'https://github.com/ThomasLam2142/vue-musicplayer/tree/main'" target="_blank">
            Github
            <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" class="bi bi-github" viewBox="0 0 16 16">
              <path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.012 8.012 0 0 0 16 8c0-4.42-3.58-8-8-8z"/>
            </svg>
          </a>
        </li>
      </ul>
      
    </nav>
  </header>
    <div class="wrapper">
      <div>
        <img src="./assets/drake.jpg" alt="drakeImg" id="drakeImg" style="max-width: 250px; max-height: 250px;" />
      </div>  

      <div>
        <input type="text" id="searchBar" placeholder="Search" />
      </div>
    
      



      <div>
        <ul>
          <li v-for="(song, index) in songs" :key="index">{{ song.name }}<button class="playBtn" @click="playTrack(song.location,song.name)">Play</button> </li>

        </ul>
      </div>
      
      <div id="audioPlayer">
        <img src="https://media.tenor.com/ADP4nszb5AcAAAAi/shigure-ui-dance.gif" alt="this slowpoke moves"  width="250" />
        <div id='nowPlayingText'>
          Now Playing:  {{ currentSong.name }}
        </div>
        <audio ref="audioRef" controls :src="currentSong.location">
        </audio>
      </div>

    </div>


</template>

<style scoped>

*,footer{
  background-color: #989898;
}

.wrapper {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;

  margin: 0 auto;

}

header{
  background-color: #333;
  padding: 0px;
  text-align: center;
  font-size: 20px;
  color: white;
}

#pageNav{
  display: flex;
  justify-content: flex-end;
  align-items: center;
  padding-right: 100px;
}

#drakeImg {
  border-radius: 50%;
  margin: 0 auto;
  display: block;
}

#audioPlayer {

}

.playBtn{
  background-color: #4CAF50;
  border: none;
  color: white;
  padding: 5px 10px;
  margin-left: 15px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 16px;
}

.playBtn:hover {
  background-color: #3e8e41;
}

#nowPlayingText{
  font-size: 20px;
  font-weight: bold;
  margin-top: 10px;
  margin-bottom: 10px;
}

</style>
