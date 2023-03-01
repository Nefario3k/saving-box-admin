<template>
  <div style="position: relative">
    <v-overlay
      z-index="99"
      :opacity="0.4"
      :value="showDrawer"
      @click="closeDrawer()"
    ></v-overlay>
    <v-navigation-drawer
      style="z-index: 100"
      v-model="showDrawer"
      :right="true"
      :width="width"
      fixed
    >
      <!-- create auto savings form -->

      <div
        class="text-right"
        style="position: fixed; right: 20px; top: 20px; border-radius: 5px"
      >
        <img
          src="/images/icons/close.svg"
          alt=""
          class="close-right-drawer"
          @click="closeDrawer()"
        />
      </div>

      <div class="right-drawer-container">
        <slot></slot>
      </div>
    </v-navigation-drawer>
  </div>
</template>

<script lang="js">
export default {
  props: {
    showDrawer: {
      type: Boolean,
      // required: true
      default: false
    },

  },
  data() {
    return {
      width: 512,
    };
  },
  mounted() {
    var nx = window.innerWidth;
    if (nx <= 540) {
      this.width = "100vw";
    }
    window.addEventListener("resize", function (event) {
      var w = window.innerWidth;
      nx = w;
    });
    $(window).resize(() => {
      if (nx <= 540) {
        this.width = "100vw";
      } else {
        this.width = 512;
      }
    });
  },
  methods: {
    closeDrawer() {
      this.$emit('closeDrawer')
    }
  }
};
</script>

<style scoped>
/*  */
</style>
