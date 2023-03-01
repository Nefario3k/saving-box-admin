<template>
  <div>
    <v-row class="row__content">
      <!-- header  -->
      <div class="col-12">
        <header class="topHeader">Dashboard</header>
        <span class="subHeader">Manage all finances</span>
      </div>

      <!-- cards   -->
      <div
        class="col-6 col-lg-3 col-xl-3 card__container"
        v-for="(items, index) in cardDetails"
        :key="index"
      >
        <DashboardCard :card="items" />
      </div>

      <!-- recent history -->
      <div class="col-12 col-md-6 col-lg-4 col-xl-4 list__col">
        <v-card class="listCard" flat color="#fff">
          <div>
            <div class="header">
              <h3>Recent Transactions</h3>
              <v-menu :nudge-bottom="3" offset-y>
                <template v-slot:activator="{ on, attrs }">
                  <v-btn
                    color="var(--border-color)"
                    outlined
                    class="Btn"
                    v-bind="attrs"
                    v-on="on"
                  >
                    <span>This Week</span>
                    <svg
                      width="20"
                      height="18"
                      viewBox="0 0 20 18"
                      fill="none"
                      xmlns="http://www.w3.org/2000/svg"
                    >
                      <path
                        d="M10 11.944L5 7.77734H15L10 11.944Z"
                        fill="#666B70"
                      />
                    </svg>
                  </v-btn>
                </template>
                <v-list class="dropdown__list">
                  <v-list-item class="dropdown__list-item">
                    <v-list-item-title class="dropdown__list-title"
                      >All</v-list-item-title
                    >
                  </v-list-item>
                  <v-list-item class="dropdown__list-item">
                    <v-list-item-title class="dropdown__list-title"
                      >Today</v-list-item-title
                    >
                  </v-list-item>
                  <v-list-item class="dropdown__list-item">
                    <v-list-item-title class="dropdown__list-title"
                      >This Week</v-list-item-title
                    >
                  </v-list-item>
                  <v-list-item class="dropdown__list-item">
                    <v-list-item-title class="dropdown__list-title"
                      >This Month</v-list-item-title
                    >
                  </v-list-item>
                </v-list>
              </v-menu>
            </div>
            <nuxt-link to="/loans" class="viewedAll">View All</nuxt-link>
            <ul>
              <li>
                <div class="listCard__content">
                  <span>Top up your savings plan</span>
                  <span>N1000</span>
                </div>
                <div class="listCard__content">
                  <span class="listCard__content-date"
                    >Due 9 November 2022, 17:30</span
                  >
                  <span
                    @click="$refs.clearLoan.showPanel()"
                    class="listCard__content-action"
                    >Clear Payment</span
                  >
                </div>
              </li>
              <li>
                <div class="listCard__content">
                  <span>Salary Loan Repayment</span>
                  <span>N1000</span>
                </div>
                <div class="listCard__content">
                  <span class="listCard__content-date"
                    >Due 9 November 2022, 17:30</span
                  >
                  <span
                    @click="$refs.clearLoan.showPanel()"
                    class="listCard__content-action"
                    >Clear Payment</span
                  >
                </div>
              </li>
              <li>
                <div class="listCard__content">
                  <span>Top up your savings plan</span>
                  <span>N1000</span>
                </div>
                <div class="listCard__content">
                  <span class="listCard__content-date"
                    >Due 9 November 2022, 17:30</span
                  >
                  <span
                    @click="$refs.clearLoan.showPanel()"
                    class="listCard__content-action"
                    >Clear Payment</span
                  >
                </div>
              </li>
              <li>
                <div class="listCard__content">
                  <span>Top up your savings plan</span>
                  <span>N1000</span>
                </div>
                <div class="listCard__content">
                  <span class="listCard__content-date"
                    >Due 9 November 2022, 17:30</span
                  >
                  <span
                    @click="$refs.clearLoan.showPanel()"
                    class="listCard__content-action"
                    >Clear Payment</span
                  >
                </div>
              </li>
            </ul>
          </div>
        </v-card>
      </div>

      <!-- active users chat -->
      <div class="col-12 col-md-6 col-lg-4 col-xl-4 list__col">
        <v-card class="listCard activeUserCard" flat color="#fff">
          <div>
            <div class="header">
              <h3>Active Users</h3>
              <v-menu :nudge-bottom="3" offset-y>
                <template v-slot:activator="{ on, attrs }">
                  <v-btn
                    color="var(--border-color)"
                    outlined
                    class="Btn"
                    v-bind="attrs"
                    v-on="on"
                  >
                    <span>This Week</span>
                    <svg
                      width="20"
                      height="18"
                      viewBox="0 0 20 18"
                      fill="none"
                      xmlns="http://www.w3.org/2000/svg"
                    >
                      <path
                        d="M10 11.944L5 7.77734H15L10 11.944Z"
                        fill="#666B70"
                      />
                    </svg>
                  </v-btn>
                </template>
                <v-list class="dropdown__list">
                  <v-list-item class="dropdown__list-item">
                    <v-list-item-title class="dropdown__list-title"
                      >All</v-list-item-title
                    >
                  </v-list-item>
                  <v-list-item class="dropdown__list-item">
                    <v-list-item-title class="dropdown__list-title"
                      >Today</v-list-item-title
                    >
                  </v-list-item>
                  <v-list-item class="dropdown__list-item">
                    <v-list-item-title class="dropdown__list-title"
                      >This Week</v-list-item-title
                    >
                  </v-list-item>
                  <v-list-item class="dropdown__list-item">
                    <v-list-item-title class="dropdown__list-title"
                      >This Month</v-list-item-title
                    >
                  </v-list-item>
                </v-list>
              </v-menu>
            </div>
            <div class="chart__area">
              <ActiveUserChart
                v-for="(item, index) in chart"
                :key="index"
                :chartData="item"
              />
            </div>
          </div>
        </v-card>
      </div>

      <!-- activity Log -->
      <div class="col-12 col-md-12 col-lg-4 col-xl-4 list__col">
        <v-card class="listCard" flat color="#fff">
          <div>
            <div class="header">
              <h3>Activity Log</h3>
            </div>
            <ul>
              <li v-for="n in 5" :key="n">
                <div class="listCard__content">
                  <span>Johhn Doe</span>
                  <span>Logged In</span>
                </div>
                <div class="listCard__content">
                  <span class="listCard__content-date">9 Nov 2022, 17:30</span>
                  <span class="listCard__content-date">Web</span>
                </div>
              </li>
            </ul>
          </div>
        </v-card>
      </div>
    </v-row>
    <ViewDisableClearLoan ref="clearLoan" />
  </div>
