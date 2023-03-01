<template>
  <div>
    <v-row class="row__content">
      <div class="col-12">
        <v-card color="#fff" class="profile__card not__profile__card">
          <header>
            <span>Investibox <span class="value">(3)</span></span>
            <v-btn
              @click="showPanel('createInvestment')"
              class="Btn"
              color="var(--primary-color)"
              ><span>Create Investment</span></v-btn
            >
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

          <SearchArea placeholder="Search by Title Name, and Category" />
          <TablesInvestiboxPage />
        </v-card>
      </div>
    </v-row>
    <CreateInvestibox
      @continueStep="showPanel('createInvestmentContinue')"
      ref="createInvestment"
    />
    <CreateInvestiboxContd ref="createInvestmentContinue" />
    <CreateRole ref="createRole" />
  </div>
</template>

<script>
export default {
  data() {
    return {
      cardDetails: [
        {
          title: "Total Investibox",
          value: "₦240,000,000",
          details: "",
          color: "var(--card-eight)",
        },
        {
          title: "Total Active Investibox ",
          value: "24",
          details: "",
          color: "var(--card-nine)",
        },
        {
          title: "Completed Investibox",
          value: "19",
          details: "",
          color: "var(--card-ten)",
        },
        {
          title: "Sold Off Investment",
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
        case "createInvestment":
          this.$refs.createInvestment.showPanel();
          break;
        case "createInvestmentContinue":
          this.$refs.createInvestmentContinue.showPanel();
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
