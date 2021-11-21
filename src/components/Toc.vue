<template>
  <div>
    <div
      :class="`${cn}__item`"
      v-for="(item, index) in list"
      :key="index"
      @click="handleClick(item.el)"
    >
      <span :class="`${cn}__item--${item.tag}`">{{ item.text }}</span>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent, onMounted, PropType, ref } from "vue";

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
    const list = ref<any[]>([]);

    onMounted(() => {
      const selector = props.container ? `.${props.container}>*` : "*";
      const items = document.querySelectorAll(selector);

      items.forEach((item) => {
        const nodeName = item.nodeName.toLowerCase();

        if (props.level.includes(nodeName)) {
          list.value.push({
            el: item,
            text: item.innerHTML,
            offset: (item as any).offsetTop,
            tag: item.nodeName.toLowerCase(),
          });
        }
      });
    });

    const handleClick = (el: Element) => {
      el.scrollIntoView({ behavior: "smooth", block: "center" });
    };

    return {
      cn: COMPONENT_NAME,
      list,
      handleClick,
    };
  },
});
</script>

<style>
.Toc__item {
  cursor: pointer;
  font-size: 20px;
  line-height: 2.5rem;
}

.Toc__item:hover {
  color: blue;
}

.Toc__item--h1 {
  font-weight: 700;
  font-size: 1.5rem;
}

.Toc__item--h2 {
  font-weight: 500;
  padding-left: 0.5rem;
}

.Toc__item--h3 {
  padding-left: 1rem;
}

.Toc__item--h4 {
  padding-left: 1.5rem;
}

.Toc__item--h5 {
}

.Toc__item--h6 {
}
</style>
