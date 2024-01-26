<template>
  <div class="pageWrap">
    <div class="tracker">
      <MainComponentsTracker />
    </div>
    <div class="dailyWork">teste2</div>
    <div class="progress">teste3</div>
    <div class="highlights">teste4</div>
    <div class="class">teste5</div>
    <div class="feedback">teste6</div>
  </div>
</template>

<script setup></script>

<style lang="scss" scoped>
.pageWrap {
  height: calc(100% - 64px);
  display: grid;
  gap: 24px;
  padding: 32px;
  grid-template-columns: 1fr 1fr 1fr;
  grid-template-rows: 1fr 1fr 1fr;
  grid-template-areas:
    "tracker dailyWork highlights"
    "tracker progress highlights"
    "class class feedback";
}

@media screen and (max-width: 768px) {
  .pageWrap {
    height: 100%;
    display: grid;
    gap: 14px;
    grid-template-areas:
      "tracker highlights"
      "tracker highlights"
      "dailyWork feedback"
      "progress feedback"
      "class class ";
  }
}

.tracker {
  grid-area: tracker;
}
.dailyWork {
  grid-area: dailyWork;
  background-color: green;
}
.progress {
  grid-area: progress;
  background-color: blue;
}
.highlights {
  grid-area: highlights;
  background-color: violet;
}
.class {
  grid-area: class;
  background-color: black;
}
.feedback {
  grid-area: feedback;
  background-color: yellow;
}
</style>
