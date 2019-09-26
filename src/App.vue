<template>
  <div id="app" class="container">
    <div>
        <b-card v-for="indice in nombres"
          :title="indice"
          img-src="https://picsum.photos/600/300/?image=25"
          img-alt="Image"
          img-top
          tag="article"
          style="max-width: 20rem;"
          class="mb-2"
        >
          <b-card-text>
            Some quick example text to build on the card title and make up the bulk of the card's content.
          </b-card-text>

          <b-button href="#" variant="primary">Go somewhere</b-button>
        </b-card>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'app',
  components: {
    HelloWorld
  },

  data() {
    return {
      personajes: [],
      nombres: [],
      url: "https://ddragon.leagueoflegends.com/cdn/6.24.1/data/en_US/champion.json"
    }
  },

  created() {
    this.peticionAPI()
  },

  methods: {
    peticionAPI() {
      axios.get(this.url).then(response => {
        this.nombres = Object.keys(response.data.data)
        console.log(this.nombres)
        this.personajes = response.data
      })
      .catch(error => {
        console.log(error)
      })
    }
  }
}
</script>

