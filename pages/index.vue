<template>
  <div class="pageWrap">
    <div class="tracker">
      <MainComponentsTracker />
    </div>
    <div class="dailyWork">
      <MainComponentsDailyWork />
    </div>
    <div class="progress"><MainComponentsProgress /></div>
    <div class="highlights"><MainComponentsHighlights /></div>
    <div class="class"><MainComponentsClass /></div>
    <div class="feedback"><MainComponentsFeedback /></div>
  </div>
</template>

<script setup></script>

<style lang="scss" scoped>
.pageWrap {
  max-height: calc(100% - 64px);
  overflow: auto;
  display: grid;
  gap: 24px;
  padding: 32px;
  grid-template-columns: 1fr 1fr 1fr;
  //grid-template-rows: 1fr 1fr 1fr;
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
}
.progress {
  grid-area: progress;
}
.highlights {
  grid-area: highlights;
}
.class {
  grid-area: class;
}
.feedback {
  grid-area: feedback;
}
</style>
