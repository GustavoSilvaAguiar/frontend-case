<template>
  <div class="pageWrap">
    <div class="tracker">teste</div>
    <div class="dailyWork">teste2</div>
    <div class="progress">teste3</div>
    <div class="highlight">teste4</div>
    <div class="class">teste5</div>
    <div class="feedback">teste6</div>
  </div>
</template>

<script setup></script>

<style lang="scss" scoped>
.pageWrap {
  height: 100%;
  display: grid;
  gap: 24px;
  grid-template-areas:
    "tracker dailyWork highlight"
    "tracker progress highlight"
    "class class feedback";
}

.tracker {
  grid-area: "tracker";
  grid-row: tracker;
  background-color: red;
}
.dailyWork {
  grid-area: "dailyWork";
  background-color: green;
}
.progress {
  grid-area: "progress";
  background-color: blue;
}
.highlight {
  grid-area: "highlight";
  grid-row: highlight;
  background-color: violet;
}
.class {
  grid-area: "class";
  grid-column: class;
  background-color: black;
}
.feedback {
  grid-area: "feedback";
  background-color: yellow;
}
</style>
