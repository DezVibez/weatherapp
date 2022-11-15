<template>
  <div id="app">
    <div class="container">
      <ul>
        <li v-for="value in cityWeather" :key="value">

          <div>
            <b-card title="Card Title" img-src="https://picsum.photos/600/300/?image=25" img-alt="Image" img-top
              tag="article" style="max-width: 20rem;" class="mb-2">
              <b-card-text>
                {{ value.main }}
              </b-card-text>


            </b-card>
          </div>

        </li>
      </ul>
    </div>
  </div>
</template>

<script>
import axios from "axios"

export default {
  name: 'App',

  data() {
    return {
      city: "Milan",
      APIkey: "95b65f89ece539353a36f3e48cfc0c86",
      cityWeather: [],
    }
  },
  created() {
    this.getWeather()
  },
  methods: {
    getWeather() {
      axios.get(`https://api.openweathermap.org/data/2.5/weather?q=${this.city}&appid=${this.APIkey}&lang=it&units=metric`)
        .then(res => {
          console.log(res.data)
          this.cityWeather.push(res.data)
        })
    }
  },
}
</script>

<style lang="scss">
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: 'Quicksand', sans-serif;
  list-style-type: none;
}
</style>
