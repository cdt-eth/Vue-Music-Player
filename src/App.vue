<template>
  <div id="app">
    <header>
      <h1>My Music</h1>
    </header>
    <main>
      <section class="player">
        <!-- 2) template strings, from our data -->
        <h2 class="song-title">
          {{ current.title }} - <span> {{ current.artist }} </span>
        </h2>
        <div class="controls">
          <button class="prev">Prev</button>
          <button class="play" v-if="!isPlaying">Play</button>
          <button class="pause" v-else>Pause</button>
          <button class="next">Next</button>
        </div>
        <!-- {{ songs[0].src }} -->
      </section>
    </main>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      // our props
      current: {},
      index: 0,
      isPlaying: false,
      songs: [
        {
          title: "Begin Again",
          artist: "Nick Mulvey",
          src: require("./assets/Nick Mulvey - Begin Again.mp3"),
        },
        {
          title: "When I Look At You",
          artist: "Rosie Carney",
          src: require("./assets/Rosie Carney - When I Look At You.mp3"),
        },
        {
          title: "Call Me When You Land",
          artist: "Old Sea Brigade",
          src: require("./assets/Old Sea Brigade & Luke Sital-Singh - Call Me When You Land.mp3"),
        },
      ],
      player: new Audio(),
    };
  },
  created() {
    this.current = this.songs[this.index];
    this.player.src = this.current.src;
    // this.player.play();
  },
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
body {
  font-family: sans-serif;
}
header {
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 15px;
  background-color: #212121;
  color: #fff;
}
main {
  width: 100%;
  max-width: 768px;
  margin: 0 auto;
  padding: 25px;
}
.song-title {
  color: #53565a;
  font-size: 32px;
  font-weight: 700;
  text-transform: uppercase;
  text-align: center;
}
.song-title span {
  font-weight: 400;
  font-style: italic;
}
.controls {
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 30px 15px;
}
button {
  appearance: none;
  background: none;
  border: none;
  outline: none;
  cursor: pointer;
}
button:hover {
  opacity: 0.8;
}
.play,
.pause {
  font-size: 20px;
  font-weight: 700;
  padding: 15px 25px;
  margin: 0px 15px;
  border-radius: 8px;
  color: #fff;
  background-color: #cc2e5d;
}
.next,
.prev {
  font-size: 16px;
  font-weight: 700;
  padding: 10px 20px;
  margin: 0px 15px;
  border-radius: 6px;
  color: #fff;
  background-color: #ff5858;
}
.playlist {
  padding: 0px 30px;
}
.playlist h3 {
  color: #212121;
  font-size: 28px;
  font-weight: 400;
  margin-bottom: 30px;
  text-align: center;
}
.playlist .song {
  display: block;
  width: 100%;
  padding: 15px;
  font-size: 20px;
  font-weight: 700;
  cursor: pointer;
}
.playlist .song:hover {
  color: #ff5858;
}
.playlist .song.playing {
  color: #fff;
  background-image: linear-gradient(to right, #cc2e5d, #ff5858);
}
</style>
