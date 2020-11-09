<template>
  <div class="Timeline__Entry">
    <img src="../assets/poll-solid.svg" class="Timeline__Symbol" />
    <span class="Timeline__Date">
      {{ entry.registered }}
    </span>
    <span class="Timeline__Description">
      {{ entry.about }}
    </span>
    <div class="Timeline__Line"></div>
  </div>
</template>

<script>
export default {
  name: "TimelineEntry",
  props: ["entry"],
};
</script>

<style scoped>
.Timeline__Entry {
  width: 100%;
  margin-right: auto;
  text-align: center;
  margin-bottom: 24px;
  padding: 0 40px;
  position: relative;
}

.Timeline__Entry::before {
  content: "";
  display: block;
  position: absolute;
  left: -8px;
  top: calc(50% - 20px + 24px);
  width: 10px;
  height: 10px;
  background-color: white;
  border: 5px solid rgb(11, 81, 132);
  border-radius: 50%;
}

.Timeline__Entry:nth-child(odd) {
  margin-right: 0;
  margin-left: auto;
}

.Timeline__Symbol {
  width: 40px;
  margin-bottom: 12px;
}

.Timeline__Date {
  display: block;
  font-weight: 700;
  margin-bottom: 12px;
}

.Timeline__Description {
  display: block;
  width: 100%;
  margin: auto;
}

@media screen and (min-width: 768px) {
  .Timeline__Entry {
    width: 50%;
    padding-left: 0;
  }

  .Timeline__Entry:nth-child(odd)::before {
    left: -10px;
  }

  .Timeline__Entry:nth-child(even)::before {
    left: unset;
    right: -10px;
  }

  .Timeline__Description {
    max-width: 50%;
  }
}

.Timeline__Line {
  display: none;
}

@media screen and (min-width: 1200px) {
  .Timeline__Entry:nth-child(even)::after,
  .Timeline__Entry:nth-child(odd)::after {
    content: "";
    display: block;
    width: 20px;
    height: 20px;
    border-radius: 50%;
    background-color: rgb(11, 81, 132);
    position: absolute;
    top: calc(50% - 20px + 24px);
    right: 100px;
  }

  .Timeline__Entry:nth-child(odd)::after {
    left: 100px;
    right: unset;
  }

  .Timeline__Line {
    display: block;
    height: 5px;
    position: absolute;
    background-color: rgb(11, 81, 132);
    right: 9px;
    left: calc(100% - 100px);
    top: calc(50% - 2.5px + 14px);
  }

  .Timeline__Entry:nth-child(odd) .Timeline__Line {
    left: 9px;
    right: calc(100% - 100px);
  }
}
</style>
