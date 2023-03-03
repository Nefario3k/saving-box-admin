<template>
  <div style="position: relative">
    <!-- <v-overlay
      z-index="99"
      :opacity="0.4"
      :value="showDrawer"
      @click="closeDrawer()"
    ></v-overlay> -->
    <v-navigation-drawer
      style="z-index: 100"
      v-model="showDrawer"
      :right="true"
      :width="width"
      temporary
      fixed
      class="adminPanel"
    >
      <v-app-bar
        style="margin-left: 1px"
        color="#fff"
        :elevation="elevation"
        fixed
        :height="50"
      >
        <div class="text-right">
          <svg
            @click="closeDrawer()"
            width="30"
            height="30"
            viewBox="0 0 30 30"
            fill="none"
            xmlns="http://www.w3.org/2000/svg"
          >
            <path
              d="M22.5 7.5L7.5 22.5"
              stroke="#FF0000"
              stroke-width="1.5"
              stroke-linecap="round"
              stroke-linejoin="round"
            />
            <path
              d="M7.5 7.5L22.5 22.5"
              stroke="#FF0000"
              stroke-width="1.5"
              stroke-linecap="round"
              stroke-linejoin="round"
            />
          </svg>
        </div>
      </v-app-bar>

      <div
        ref="myDiv"
        class="mt-2 right-drawer-container"
        @scroll="handleScroll"
      >
        <div>
          <div class="right-drawer-title">
            <div class="headerD">
              <h1 class="">Birth Certificate.pdf</h1>
              <svg
                title="Download"
                width="22"
                height="20"
                viewBox="0 0 22 20"
                fill="none"
                xmlns="http://www.w3.org/2000/svg"
              >
                <path
                  d="M11.85 11.7339L11.8508 1.75001C11.8508 1.28077 11.47 0.9 11.0008 0.9C10.5316 0.9 10.1508 1.28077 10.1508 1.74999L10.15 11.7338L8.68675 10.2635L11.85 11.7339ZM11.85 11.7339L13.3148 10.2635L11.85 11.7339ZM11.4275 14.4078C11.4048 14.4234 11.3818 14.4376 11.358 14.4506M11.4275 14.4078L10.4698 14.32L10.4705 14.3212C10.4957 14.3464 10.5227 14.3698 10.5512 14.3913M11.4275 14.4078C11.4328 14.4041 11.4382 14.4003 11.4434 14.3964L11.4275 14.4078ZM11.358 14.4506C11.3465 14.4568 11.3344 14.463 11.3222 14.4687C11.3004 14.4791 11.278 14.4885 11.2551 14.4967C11.2436 14.5008 11.2321 14.5046 11.2206 14.5081M11.358 14.4506L11.4057 14.5384C11.4057 14.5384 11.4058 14.5384 11.4058 14.5384M11.358 14.4506L11.25 14.6037M11.2206 14.5081C11.1924 14.5169 11.1635 14.5239 11.1339 14.5292L11.1151 14.5323M11.2206 14.5081L11.2498 14.6038C11.2499 14.6037 11.25 14.6037 11.25 14.6037M11.2206 14.5081L11.2502 14.6037L11.25 14.6037M11.1151 14.5323C11.0912 14.536 11.0663 14.5386 11.0411 14.5399C11.0288 14.5406 11.0167 14.5409 11.0046 14.541L11.0008 14.641M11.1151 14.5323L11.1306 14.6311C11.1032 14.6354 11.0749 14.6383 11.0464 14.6398L11.0463 14.6398C11.0311 14.6406 11.016 14.641 11.0008 14.641M11.1151 14.5323L10.8508 14.6277M11.0008 14.641C10.9983 14.641 10.9958 14.641 10.9933 14.641M11.0008 14.641H10.9933L10.9933 14.641M10.9933 14.641L10.9933 14.6407L10.9932 14.6407L10.9548 14.6378L10.9535 14.6377L10.8929 14.634L10.8902 14.6338M10.9933 14.641C10.9587 14.6407 10.9242 14.6382 10.8902 14.6338M10.8902 14.6338C10.8887 14.6336 10.8872 14.6334 10.8856 14.6332C10.8806 14.6325 10.8756 14.6318 10.8707 14.631M10.8902 14.6338L10.8856 14.6335L10.8856 14.6332L10.8707 14.6311L10.8707 14.631M10.8707 14.631L10.8821 14.5316C10.8775 14.5308 10.8729 14.5301 10.8683 14.5292M10.8707 14.631C10.864 14.63 10.8574 14.6289 10.8508 14.6277M10.8683 14.5292C10.8382 14.5239 10.8093 14.5169 10.7811 14.5083C10.7699 14.5047 10.7588 14.5011 10.7478 14.4971M10.8683 14.5292L10.8507 14.6277C10.8507 14.6277 10.8508 14.6277 10.8508 14.6277M10.8683 14.5292L10.8509 14.6277L10.7143 14.5913M10.7478 14.4971C10.7249 14.489 10.7022 14.4796 10.6801 14.4691M10.7478 14.4971L10.7142 14.5913C10.7142 14.5913 10.7142 14.5913 10.7143 14.5913M10.7478 14.4971L10.7144 14.5914L10.6372 14.5594M10.6801 14.4691C10.6666 14.4627 10.6533 14.4559 10.6401 14.4487C10.6217 14.4385 10.6039 14.4277 10.5866 14.4162M10.6801 14.4691L10.6372 14.5594C10.6372 14.5594 10.6372 14.5594 10.6372 14.5594M10.6801 14.4691L10.6372 14.5594M10.5866 14.4162C10.5747 14.4084 10.5629 14.4 10.5512 14.3913M10.5866 14.4162L10.5312 14.4995C10.5313 14.4996 10.5314 14.4996 10.5315 14.4997L10.5866 14.4162ZM10.5512 14.3913L10.4912 14.4712C10.4912 14.4712 10.4911 14.4712 10.4911 14.4712C10.4588 14.4469 10.4283 14.4204 10.3998 14.392L10.3911 14.3832L10.3903 14.3819M10.5512 14.3913L10.3903 14.3819M10.3903 14.3819L7.48296 11.4636L7.48285 11.4635C7.15206 11.1304 7.15306 10.5922 7.48521 10.2612L7.48533 10.261C7.81821 9.93043 8.35547 9.93006 8.68668 10.2635L10.3903 14.3819ZM10.6372 14.5594C10.6622 14.5713 10.688 14.582 10.7143 14.5913M10.7143 14.5913C10.7267 14.5958 10.7389 14.5998 10.7511 14.6037L10.7519 14.6039C10.7838 14.6137 10.8167 14.6217 10.8508 14.6277M11.25 14.6037C11.2631 14.5997 11.2758 14.5955 11.2883 14.591L11.289 14.5908C11.315 14.5814 11.3403 14.5709 11.3651 14.5591C11.3789 14.5525 11.3926 14.5456 11.4058 14.5384M11.4058 14.5384C11.4328 14.5237 11.4588 14.5077 11.4843 14.4901L11.4845 14.4899C11.4934 14.4838 11.5021 14.4775 11.5107 14.471M11.4058 14.5384L11.5107 14.471M11.5107 14.471C11.546 14.4445 11.5791 14.4153 11.6098 14.3838C11.61 14.3836 11.6101 14.3835 11.6102 14.3834L14.5186 11.4636L14.5188 11.4635C14.8495 11.1304 14.8485 10.5922 14.5164 10.2612L14.5163 10.261C14.1834 9.93044 13.6462 9.93006 13.315 10.2634L11.5107 14.471ZM7.217 6.4825C7.217 6.01327 6.83623 5.6325 6.367 5.6325H5.426C2.92982 5.6325 0.9 7.66123 0.9 10.1565V15.0415C0.9 17.5427 2.93479 19.5765 5.435 19.5765H16.575C19.0692 19.5765 21.1 17.5467 21.1 15.0515V10.1675C21.1 7.6673 19.0663 5.6325 16.566 5.6325H15.634C15.1648 5.6325 14.784 6.01327 14.784 6.4825C14.784 6.95173 15.1648 7.3325 15.634 7.3325H16.566C18.1278 7.3325 19.4 8.60373 19.4 10.1675V15.0515C19.4 16.6083 18.1318 17.8765 16.575 17.8765H5.435C3.87123 17.8765 2.6 16.6053 2.6 15.0415V10.1565C2.6 8.59879 3.86716 7.3325 5.426 7.3325H6.367C6.83623 7.3325 7.217 6.95173 7.217 6.4825Z"
                  fill="#666B70"
                  stroke="#333940"
                  stroke-width="0.2"
                />
              </svg>
            </div>
            <p>2 Pages . 256KB</p>
          </div>
        </div>
        <!-- <div class="pdfContainer"> -->
        <object
          height="90%"
          width="100%"
          type="application/pdf"
          class="pdfContainer__object"
          :data="pdfUrl"
          align="top"
          name="User Verification"
          title="Birth Certificate"
        >
          <p>
            Your web browser doesn't have a PDF plugin. Instead you can
            <a download :href="pdfUrl">click here to download the PDF file.</a>
          </p>
        </object>
        <!-- </div> -->
      </div>
    </v-navigation-drawer>
  </div>
