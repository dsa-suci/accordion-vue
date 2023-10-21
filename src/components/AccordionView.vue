<template>
  <div class="flex justify-center items-center">
    <AccordionComponent
      label="Device"
      :aria-expanded="open ? true : false"
      :classSvg="open ? 'w-3 h-3 shrink-0' : 'w-3 h-3 rotate-180 shrink-0'"
      @onClick="openList"
      :addClass="open ? 'relative' : 'hidden'"
      :dataSelect="list"
      name="device"
      v-model:value="listSelect"
      @handleChange="handleChange"
    />
  </div>
</template>
<script>
import { ref } from "vue";
import AccordionComponent from "./AccordionComponent.vue";

export default {
  components: {
    AccordionComponent,
  },
  setup() {
    const open = ref(false);
    const list = ref([
      {
        id: "1",
        label: "device 1",
      },
      {
        id: "2",
        label: "device 2",
      },
      {
        id: "3",
        label: "device 3",
      },
      {
        id: "4",
        label: "device 4",
      },
    ]);

    const listSelect = ref("1");

    const openList = () => {
      open.value = !open.value;
    };

    const handleChange = (item) => {
      listSelect.value = item;
      console.log("select", listSelect.value);
    };

    return {
      open,
      list,
      listSelect,
      openList,
      handleChange,
    };
  },
};
</script>
