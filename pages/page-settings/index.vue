<template>
  <div>
    <v-row class="row__content">
      <!-- header  -->
      <div class="pb-0 col-12">
        <header class="topHeader">Page Settings</header>
      </div>

      <div class="pt-0 col-12">
        <v-card color="#fff" class="mt-2 profile__card not__profile__card">
          <div style="width: 100%; max-width: 41.8rem">
            <v-tabs
              center-active
              show-arrows
              v-model="savingsTab"
              grow
              background-color="transparent"
              color="basil"
              :hide-slider="true"
              class="v-tabs-styles"
            >
              <v-tab :ripple="false"> Top Users</v-tab>
              <v-tab :ripple="false">Testimonials </v-tab>
              <v-tab :ripple="false">Interest </v-tab>
            </v-tabs>
          </div>

          <v-divider style="margin: 0 -33px 10px 0"></v-divider>

          <v-tabs-items v-model="savingsTab" class="profile__card-tabItems">
            <!-- top user  -->
            <v-tab-item>
              <header class="cardHeader">
                <span
                  >User of the Month<span class="subHead"
                    >Set users of the month on home page</span
                  ></span
                >
                <v-btn
                  @click="$refs.createTopUsers.showPanel()"
                  color="var(--primary-color)"
                  class="Btn noMobileViewPage"
                >
                  <span>Add New User</span>
                </v-btn>
              </header>

              <SearchPageSettings placeholder="Search by Username or User ID" />
              <TablesTopUsers />
            </v-tab-item>
            <!-- testimonial  -->
            <v-tab-item>
              <header class="cardHeader">
                <span
                  >Testimonials<span class="subHead"
                    >Set users of the month on home page</span
                  ></span
                >
                <v-btn
                  @click="showPanel('createTestimonial')"
                  class="Btn"
                  color="var(--primary-color)"
                  ><span>Add Testimonial</span></v-btn
                >
              </header>
              <TablesTestimonial />
            </v-tab-item>
          </v-tabs-items>
        </v-card>
      </div>
    </v-row>
    <CreateTestimonial ref="createTestimonial" />
    <CreateTopUser ref="createTopUsers" />
  </div>
</template>

<script>
export default {
  data() {
    return {
      profileTab: null,
      savingsTab: null,
      paymentTab: null,
      cardDetails: [
        {
          title: "Total Loan Accessed",
          value: "₦240,000,000",
          details: "",
          color: "var(--card-eight)",
        },
        {
          title: "Total Active Loans",
          value: "24",
          details: "",
          color: "var(--card-nine)",
        },
        {
          title: "Completed Loans",
          value: "19",
          details: "",
          color: "var(--card-ten)",
        },
        {
          title: "Total Requested Loans",
          value: "09",
          details: "",
          color: "var(--card-alt-one)",
        },
      ],
    };
  },
  methods: {
    showPanel(type) {
      switch (type) {
        case "createTestimonial":
          this.$refs.createTestimonial.showPanel();
          break;
        case "createRole":
          this.$refs.createRole.showPanel();
          break;

        default:
          break;
      }
    },
  },
  // page properties go here
};
</script>

<style scoped lang="scss">
/* tab */
.cardHeader {
  font-size: 2rem !important;
}
.v-tabs-bar .v-tab:not(.v-tab--active) {
  color: rgba(102, 107, 112, 1) !important;
  font-weight: 600 !important;
  font-size: 14px !important;
  text-transform: capitalize;
}

.v-tab--active {
  background-color: #ffffff;
  border-radius: 4px;
  font-weight: 600;
  font-size: 14px;
  color: rgba(65, 105, 225, 1) !important;
  text-transform: capitalize;
}
.v-tabs-styles .v-tabs-bar .v-tab:not(.v-tab--active) {
  color: var(--label-second-color) !important;
  font-weight: 600 !important;
  font-size: 14px !important;
  text-transform: capitalize;
  margin: 3px 3px 2px 3px;
  transition: all 0.2s ease-in-out;
}
.v-tabs-styles .v-tabs-bar .v-tab {
  &::before {
    display: none;
  }
}

.v-tabs-styles .v-tab--active {
  transition: all 0.2s ease-in-out;
  background-color: #ffffff;
  margin: 3px 3px 2px 3px;
  border-radius: 4px;
  font-weight: 600;
  font-size: 14px;
  color: var(--primary-color) !important;
  text-transform: capitalize;
}
</style>
