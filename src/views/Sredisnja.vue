<template>
  <div class="container" style="max-width: 500px;">
    <div id="cards">
      <dogadaji-card v-for="card in cards" :key="card.naslov" :info="card" />
      <!-- :key mora svugdje biti drugaciji tj imati nesta jedinstveno iz polja poput naslova-->
      <!-- kada stavimo : onda ovaj = prima js  ako stavim samo info prenjet ce se string -->
    </div>
    <footer id="footer"></footer>
  </div>
</template>

<script>
import DogadajiCard from "@/components/DogadajiCard.vue";
import { db } from "@/firebase";

/*let cards = [];

cards = [
  {
    img: require('@/assets/vidi-pivo.png'),
    naslov: 'Izložba VIDI, PIVO!/LOOK, BEER!',
    heart: false,
  },
  {
    img: require('@/assets/kazaliste.jpg'),
    naslov: 'Natjecanje amaterskih kazališta',
    heart: false,
  },
]; */

export default {
  name: "Sredisnja",
  data: function() {
    return {
      cards: []
    };
  },
  components: {
    DogadajiCard
  },
  mounted() {
    this.getPosts();
  },
  methods: {
    getPosts() {
      console.log("Firebase dohvat..");

      db.collection("posts")
        .get()
        .then(query => {
          query.forEach(doc => {
            const data = doc.data();

            if (data.region == "Central Croatia") {
              this.cards.push({
                id: doc.id,
                img: data.url,
                naslov: data.name,
                heart: false
              });
              if ("Central Croatia" == null) {
                console.log("Sorry,there are no events available yet ... ");
              }
            }
          });
        });
    }
  }
};
</script>
<style scoped>
#footer {
  width: 100%;
  height: 80px;
}
#cards {
  max-width: 100%;
  align-content: center;
}
</style>
