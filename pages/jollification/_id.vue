<template>
  <div>
    <v-row class="row__content">
      <div class="col-12">
        <v-card color="#fff" class="profile__card not__profile__card">
          <header>
            <span>December Jolly Items <span class="value">(6)</span></span>
          </header>
          <v-divider style="margin: 0 -33px 10px 0"></v-divider>
          <div style="width: 100%; max-width: 37.8rem">
            <v-tabs
              v-model="savingsTab"
              grow
              background-color="transparent"
              color="basil"
              :hide-slider="true"
              class="v-tabs-styles"
            >
              <v-tab :ripple="false"> Active</v-tab>
              <v-tab :ripple="false"> Completed</v-tab>
              <v-tab :ripple="false"> History</v-tab>
            </v-tabs>
          </div>

          <SearchArea
            class="mt-5"
            placeholder="Search by Plan Name, and duration"
          />
          <v-tabs-items v-model="savingsTab" class="profile__card-tabItems">
            <v-tab-item v-for="n in 3" :key="n">
              <TablesSingleJolly />
            </v-tab-item>
          </v-tabs-items>
        </v-card>
      </div>
    </v-row>
    <CreateJolly
      @continueStep="showPanel('createJollyContinue')"
      ref="createJolly"
    />
    <CreateJollyContd
      @showAddJolly="showPanel('addJolly')"
      ref="createJollyContinue"
    />
    <CreateJollyItem
      @continueItemStep="showPanel('createJollyContinue')"
      ref="addJolly"
    />
    <CreateRole ref="createRole" />
  </div>
</template>

<script>
export default {
  data() {
    return {
      cardDetails: [
        {
          title: "Total Jolly Amount",
          value: "₦240,000,000",
          details: "",
          color: "var(--card-eight)",
        },
        {
          title: "Total Active Jollification ",
          value: "24",
          details: "",
          color: "var(--card-nine)",
        },
        {
          title: "Completed Jollification",
          value: "19",
          details: "",
          color: "var(--card-ten)",
        },
        {
          title: "Relinquished Jolly",
          value: "09",
          details: "",
          color: "var(--card-alt-one)",
        },
      ],
      savingsTab: false,
    };
  },
  methods: {
    showPanel(type) {
      switch (type) {
        case "createJolly":
          this.$refs.createJolly.showPanel();
          break;
        case "createJollyContinue":
          this.$refs.createJollyContinue.showPanel();
          break;
        case "createRole":
          this.$refs.createRole.showPanel();
          break;
        case "addJolly":
          this.$refs.addJolly.showPanel();
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
