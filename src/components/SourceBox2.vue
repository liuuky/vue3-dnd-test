<script lang="ts" setup>
import { useDrag } from "vue3-dnd";
import { ItemTypes } from "./ItemTypes";
import { toRefs } from "@vueuse/core";

const props = defineProps<{
  showCopyIcon?: boolean;
}>();

const [collect, drag] = useDrag(() => ({
  type: ItemTypes.BOX,
  options: {
    dropEffect: props.showCopyIcon ? "copy" : "move",
  },
  collect: (monitor) => ({
    opacity: monitor.isDragging() ? 0.4 : 1,
  }),
}));
const { opacity } = toRefs(collect);
</script>
<template>
  <div :ref="drag" class="source-box" :style="{ opacity }">
    <!-- When I am over a drop zone, I have {{ showCopyIcon ? 'copy' : 'no' }} icon. -->
    <el-alert title="success alert" type="success" />
    <el-alert title="info alert" type="info" />
    <el-alert title="warning alert" type="warning" />
    <el-alert title="error alert" type="error" />
  </div>
</template>
<style lang="less" scoped>
.source-box {
  padding: 14px;
  box-sizing: border-box;
  width: 388px;
  height: 192px;
  margin-bottom: 20px;
  background: #091620;
  border: 4px solid red;
  overflow: hidden;
}
.el-alert {
  margin: 20px 0 0;
}
.el-alert:first-child {
  margin: 0;
}
</style>
