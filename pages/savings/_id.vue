<template>
  <div>
    <v-row class="row__content">
      <div class="col-12">
        <v-card color="#fff" class="profile__card not__profile__card">
          <header>
            <span>Autobox Savings <span class="value">(4)</span></span>
          </header>
          <v-divider style="margin: 0 -33px 10px 0"></v-divider>

          <div class="row m-0 mb-5">
            <!-- cards   -->
            <div
              class="col-6 col-lg-3 col-xl-3 card__container savings"
              v-for="(items, index) in cardDetails"
              :key="index"
            >
              <DashboardCard :card="items" />
            </div>
          </div>

          <div style="width: 100%; max-width: 59.8rem">
            <v-tabs
              center-active
              :show-arrows="true"
              v-model="savingsTab"
              grow
              background-color="transparent"
              color="basil"
              :hide-slider="true"
              class="v-tabs-styles"
            >
              <v-tab :ripple="false"> Active</v-tab>
              <v-tab :ripple="false">Completed </v-tab>
              <v-tab :ripple="false"> Liquidated </v-tab>
              <v-tab :ripple="false"> Abandoned </v-tab>
            </v-tabs>
          </div>

          <SearchArea placeholder="Search by Plan Name, and duration" />
          <v-tabs-items v-model="savingsTab" class="profile__card-tabItems">
            <v-tab-item v-for="n in 4" :key="n">
              <TablesSingleSaving />
            </v-tab-item>
          </v-tabs-items>
        </v-card>
      </div>
    </v-row>
    <CreateAdmin ref="createAdmin" />
    <CreateRole ref="createRole" />
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
          title: "Total Autobox Savings",
          value: "₦240,000,000",
          details: "",
          color: "var(--card-eight)",
        },
        {
          title: "Ongoing Savings",
          value: "24",
          details: "",
          color: "var(--card-nine)",
        },
        {
          title: "Completed Savings",
          value: "19",
          details: "",
          color: "var(--card-ten)",
        },
        {
          title: "Liquidated Savings",
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
        case "createAdmin":
          this.$refs.createAdmin.showPanel();
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
.v-tabs-bar .v-tab:not(.v-tab--active) {
  color: rgba(102, 107, 112, 1) !important;
  font-weight: 600 !important;
  font-size: 14px;
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
  font-size: 14px;
  text-transform: capitalize;
  margin: 3px 3px 2px 3px;
  transition: all 0.2s ease-in-out;
}
.v-tabs-styles .v-tabs-bar .v-tab {
  &::before {
    display: none;
  }
}
.v-tabs-styles {
  background: var(--tab-bg);
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
