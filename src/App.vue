<template>
  <div id="app">

    <h1>Movie Words Emotion Over Time</h1>
    <!-- <div v-for="movie in movies">
      <h2>{{ movie.label }}</h2>

      <div style="height: 50px; border: 1px solid black; display: flex; flex-direction: row;">
        <div
        @click="() => {
          movie.lineColor = getColor(movie.posRatings[index])
          }"
        v-for="(rating, index) in movie.posRatings"
        style="height: 50px;"
        :style="{ width: (1/movie.posRatings.length)*100 + '%'}"
        >
          <div

          style="height: 100%; width: 100%"
          :style="{backgroundColor: getColor(movie.posRatings[index])}">
          </div>
        </div>
      </div>
      </div>

      {{ movieDataJson1[0] }} -->
      {{ movieLine }}
      <div style="height: 50px; border: 1px solid black; display: flex; flex-direction: row;">
        <div
        @click="movieLine = line.MovieLine"
        v-for="line in movieArray[indexForMovie]"
        style="height: 50px;"
        :style="{ width: (1/movieArray[indexForMovie].length)*100 + '%'}"
        >
          <div

          style="height: 100%; width: 100%"
          :style="{backgroundColor: getColor(line.NumPositiveRatings)}">
          </div>
        </div>
      </div>

      <div @click="indexForMovie++">
        up
      </div>
      <div @click="indexForMovie--">
        down
      </div>

      <!-- <div v-for="(movie, indexMovie) in movies">
        <h2>{{ indexMovie + 1 }}: &nbsp;{{ movie.label }}</h2>
        <h3 :style="{color: movie.lineColor}">{{ movie.clickedLine }}</h3>
        <div style="height: 50px; border: 1px solid black; display: flex; flex-direction: row;">
          <div
          @click="() => {
            movie.clickedLine = line
            movie.lineColor = getColor(movie.posRatings[index])
            }"
          v-for="(line, index) in movie.lines"
          style="height: 50px;"
          :style="{ width: (1/movie.lines.length)*100 + '%'}"
          >
            <div

            style="height: 100%; width: 100%"
            :style="{backgroundColor: getColor(movie.posRatings[index])}">
            </div>
          </div>
        </div>
      </div> -->
  </div>
</template>

<script>
import movieDataJson1 from './assets/1.json'
import movieDataJson2 from './assets/2.json'
import movieDataJson3 from './assets/3.json'
import movieDataJson4 from './assets/4.json'
import movieDataJson5 from './assets/5.json'
import movieDataJson6 from './assets/6.json'
import movieDataJson7 from './assets/7.json'
import movieDataJson8 from './assets/8.json'
import movieDataJson9 from './assets/9.json'
import movieDataJson10 from './assets/10.json'
import movieDataJson11 from './assets/11.json'
import movieDataJson12 from './assets/12.json'
import movieDataJson13 from './assets/13.json'
import movieDataJson14 from './assets/14.json'
import movieDataJson15 from './assets/15.json'
import movieDataJson16 from './assets/16.json'
import movieDataJson17 from './assets/17.json'
import movieDataJson18 from './assets/18.json'
import movieDataJson19 from './assets/19.json'
import movieDataJson20 from './assets/20.json'
import movieDataJson21 from './assets/21.json'
import movieDataJson22 from './assets/22.json'
import movieDataJson23 from './assets/23.json'
import movieDataJson24 from './assets/24.json'
import movieDataJson25 from './assets/25.json'
import movieDataJson26 from './assets/26.json'
import movieDataJson27 from './assets/27.json'
import movieDataJson28 from './assets/28.json'
import movieDataJson29 from './assets/29.json'
import movieDataJson30 from './assets/30.json'
import movieDataJson31 from './assets/31.json'
import movieDataJson32 from './assets/32.json'
import movieDataJson33 from './assets/33.json'
import movieDataJson34 from './assets/34.json'
import movieDataJson35 from './assets/35.json'
import movieDataJson36 from './assets/36.json'
import movieDataJson37 from './assets/37.json'
import movieDataJson38 from './assets/38.json'
import movieDataJson39 from './assets/39.json'
import movieDataJson40 from './assets/40.json'
import movieDataJson41 from './assets/41.json'
import movieDataJson42 from './assets/42.json'
import movieDataJson43 from './assets/43.json'
import movieDataJson44 from './assets/44.json'
import movieDataJson45 from './assets/45.json'
import movieDataJson46 from './assets/46.json'
import movieDataJson47 from './assets/47.json'
import movieDataJson48 from './assets/48.json'
import movieDataJson49 from './assets/49.json'
import movieDataJson50 from './assets/50.json'
export default {
  name: 'app',
  methods: {
    getColor(number) {
      if (number === 1) {
        return '#dd3e54'
      }
      if (number === 2) {
        return '#ca5a5c'
      }
      if (number === 3) {
        return '#b77664'
      }
      if (number === 4) {
        return '#a4916d'
      }
      if (number === 5) {
        return '#91ad75'
      }
      if (number === 6) {
        return '#7ec97d'
      }
      if (number === 7) {
        return '#6be585'
      }
    }
  },
  data () {
    return {
      msg: 'Welcome to Your Vue.js App',
      movieArray: [movieDataJson1,
        movieDataJson2,
        movieDataJson3,
        movieDataJson4,
        movieDataJson5,
        movieDataJson6,
        movieDataJson7,
        movieDataJson8,
        movieDataJson9,
        movieDataJson10,
        movieDataJson11,
        movieDataJson12,
        movieDataJson13,
        movieDataJson14,
        movieDataJson15,
        movieDataJson16,
        movieDataJson17,
        movieDataJson18,
        movieDataJson19,
        movieDataJson20,
        movieDataJson21,
        movieDataJson22,
        movieDataJson23,
        movieDataJson24,
        movieDataJson25,
        movieDataJson26,
        movieDataJson27,
        movieDataJson28,
        movieDataJson29,
        movieDataJson30,
        movieDataJson31,
        movieDataJson32,
        movieDataJson33,
        movieDataJson34,
        movieDataJson35,
        movieDataJson36,
        movieDataJson37,
        movieDataJson38,
        movieDataJson39,
        movieDataJson40,
        movieDataJson41,
        movieDataJson42,
        movieDataJson43,
        movieDataJson44,
        movieDataJson45,
        movieDataJson46,
        movieDataJson47,
        movieDataJson48,
        movieDataJson49,
        movieDataJson50],
      movieLine: 'Click the bar',
      indexForMovie: 0
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
