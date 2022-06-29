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

const tableData = [
  {
    date: "2016-05-03",
    name: "Tom",
    address: "No. 189, Grove St, Los Angeles",
  },
  {
    date: "2016-05-02",
    name: "Tom",
    address: "No. 189, Grove St, Los Angeles",
  },
  {
    date: "2016-05-04",
    name: "Tom",
    address: "No. 189, Grove St, Los Angeles",
  },
  // {
  //   date: "2016-05-01",
  //   name: "Tom",
  //   address: "No. 189, Grove St, Los Angeles",
  // },
  // {
  //   date: "2016-05-08",
  //   name: "Tom",
  //   address: "No. 189, Grove St, Los Angeles",
  // },
  // {
  //   date: "2016-05-06",
  //   name: "Tom",
  //   address: "No. 189, Grove St, Los Angeles",
  // },
  // {
  //   date: "2016-05-07",
  //   name: "Tom",
  //   address: "No. 189, Grove St, Los Angeles",
  // },
];
</script>
<template>
  <div :ref="drag" class="source-box" :style="{ opacity }">
    <!-- When I am over a drop zone, I have {{ showCopyIcon ? 'copy' : 'no' }} icon. -->
    <el-table :data="tableData" height="160" style="width: 100%">
      <el-table-column prop="date" label="Date" width="118" />
      <el-table-column prop="name" label="Name" width="118" />
      <el-table-column prop="address" label="Address" width="118" />
    </el-table>
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
}
</style>
