<template>
  <div id="app">

    <h1 style="font-weight: bold;">Movie Words Emotion Over Time</h1>

    <p>Each line has been rated independently by seven coders. Sentiment data is restricted to linguistic content only.</p>

    <h2 :style="{color: getColor(movieLine.NumPositiveRatings)}">
    {{ indexForMovie !== null ? movieTitleList[indexForMovie] : 'Select a movie'}}</h2>

    <select v-model="indexForMovie">
      <option disabled value="">Please select one</option>
      <option
      v-for="(title, index) in movieTitleList"
       :value="index">{{ title }}</option>
    </select>


      <h2 :style="{color: getColor(movieLine.NumPositiveRatings)}">
      {{ indexForMovie !== null ? (movieLine.MovieLine ? movieLine.MovieLine : 'Click on the bars! :)') : ''}}</h2>


<transition-group name="fade" appear>
<h2 v-if="indexForMovie !== null" key="sentHeader"  style="margin: 30px 0px -4px 0px">Is the line positive or negative?</h2>Greener means more votes for positive, redder more votes for negative.

      <div
      v-if="indexForMovie !== null"
      key="sentHeader2"
      style="margin-top: 10px; height: 50px; border: 1px solid black; display: flex; flex-direction: row;">
        <div
        @click="movieLine = line"
        v-for="line in movieDataJson1"
        style="height: 50px;"
        :style="{ width: (1/movieDataJson1.length)*100 + '%'}"
        >
          <div

          style="height: 100%; width: 100%"
          :style="{backgroundColor: getColor(line.NumPositiveRatings)}">
          </div>
        </div>
      </div>
      <!-- <div style="background-color: maroon; margin: 27px 0px 0px 0px; height: 50px; display: flex; flex-direction: row;">
        <div
        @click="movieLine = line"
        v-for="line in movieDataJson1"
        style="height: 50px;"
        :style="{ width: (1/movieDataJson1.length)*100 + '%'}"
        >
          <div

          style="width: 100%; background-color: white;"
          :style="{height: (line.NumPositiveRatings/7 * 100) + '%'}">
          </div>
        </div>
      </div> -->


<!-- THOUGHT PROVOKING -->

<h2
  key="tpHeader"
  v-if="indexForMovie !== null"
  style="margin: 30px 0px -4px 0px">Is the line thought provoking?</h2>Taller black bars means more votes.

      <div
      key="tpHeader2"
      v-if="indexForMovie !== null"
      style="position: relative; vertical-align: bottom; background-color: black; margin: 0px 0px 0px 0px; height: 50px; display: flex; flex-direction: row;">
        <div
        @click="movieLine = line"
        v-for="line in movieDataJson1"
        style="height: 50px;"
        :style="{ width: (1/movieDataJson1.length)*100 + '%'}"
        >
          <div

          style="width: 100%; background-color: white;"
          :style="{height: (Math.abs(line.ThoughtProvokingVoteCount/7 - 1) * 100) + '%'}">
          </div>
        </div>
      </div>

      <!-- INTENSITY -->

      <h2 v-if="indexForMovie !== null" key="intenseHeader" style="margin: 30px 0px -4px 0px">Is the line intense?</h2>Taller red bars means more votes.

            <div
            key="intenseHeader2"
            v-if="indexForMovie !== null"
            style="position: relative; vertical-align: bottom; background-color: red; margin: 0px 0px 70px 0px; height: 50px; display: flex; flex-direction: row;">
              <div
              @click="movieLine = line"
              v-for="line in movieDataJson1"
              style="height: 50px;"
              :style="{ width: (1/movieDataJson1.length)*100 + '%'}"
              >
                <div

                style="width: 100%; background-color: white;"
                :style="{height: (Math.abs(line.IntensityVoteCount/7 - 1) * 100) + '%'}">
                </div>
              </div>
            </div>



<h2
v-if="indexForMovie !== null"
key="linesHeader">Movie Lines Color Coded by Sentiment</h2>

      <p
      v-if="indexForMovie !== null"
      key="lines"
      :style="{color: getColor(movie.NumPositiveRatings)}"
      v-for="movie in movieDataJson1">
        {{ movie.MovieLine }}
      </p>
</transition-group>
  </div>
</template>

<script>
export default {
  name: 'app',
  methods: {
    getMovie (index) {
      this.movieDataJson1 = require('./assets/' + index + '.json')
    },
    getColor(number) {
      if (number === 0) {
        return '#dd3e54'
      }
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
  watch: {
    indexForMovie () {
      this.getMovie (this.indexForMovie+1)
    }
  },
  data () {
    return {
      msg: 'Welcome to Your Vue.js App',
      movieDataJson1: null,
      movieLine: 'Click the bar',
      indexForMovie: null,
      movieTitleList: [`Alice in Wonderland (2010)`, 	`Seven Samurai`, 	`Schindler's List`, 	`Harry Potter and the Order of the Phoenix`, 	`Harry Potter and the Half Blood Prince`, 	`Shrek 2`, 	`Pulp Fiction`, 	`Forrest Gump`, 	`Transformers 3 Dark of the Moon`, 	`The Good, the Bad, and the Ugly`, 	`Avatar`, 	`Silence of the Lambs`, 	`Se7en`, 	`The Lion King`, 	`Once Upon a Time in the West`, 	`The Matrix`, 	`The Dark Knight Rises (Batman)`, 	`City of God`, 	`The Godfather`, 	`Harry Potter and the Philosopher's Stone`, 	`Iron Man 3`, 	`Skyfall`, 	`Casablanca`, 	`Lord of the Rings: Return of the King`, 	`Shawshank Redemption`, 	`Goodfellas`, 	`The Godfather 2`, 	`Star Wars: A New Hope`, 	`Pirates Of The Caribbean: At World's End`, 	`Inception`, 	`The Usual Suspects`, 	`Indiana Jones: Raiders of the Lost Ark`, 	`The Avengers`, 	`Pirates of the Caribbean: Dead Man's Chest`, 	`Lord of the Rings: The Two Towers`, 	`Titanic`, 	`Fight Club`, 	`Finding Nemo`, 	`Harry Potter and the Deathly Hallows: Part 2`, 	`Star Wars: The Phantom Menace`, 	`Harry Potter and the Deathly Hallows: Part 1`, 	`Lord of the Rings: Fellowship of the Ring`, 	`Toy Story 3`, 	`The Dark Knight`, 	`One Flew Over the Cuckoo's Nest`, 	`The Hobbit, part 1`, 	`Star Wars: The Empire Strikes Back`, 	`Pirates of the Caribbean: On Stranger Tides`, 	`12 Angry Men`, 	`Jurassic Park`]
    }
  }
}
</script>

<style>

.fade-enter-active {
  transition: opacity 1s
}
.fade-leave-active {
  transition: opacity .05s
}
.fade-enter, .fade-leave-to /* .fade-leave-active in <2.1.8 */ {
  opacity: 0
}

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