</template>

<script>
export default {
  props: ["pdfUrl"],
  data() {
    return {
      showDrawer: false,
      elevation: 0,
      width: 512,
      jollificationsTab: null,
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
      this.showDrawer = false;
    },
    showPanel() {
      this.showDrawer = true;
    },
    handleScroll() {
      const myDiv = this.$refs.myDiv;
      const heightScrolled = myDiv.scrollTop;
      // const initialHeight = myDiv.scrollHeight;
      if (heightScrolled > 0) {
        this.elevation = 2;
      } else {
        this.elevation = 0;
      }
    },
    showApproval() {
      this.showDrawer = false;
      this.$emit("showApproval");
    },
    showReject() {
      this.showDrawer = false;
      this.$emit("showReject");
    },
  },
};
</script>

<style lang="scss" scoped>
.text-right {
  width: 100%;
  display: flex;
  justify-content: flex-end;
}
.v-tabs-bar .v-tab:not(.v-tab--active) {
  color: var(--label-second-color) !important;
  font-weight: 600 !important;
  font-size: 14px !important;
  text-transform: capitalize;
  margin: 3px 3px 2px 3px;
  transition: all 0.2s ease-in-out;
}
.v-tabs-bar .v-tab {
  &::before {
    display: none;
  }
}

.v-tab--active {
  transition: all 0.2s ease-in-out;
  background-color: #ffffff;
  margin: 3px 3px 2px 3px;
  border-radius: 4px;
  font-weight: 600;
  font-size: 14px;
  color: var(--primary-color) !important;
  text-transform: capitalize;
}

.headerD {
  display: flex;
  align-items: center;
  justify-content: space-between;
  grid-gap: 10px;
  svg {
    cursor: pointer;
    &:hover {
      path {
        stroke: red;
        fill: red;
      }
    }
  }
}
</style>
