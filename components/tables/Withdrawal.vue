<template>
  <div>
    <v-data-table
      :headers="headers"
      :mobile-breakpoint="766"
      :disable-filtering="true"
      :disable-sort="true"
      :items="admin"
      item-key="id"
      :items-per-page="5"
      class="generic__table"
    >
      <!-- user details  -->
      <template v-slot:item.user="{ item }">
        <div class="user_content">
          <div class="user_content_details">
            <div>
              <p>{{ item.user }}</p>
            </div>
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

      <!-- date  -->
      <template v-slot:item.date="{ item }">
        <div class="user_content">
          <div class="user_content_details">
            <p>
              {{ item.date }}
            </p>
          </div>
        </div>
      </template>

      <!-- bName  -->
      <template v-slot:item.bName="{ item }">
        <div class="user_content">
          <div class="user_content_details">
            <p>
              {{ item.bName }}
            </p>
          </div>
        </div>
      </template>

      <!-- balance  -->
      <template v-slot:item.balance="{ item }">
        <div class="user_content">
          <div class="user_content_details">
            <p v-if="item.balance">{{ item.balance }}</p>
            <p v-else>Null</p>
          </div>
        </div>
      </template>

      <!-- status  -->
      <template v-slot:item.status="{ item }">
        <div class="user_content">
          <div class="user_content_details">
            <p
              :class="{
                approved: item.status == 'successful',
                danger: item.status == 'declined',
              }"
            >
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
                @click="showPanel('request')"
                class="dropdown__list-item"
              >
                <v-list-item-title class="dropdown__list-title"
                  >View Details</v-list-item-title
                >
              </v-list-item>

              <v-list-item class="dropdown__list-item">
                <v-list-item-title class="dropdown__list-title"
                  >Approve</v-list-item-title
                >
              </v-list-item>
              <v-list-item class="dropdown__list-item">
                <v-list-item-title class="dropdown__list-title"
                  >Disapprove</v-list-item-title
                >
              </v-list-item>
            </v-list>
          </v-menu>
        </div>
      </template>
    </v-data-table>
    <ViewWithdrawRequest ref="request" />
  </div>
</template>

<script>
export default {
  data() {
    return {
      selected: [],
      headers: [
        {
          text: "USERS",
          align: "start",
          sortable: false,
          value: "user",
        },
        { text: "REQUEST AMOUNT", value: "email" },
        { text: "ACCOUNt NUMBER", value: "balance" },
        { text: "BANK NAME", value: "bName" },
        { text: "STATUS", value: "status" },
        { text: "DATE", value: "date" },
        { text: "ACTION", value: "action" },
      ],
      admin: [
        {
          id: 1,
          user: "John Doe",
          email: "₦10,000",
          number: "6 Months",
          bName: "First Bank",
          balance: "22348599599",
          status: "successful",
          date: "22, Sept. 2022",
        },
        {
          id: 2,
          user: "John Doe",
          email: "₦10,000",
          number: "6 Months",
          balance: null,
          bName: "Bank of Sapa",
          status: "declined",
          date: "22, Sept. 2022",
        },
        {
          id: 3,
          user: "Kenneth Doe",
          email: "₦10,000",
          number: "6 Months",
          balance: "22348599599",
          bName: "GT Bank",
          status: "successful",
          date: "22, Sept. 2022",
        },
        {
          id: 4,
          user: "Kenneth Kings",
          email: "₦10,000",
          number: "6 Months",
          balance: "22348599599",
          bName: "Access Bank",
          status: "successful",
          date: "22, Sept. 2022",
        },
      ],
    };
  },
  methods: {
    showPanel(type) {
      switch (type) {
        case "request":
          this.$refs.request.showPanel();
          break;
        case "edit":
          this.$refs.userEdit.showPanel();
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