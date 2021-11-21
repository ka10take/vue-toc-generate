<template>
  <div>
    <div v-for="(item, index) in list" :key="index">
      {{ item.innerHTML }}
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent, onMounted, PropType, ref } from "vue";

// TODO: levelのタイプを記載
type TocLevel = "h1" | "h2" | "h3" | "h4" | "h5" | "h6";

const COMPONENT_NAME = "Toc";

export default defineComponent({
  name: COMPONENT_NAME,

  props: {
    level: {
      type: Array as PropType<string[]>,
      default: ["h1", "h2", "h3", "h4"],
      required: false,
    },
    container: {
      type: String as PropType<string>,
      default: "",
      required: false,
    },
  },

  setup(props) {
    const list = ref<Element[]>([]);

    onMounted(() => {
      const selector = props.container ? `.${props.container}>*` : "*";
      const listItems = document.querySelectorAll(selector);

      listItems.forEach((item) => {
        const nodeName = item.nodeName.toLowerCase();

        if (props.level.includes(nodeName)) {
          list.value.push(item);
        }
      });
    });

    return {
      cn: COMPONENT_NAME,
      list,
    };
  },
});
</script>
