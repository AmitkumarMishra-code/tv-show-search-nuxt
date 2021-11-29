<script lang="ts">
export default {
  layout: "default"
};
</script>
<script setup lang="ts">
import { ref } from "vue";
const searchText = ref("");

const myData = ref([]) as any;
async function searchForStuff() {
  const data = await fetch(`/api/server?search=${searchText.value}`);
  const json = await data.json();
  console.log("data.value", json);
  myData.value = json;
}

const clearSearch = () => {
  searchText.value = ''
  myData.value = []
}
</script>
<template>
  <div>
    <form class="form" @submit.prevent="searchForStuff">
      <input type="text" v-model="searchText" />
      <button>Search For TV Shows</button>
    </form>
    <div class="stuff">
      <div v-for="show in myData">
        <img :src="show.show?.image?.medium" alt="" />
      </div>
    </div>
    <div class="clear">
    <button @click="clearSearch">Clear</button>
    </div>
  </div>
</template>

<style>
.stuff {
  margin: 50px;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-wrap: wrap;
  gap: 10px;
}

.stuff img{
  border-radius: 12px;
  border: 1px solid rgba(128, 128, 128, 0.25);
  box-shadow: 5px 5px 5px rgba(128, 128, 128, 0.25);
}

.form {
  display: flex;
  justify-content: center;
  align-items: center;
  margin-top: 10px;
}

.clear{
  width: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>