</template>

<script>
export default {
  data() {
    return {
      paymentTab: null,
      isFundingWallet: false,
      isWithdrawing: false,
      isSendingMoney: false,
      showAmount: true,
      chart: [
        {
          day: "mon",
          height: 100,
        },
        {
          day: "tue",
          height: 40,
        },
        {
          day: "wed",
          height: 60,
        },
        {
          day: "thu",
          height: 20,
        },
        {
          day: "fri",
          height: 50,
        },
        {
          day: "sat",
          height: 40,
        },
        {
          day: "sun",
          height: 20,
        },
      ],

      cardDetails: [
        {
          title: "Total Wallet Balance",
          value: "₦340,000,000",
          details: "",
          color: "var(--card-one)",
        },
        {
          title: "Total Users",
          value: "1,209",
          details: "",
          color: "#fff",
        },
        {
          title: "Total Savings",
          value: "30",
          details: "₦100,000",
          color: "var(--card-two)",
        },
        {
          title: "Total Investment",
          value: "30",
          details: "₦100,000",
          color: "var(--card-three)",
        },
        {
          title: "Total loans",
          value: "30",
          details: "₦100,000",
          color: "var(--card-four)",
        },
        {
          title: "Total Jollification",
          value: "30",
          details: "₦100,000",
          color: "var(--card-five)",
        },
        {
          title: "Total Transactions",
          value: "3,000",
          details: "₦100,000",
          color: "var(--card-six)",
        },
        {
          title: "Total Withdrwal",
          value: "30",
          details: "₦100,000",
          color: "var(--card-seven)",
        },
      ],
    };
  },
  // page properties go here
};
</script>


