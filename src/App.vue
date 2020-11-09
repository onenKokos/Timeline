<template>
  <Timeline v-bind:entries="entries" />
</template>

<script>
import data from "./data/entries";
import Timeline from "./components/Timeline";

function sortDates(entryOne, entryTwo) {
  return new Date(entryOne.registered) - new Date(entryTwo.registered);
}

export default {
  name: "Timline",
  components: {
    Timeline,
  },
  data() {
    return {
      entries: data.sort(sortDates),
    };
  },
  created() {
    console.table(data);
  },
};
</script>

<style>
* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}

body {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: rgb(11, 81, 132);
}
</style>
