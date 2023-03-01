<template>
  <div>
    <v-row class="row__content">
      <div class="col-12">
        <v-card color="#fff" class="profile__card not__profile__card">
          <header>
            <span
              >Poultry Farming Wuye <span class="value">(4)</span
              ><span class="subHead">Thrive Agric, Gwarimpa Abuja</span></span
            >
          </header>
          <v-divider style="margin: 0 -33px 10px 0"></v-divider>
          <div class="titlePageTab">
            <p>Users/Investors</p>
          </div>
          <div style="width: 100%; max-width: 54.8rem">
            <v-tabs
              center-active
              show-arrows=""
              v-model="savingsTab"
              grow
              background-color="transparent"
              color="basil"
              :hide-slider="true"
              class="v-tabs-styles"
            >
              <v-tab :ripple="false"> Active</v-tab>
              <v-tab :ripple="false"> Completed</v-tab>
              <v-tab :ripple="false"> Marketplace</v-tab>
              <v-tab :ripple="false"> Transaction</v-tab>
            </v-tabs>
          </div>

          <SearchArea
            class="mt-5 pt-2"
            placeholder="Search by Plan Name, and duration"
          />
          <v-tabs-items v-model="savingsTab" class="profile__card-tabItems">
            <v-tab-item>
              <TablesSingleInvestibox />
            </v-tab-item>
            <v-tab-item>
              <TablesSingleCompletedInvestibox />
            </v-tab-item>
            <v-tab-item>
              <TablesSingleMarketInvestibox />
            </v-tab-item>
            <v-tab-item>
              <TablesSingleInvestibox />
            </v-tab-item>
          </v-tabs-items>
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
      savingsTab: null,
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
