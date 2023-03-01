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
            <span @click="showPanel('topUser')" class="">
              {{ item.user }}
            </span>
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
            <svg
              v-for="n in 5"
              :key="n"
              width="14"
              height="14"
              viewBox="0 0 14 14"
              fill="none"
              xmlns="http://www.w3.org/2000/svg"
            >
              <g clip-path="url(#clip0_458_72254)">
                <path
                  d="M7.00011 10.651L2.88586 12.954L3.80461 8.32935L0.342529 5.12802L5.02495 4.57268L7.00011 0.291016L8.97528 4.57268L13.6577 5.12802L10.1956 8.32935L11.1144 12.954L7.00011 10.651Z"
                  fill="#7DA54A"
                />
              </g>
              <defs>
                <clipPath id="clip0_458_72254">
                  <rect width="14" height="14" fill="white" />
                </clipPath>
              </defs>
            </svg>
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
                @click="showPanel('topUser')"
                class="dropdown__list-item"
              >
                <v-list-item-title class="dropdown__list-title"
                  >Edit</v-list-item-title
                >
              </v-list-item>

              <v-list-item class="dropdown__list-item">
                <v-list-item-title class="dropdown__list-title"
                  >Disable</v-list-item-title
                >
              </v-list-item>
              <v-list-item
                @click="showPanel('showEdit')"
                class="dropdown__list-item delete"
              >
                <v-list-item-title class="dropdown__list-title"
                  >Delete</v-list-item-title
                >
              </v-list-item>
            </v-list>
          </v-menu>
        </div>
      </template>
    </v-data-table>
    <ViewTopUser @showEdit="showPanel('showEdit')" ref="topUser" />
    <EditTopUser ref="showEdit" />
  </div>
</template>

<script>
export default {
  data() {
    return {
      selected: [],
      headers: [
        {
          text: "USER",
          align: "start",
          sortable: false,
          value: "user",
        },
        { text: "QUOTE", value: "category" },
        { text: "IMAGE", value: "email" },
        { text: "RATING", value: "balance" },
        { text: "DATE ADDED", value: "status" },
        { text: "ACTION", value: "action" },
      ],
      admin: [
        {
          id: 1,
          user: "Ogechukwu Moe",
          email: "johndoepics.jpg",
          balance: "Active",
          category: "Impressive and Commited to his savings plans",
          status: "22, Sept. 2022",
        },
        {
          id: 2,
          user: "John Doe",
          email: "johndoepics.jpg",
          balance: "Inactive",
          category: "Impressive and Commited to his savings plans",
          status: "22, Sept. 2022",
        },
        {
          id: 3,
          user: "John Doe",
          email: "johndoepics.jpg",
          balance: "Inactive",
          category: "Impressive and Commited to his savings plans",
          status: "22, Sept. 2022",
        },
        {
          id: 4,
          user: "Kenneth Cole",
          email: "johndoepics.jpg",
          balance: "Inactive",
          category: "Impressive and Commited to his savings plans",
          status: "22, Sept. 2022",
        },
        {
          id: 5,
          user: "Kenneth Cole",
          email: "johndoepics.jpg",
          balance: "Inactive",
          category: "Impressive and Commited to his savings plans",
          status: "22, Sept. 2022",
        },
        {
          id: 6,
          user: "Kenneth Cole",
          email: "johndoepics.jpg",
          balance: "Inactive",
          category: "Impressive and Commited to his savings plans",
          status: "22, Sept. 2022",
        },
      ],
    };
  },
  methods: {
    showPanel(type) {
      switch (type) {
        case "topUser":
          this.$refs.topUser.showPanel();
          break;
        case "showEdit":
          this.$refs.showEdit.showPanel();
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