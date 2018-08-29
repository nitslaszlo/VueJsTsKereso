<template>
  <div id="app">
    <h1>Kereső</h1>
    <!-- filterek -->
    <div id="filters">
        <input type="text" id="nameFilter" v-model="nameFilter">
    </div>

    <!-- találatok -->
    <ol id="resultList">
        <li v-for="resultItem in GetResults()" v-bind:key="resultItem">
               {{ resultItem }}
        </li>
    </ol>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";

@Component
export default class App extends Vue {
  nameFilter: string = "";
  list: string[] = [];

  private GetResults(): string[] {
    return this.list.filter(item => {
      if (this.nameFilter == "") return true; // ha nincs filter, akkor minden megjelenik
      // pozíció megállapítása
      let position = item.toLowerCase().indexOf(this.nameFilter.toLowerCase());
      return position != -1;
    });
  }

  private created(): void {
    this.list = [
      "Get Out",
      "Dunkirk",
      "Lady Bird",
      "Blade Runner 2049",
      "A Ghost Story",
      "The Florida Project",
      "Phantom Thread",
      "Call Me By Your Name",
      "Raw",
      "The Shape of Water",
      "Okja",
      "Personal Shopper",
      "It Comes at Night",
      "Good Time",
      "Star Wars: The Last Jedi"
    ];
  }
}
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
}
</style>
