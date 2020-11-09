<template>
  <div class="Timeline">
    <div class="Timeline__Inner">
      <div class="Timeline__CenterLine"></div>

      <TimelineEntry
        v-bind:entry="entry"
        v-bind:key="entry.id"
        v-for="entry in entries"
      />
    </div>
  </div>
</template>

<script>
import TimelineEntry from "./TimelineEntry";
export default {
  name: "Timeline",
  components: {
    TimelineEntry,
  },
  props: ["entries"],
};
</script>

<style scoped>
.Timeline {
  width: 100%;
  min-height: 200px;
  padding: 20px 15px;
  max-width: 1440px;
  margin: 0 auto;
}

.Timeline__Inner {
  width: 100%;
  position: relative;
}

.Timeline__CenterLine {
  background-color: rgb(11, 81, 132);
  width: 4px;
  position: absolute;
  top: 0;
  bottom: 0;
  left: 0;
  pointer-events: none;
}

@media screen and (min-width: 768px) {
  .Timeline__CenterLine {
    left: calc(50% - 2px);
  }
}

.Timeline__CenterLine::before,
.Timeline__CenterLine::after {
  content: "";
  display: block;
  position: absolute;
  width: 20px;
  height: 20px;
  border-radius: 50%;
  background-color: rgb(11, 81, 132);
  left: calc(50% - 10px);
  pointer-events: none;
}

.Timeline__CenterLine::before {
  top: 0;
}

.Timeline__CenterLine::after {
  bottom: 0;
}
</style>
