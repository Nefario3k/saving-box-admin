<template>
  <div>
    <v-data-table
      :headers="headers"
      :mobile-breakpoint="766"
      :disable-filtering="true"
      :disable-sort="true"
      :items="admin"
      :single-select="false"
      show-select
      item-key="id"
      :items-per-page="5"
      class="generic__table selectTable"
    >
      <!-- user details  -->
      <template v-slot:item.user="{ item }">
        <div class="user_content">
          <div class="user_content_details">
            <p>
              {{ item.user }}
            </p>
          </div>
        </div>
      </template>

      <!-- email  -->
      <template v-slot:item.email="{ item }">
        <div class="user_content">
          <div class="user_content_details">
            <p>
              {{ item.email }}
            </p>
          </div>
        </div>
      </template>

      <!-- category  -->
      <template v-slot:item.category="{ item }">
        <div class="user_content">
          <div class="user_content_details">
            <p>
              {{ item.category }}
            </p>
          </div>
        </div>
      </template>

      <!-- balance  -->
      <template v-slot:item.balance="{ item }">
        <div class="user_content">
          <div class="user_content_details">
            <p>{{ item.balance }}</p>
          </div>
        </div>
      </template>

      <!-- status  -->
      <template v-slot:item.status="{ item }">
        <div class="user_content">
          <div class="user_content_details">
            <p>
              {{ item.status }}
            </p>
          </div>
        </div>
      </template>

      <!-- action  -->
      <template v-slot:item.action="{ item }">
        <div class="user_content_details" style="justify-content: center">
          <v-menu offset-y min-width="156">
            <template v-slot:activator="{ on, attrs }">
              <div v-bind="attrs" v-on="on" class="action__activator">
                <svg
                  width="17"
                  height="4"
                  viewBox="0 0 17 4"
                  fill="none"
                  xmlns="http://www.w3.org/2000/svg"
                >
                  <g clip-path="url(#clip0_458_67292)">
                    <path
                      d="M6.89022 1.83858C6.89022 2.85374 7.71316 3.67668 8.72831 3.67668C9.74346 3.67668 10.5664 2.85374 10.5664 1.83858C10.5664 0.823431 9.74346 0.000488245 8.72831 0.000488201C7.71316 0.000488157 6.89022 0.823431 6.89022 1.83858Z"
                      fill="#333940"
                    />
                    <path
                      d="M13.3238 1.83858C13.3238 2.85374 14.1468 3.67668 15.1619 3.67668C16.1771 3.67668 17 2.85374 17 1.83858C17 0.823431 16.1771 0.000488245 15.1619 0.000488201C14.1468 0.000488157 13.3238 0.823431 13.3238 1.83858Z"
                      fill="#333940"
                    />
                    <path
                      d="M0.45711 1.83858C0.45711 2.85374 1.28005 3.67668 2.29521 3.67668C3.31036 3.67668 4.1333 2.85374 4.1333 1.83858C4.1333 0.823431 3.31036 0.000488245 2.29521 0.000488201C1.28005 0.000488157 0.45711 0.823431 0.45711 1.83858Z"
                      fill="#333940"
                    />
                  </g>
                  <defs>
                    <clipPath id="clip0_458_67292">
                      <rect
                        width="3.67619"
                        height="16.5429"
                        fill="white"
                        transform="translate(17) rotate(90)"
                      />
                    </clipPath>
                  </defs>
                </svg>
              </div>
            </template>
            <v-list class="dropdown__list">
              <v-list-item
                @click="showPanel('loanDocs')"
                class="dropdown__list-item"
              >
                <v-list-item-title class="dropdown__list-title"
                  >View Details</v-list-item-title
                >
              </v-list-item>
              <v-list-item
                @click="showPanel('approveLoan')"
                class="dropdown__list-item"
              >
                <v-list-item-title class="dropdown__list-title"
                  >Approve Loan</v-list-item-title
                >
              </v-list-item>
              <v-list-item
                @click="showPanel('disableLoan')"
                class="dropdown__list-item"
              >
                <v-list-item-title class="dropdown__list-title"
                  >Reject</v-list-item-title
                >
              </v-list-item>
            </v-list>
          </v-menu>
        </div>
      </template>
    </v-data-table>
    <ViewLoanDocs
      @showApproval="showPanel('approveLoan')"
      @showReject="showPanel('disableLoan')"
      ref="loanDocs"
    />
    <ViewApproveLoanRequest ref="approveLoan" />
    <ViewDisableLoanPage ref="disableLoan" />
    <EditLoanPage ref="editSaving" />
  </div>
</template>

<script>
export default {
  data() {
    return {
      selected: [],
      headers: [
        {
          text: "REQUEST AMOUNT",
          align: "start",
          sortable: false,
          value: "user",
        },
        { text: "USER", value: "category" },
        { text: "PERIOD", value: "email" },
        { text: "DOCUMENTS", value: "balance" },
        { text: "DATE", value: "status" },
        { text: "ACTION", value: "action" },
      ],
      admin: [
        {
          id: 1,
          user: "₦100,000",
          email: "11 Months",
          balance: "5 Document",
          category: "Breaking Bad",
          status: "22, Sept. 2022",
        },
        {
          id: 2,
          user: "₦100,000",
          email: "11 Months",
          balance: "5 Document",
          category: "Kenneth Kings",
          status: "22, Sept. 2022",
        },
        {
          id: 3,
          user: "₦100,000",
          email: "2 Years",
          balance: "5 Document",
          category: "Kenneth Kings",
          status: "22, Sept. 2022",
        },
        {
          id: 4,
          user: "₦100,000",
          email: "2 Years",
          balance: "6 Document",
          category: "John Doe",
          status: "22, Sept. 2022",
        },
        {
          id: 5,
          user: "₦100,000",
          email: "2 Years",
          balance: "6 Document",
          category: "John Doe",
          status: "22, Sept. 2022",
        },
        {
          id: 6,
          user: "₦100,000",
          email: "2 Years",
          balance: "6 Document",
          category: "John Doe",
          status: "22, Sept. 2022",
        },
      ],
    };
  },
  methods: {
    showPanel(type) {
      switch (type) {
        case "loanDocs":
          this.$refs.loanDocs.showPanel();
          break;
        case "editSaving":
          this.$refs.editSaving.showPanel();
          break;
        case "disableLoan":
          this.$refs.disableLoan.showPanel();
          break;
        case "approveLoan":
          this.$refs.approveLoan.showPanel();
          break;

        default:
          break;
      }
    },
  },
};
</script>

<style lang="scss" scoped>
.chip__wrapper {
  display: flex;
  align-items: center;
  gap: 4px;
  flex-wrap: wrap;
}
</style>