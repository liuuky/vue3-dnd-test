<script setup lang="ts">
import SourceBox from "./SourceBox.vue";
import SourceBox2 from "./SourceBox2.vue";
import TargetBox from "./TargetBox.vue";
</script>
<template>
  <div :style="{ overflow: 'hidden', clear: 'both', marginTop: '1.5rem' }">
    <div :style="{ float: 'left' }">
      <SourceBox show-copy-icon />
      <SourceBox2 />
    </div>
    <div :style="{ float: 'left' }">
      <TargetBox />
    </div>
  </div>
</template>
