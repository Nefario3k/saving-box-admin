<template>
  <div
    :style="`background-color: ${color}; top: ${top}px; right: ${right}px;z-index: ${index}; border-bottom-color: ${borderColor}`"
    :class="{ absolute: absolute, borderstyled: border, fixed: fixed }"
    class="statusWrapper"
  >
    <svg
      v-if="svg"
      width="40"
      height="40"
      viewBox="0 0 40 40"
      fill="none"
      xmlns="http://www.w3.org/2000/svg"
    >
      <g clip-path="url(#clip0_1805_91778)">
        <path
          fill-rule="evenodd"
          clip-rule="evenodd"
          d="M0.0925903 19.9992C0.0925903 9.00465 9.00544 0.0917969 20 0.0917969C30.9946 0.0917969 39.9074 9.00465 39.9074 19.9992C39.9074 30.9938 30.9946 39.9066 20 39.9066C9.00544 39.9066 0.0925903 30.9938 0.0925903 19.9992Z"
          :fill="svgColor"
        />
        <path
          fill-rule="evenodd"
          clip-rule="evenodd"
          d="M28.3894 14.3873C28.9318 14.9296 28.9318 15.8091 28.3894 16.3514L19.8224 24.9186C18.5568 26.1842 16.5048 26.1842 15.2393 24.9186L11.6105 21.2897C11.0681 20.7473 11.0681 19.8679 11.6105 19.3255C12.1529 18.7831 13.0323 18.7831 13.5747 19.3255L17.2035 22.9544C17.3843 23.1351 17.6774 23.1351 17.8581 22.9544L26.4254 14.3873C26.9678 13.8449 27.847 13.8449 28.3894 14.3873Z"
          :fill="svgStroke"
        />
      </g>
      <defs>
        <clipPath id="clip0_1805_91778">
          <rect width="40" height="40" fill="white" />
        </clipPath>
      </defs>
    </svg>
    <div class="status__text">
      <p v-if="headerColor" :style="`color: ${headerColor}`">{{ header }}</p>
      <span v-if="subtext" :style="`color: ${subtextColor}`">{{
        subtext
      }}</span>
    </div>
  </div>
</template>

<script>
export default {
  props: [
    "absolute",
    "right",
    "top",
    "color",
    "header",
    "headerColor",
    "subtext",
    "subtextColor",
    "svg",
    "svgStroke",
    "svgColor",
    "index",
    "border",
    "borderColor",
    "fixed",
  ],
};
</script>

<style lang="scss" scoped>
</style>