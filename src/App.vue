<template>
  <div id="app" class="container">
    <div>
      <b-card
        v-for="indice in personajes"
        :key="indice.name"
        :title="indice.name"
        :img-src="
          `http://ddragon.leagueoflegends.com/cdn/6.24.1/img/champion/${indice.image.full}`
        "
        img-alt="Image"
        img-top
        tag="article"
        style="max-width: 20rem;"
        class="mb-2"
      >
        <b-card-text>
          <b>{{ indice.title }}:</b>
          {{ indice.blurb }}
        </b-card-text>

        <b-button href="#" variant="primary">Go somewhere</b-button>
      </b-card>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "app",
  data() {
    return {
      personajes: [],
      nombres: [],
      url:
        "https://ddragon.leagueoflegends.com/cdn/6.24.1/data/en_US/champion.json"
    };
  },

  created() {
    this.peticionAPI();
  },

  methods: {
    peticionAPI() {
      axios
        .get(this.url)
        .then(response => {
          this.nombres = Object.keys(response.data.data);
          this.personajes = response.data.data;
        })
        .catch(error => {
          // eslint-disable-next-line no-console
          console.log(error);
        });
    }
  }
};
</script>
