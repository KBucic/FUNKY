<template>
  <div id="cards">
    <a :href="info.route"><img class="card-img-top" :src="info.img"/></a>
    <div class="card-body">
      <p class="card-text">{{ info.naslov }}</p>
    </div>
  </div>
</template>

<script>
export default {
  props: ["info"],
  name: "RegijeCard"
};
</script>

<style scoped>
#cards {
  width: 100%;
  margin-bottom: 25px;
  margin-top: 17px;
  border-bottom: none;
  border-bottom-left-radius: 0%;
  border-bottom-right-radius: 0%;
  border-left: none;
  border-right: none;
  border-top: none;
  background-color: transparent;
  align-items: center;
}
.card-img-top {
  height: 150px;
  object-fit: cover;
  border-radius: 14%;
  /* zaobljenost rubova*/
}
.card-body {
  text-align: center;
  margin-top: -5px;
  margin-bottom: 5px;
}
.card-text {
  height: 1px;
  margin-bottom: 10px;
  font-size: 18px;
  margin-left: -10px;
  color: #d0d0d0;
}
</style>
