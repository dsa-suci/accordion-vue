<template>
  <div
    id="accordion-flush"
    data-accordion="collapse"
    data-active-classes="bg-white dark:bg-gray-900 text-gray-900 dark:text-white"
    data-inactive-classes="text-gray-500 dark:text-gray-400"
  >
    <h2
      id="accordion-flush-heading-1"
      class="text-gray-900 font-medium w-[330px]"
    >
      <button
        type="button"
        class="flex items-center justify-between w-full pb-3 font-medium text-left text-gray-500 border-b border-gray-200 dark:border-gray-700 dark:text-gray-400"
        data-accordion-target="#accordion-flush-body-1"
        :aria-expanded="ariaExtended"
        aria-controls="accordion-flush-body-1"
      >
        <span>{{ label }}</span>
        <svg
          data-accordion-icon
          :class="classSvg"
          xmlns="http://www.w3.org/2000/svg"
          fill="none"
          viewBox="0 0 10 6"
          @click="$emit('onClick')"
        >
          <path
            stroke="currentColor"
            stroke-linecap="round"
            stroke-linejoin="round"
            stroke-width="2"
            d="M9 5 5 1 1 5"
          />
        </svg>
      </button>
    </h2>
    <div
      id="accordion-flush-body-1"
      :class="addClass"
      aria-labelledby="accordion-flush-heading-1"
    >
      <div class="border-b border-gray-200 dark:border-gray-700 w-[330px]">
        <ul class="text-gray-900 font-medium">
          <li
            v-for="(item, index) in dataSelect"
            :key="item.id"
            class="py-1 cursor-pointer flex justify-between gap-3 items-center"
          >
            {{ item.label }}
            <input
              v-model="valueName"
              :id="item.id"
              :value="item.id"
              type="radio"
              :defaultChecked="index === 0 ? true : false"
              :name="name"
              @change="handleChange(item.id)"
              class="w-4 h-4 text-blue-600 bg-gray-100 border-gray-300 focus:ring-blue-500 dark:focus:ring-blue-600 dark:ring-offset-gray-800 focus:ring-2 dark:bg-gray-700 dark:border-gray-600"
            />
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
import { computed } from "vue";
export default {
  props: {
    ariaExtended: String,
    label: String,
    classSvg: String,
    addClass: String,
    dataSelect: Array,
    name: String,
    value: String,
    newClass: String,
  },
  setup(props, { emit }) {
    const valueName = computed({
      get() {
        return props.value;
      },
      set(value) {
        emit("update:value", value);
      },
    });

    const handleChange = (item) => {
      emit("handleChange", item);
    };

    return {
      valueName,
      handleChange,
    };
  },
};
</script>

<style></style>
