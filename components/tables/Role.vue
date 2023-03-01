<template>
  <div>
    <v-data-table
      :headers="headers"
      :mobile-breakpoint="766"
      :disable-filtering="true"
      :disable-sort="true"
      :items="admin"
      :items-per-page="5"
      class="generic__table"
    >
      <!-- user details  -->
      <template v-slot:item.user="{ item }">
        <div class="user_content">
          <div class="user_content_details">
            <span @click="showPanel('viewRole')">{{ item.user }}</span>
          </div>
        </div>
      </template>

      <!-- role  -->
      <template v-slot:item.role="{ item }">
        <div class="user_content">
          <div class="user_content_details">
            <p>{{ item.role }}</p>
          </div>
        </div>
      </template>

      <!-- date  -->
      <template v-slot:item.date="{ item }">
        <div class="user_content">
          <div class="user_content_details">
            <p>{{ item.date }}</p>
          </div>
        </div>
      </template>

      <!-- created  -->
      <template v-slot:item.created="{ item }">
        <div class="user_content">
          <div class="user_content_details">
            <p>{{ item.created }}</p>
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
                @click="showPanel('viewRole')"
                class="dropdown__list-item"
              >
                <v-list-item-title class="dropdown__list-title"
                  >View</v-list-item-title
                >
              </v-list-item>
              <v-list-item
                @click="showPanel('editRole')"
                class="dropdown__list-item"
              >
                <v-list-item-title class="dropdown__list-title"
                  >Edit</v-list-item-title
                >
              </v-list-item>
              <v-list-item
                @click="showPanel('deleteRole')"
                class="dropdown__list-item"
              >
                <v-list-item-title class="dropdown__list-title delete"
                  >Delete</v-list-item-title
                >
              </v-list-item>
            </v-list>
          </v-menu>
        </div>
      </template>
    </v-data-table>
    <ViewRole @showEdit="showPanel('editRole')" ref="viewRole" />
    <EditRole ref="editRole" />
    <ViewDisableRole ref="deleteRole" />
  </div>
</template>

<script>
export default {
  data() {
    return {
      headers: [
        {
          text: "ROLE",
          align: "start",
          sortable: false,
          value: "user",
        },
        { text: "ASSIGNED", value: "role" },
        { text: "DATE CREATED", value: "created" },
        { text: "PERMISSIONS", value: "date" },
        { text: "ACTION", value: "action" },
      ],
      admin: [
        {
          user: "Compliant Officer",
          role: 1,
          date: 14,
          created: "22 April. 2023",
          protein: 4.0,
          iron: 1,
        },
        {
          user: "Compliant Officer",
          role: 3,
          date: 23,
          created: "22 April. 2023",
          protein: 4.3,
          iron: 1,
        },
        {
          user: "Loan Officer",
          role: 3,
          date: 50,
          created: "22 April. 2023",
          protein: 6.0,
          iron: 7,
        },
        {
          user: "Loan Officer",
          role: 5,
          date: 14,
          created: "22 April. 2023",
          protein: 4.3,
          iron: 8,
        },
        {
          user: "Investment Officer",
          role: 2,
          date: 45,
          created: "22 April. 2023",
          protein: 3.9,
          iron: 16,
        },
      ],
    };
  },
  methods: {
    showPanel(type) {
      switch (type) {
        case "viewRole":
          this.$refs.viewRole.showPanel();
          break;
        case "editRole":
          this.$refs.editRole.showPanel();
          break;
        case "deleteRole":
          this.$refs.deleteRole.showPanel();
          break;

        default:
          break;
      }
    },
  },
};
</script>

<style lang="scss" scoped>
</style>