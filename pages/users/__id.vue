<template>
  <div>
    <v-row class="row__content">
      <div class="col-12">
        <v-card color="#fff" class="profile__card not__profile__card">
          <div class="userCard">
            <div class="headerSection">
              <div class="titleSection">
                <h3>John Doe</h3>
                <span>@johndoe</span>
              </div>
              <h5 onclick="history.back()">
                <svg
                  width="9"
                  height="14"
                  viewBox="0 0 9 14"
                  fill="none"
                  xmlns="http://www.w3.org/2000/svg"
                >
                  <path
                    d="M8 13L2 7L8 1"
                    stroke="#4169E1"
                    stroke-width="2"
                    stroke-linecap="round"
                  />
                </svg>

                <span>Back</span>
              </h5>
            </div>

            <div class="userInfo">
              <img src="/images/temporary/profile.jpg" alt="avatar" />

              <!-- balance  -->
              <div>
                <span class="titleInfo">Wallet Balance</span>
                <p class="titleValue">₦240,050</p>
              </div>

              <!-- email  -->
              <div>
                <span class="titleInfo">Email</span>
                <p class="titleValue">
                  <a href="mailto:johndoe@gmail.com">johndoe@gmail.com</a>
                </p>
              </div>

              <!-- Phone  -->
              <div>
                <span class="titleInfo">Phone</span>
                <p class="titleValue">
                  <a href="tel:+2349039784784">09039784784</a>
                </p>
              </div>

              <!-- Virtual Account Number  -->
              <div>
                <span class="titleInfo">Virtual Account Number</span>
                <p class="titleValue">09039784784</p>
              </div>
            </div>
          </div>
          <v-divider class="mt-5"></v-divider>

          <div class="noTabMobile" style="width: 100%; max-width: 82.8rem">
            <v-tabs
              :show-arrows="true"
              v-model="jollificationsTab"
              grow
              background-color="transparent"
              color="basil"
              :hide-slider="true"
              class="v-tabs-styles slyTabs"
            >
              <v-tab :ripple="false"> Portfolio</v-tab>
              <v-tab :ripple="false">Verification </v-tab>
              <v-tab :ripple="false"> Transactions </v-tab>
              <v-tab :ripple="false"> Funding Method </v-tab>
              <v-tab :ripple="false"> Referrals </v-tab>
              <v-tab :ripple="false"> Activity Log </v-tab>
            </v-tabs>
          </div>
          <MiniTab
            :inputVal="tabItem[jollificationsTab]"
            :activeTab="jollificationsTab"
            @changeTabs="
              (id) => {
                jollificationsTab = id;
              }
            "
            :tabs="tabItem"
          />

          <v-tabs-items
            v-model="jollificationsTab"
            class="profile__card-tabItems"
          >
            <!-- portfolio  -->
            <v-tab-item>
              <!-- tab control  -->
              <v-tabs
                :show-arrows="true"
                v-model="profileTab"
                background-color="transparent"
                color="var(--primary-color)"
                class="profile__card-tabs"
              >
                <v-tabs-slider color="var(--primary-color)"></v-tabs-slider>
                <v-tab class="profile__card-tab not__profile__card-tabs users">
                  Savings
                </v-tab>
                <v-tab class="profile__card-tab not__profile__card-tabs users">
                  Investibox
                </v-tab>
                <v-tab class="profile__card-tab not__profile__card-tabs users">
                  Loan
                </v-tab>
                <v-tab class="profile__card-tab not__profile__card-tabs users">
                  Jollification
                </v-tab>
              </v-tabs>
              <v-divider
                style="margin-bottom: 18px"
                class="profile__card-divider"
              ></v-divider>

              <SearchArea placeholder="Search by Name, Email & Phone Number" />

              <!-- tab items  -->
              <v-tabs-items v-model="profileTab" class="profile__card-tabItems">
                <v-tab-item>
                  <TablesSaving />
                </v-tab-item>

                <v-tab-item>
                  <TablesInvestibox />
                </v-tab-item>

                <v-tab-item>
                  <TablesLoan />
                </v-tab-item>

                <v-tab-item>
                  <TablesJolly />
                </v-tab-item>
              </v-tabs-items>
            </v-tab-item>
            <!-- verification  -->
            <v-tab-item>
              <div class="verification__tab">
                <h3>BVN</h3>
                <div class="my-2 flex__wrapper">
                  <div>
                    <span class="label">BVN</span>
                    <h4>347995***673</h4>
                  </div>
                  <div>
                    <span class="label">Date of Birth</span>
                    <h4>10-09-2000</h4>
                  </div>
                </div>

                <v-divider class="mt-5"></v-divider>
                <div class="my-5 flex__wrapper items">
                  <div>
                    <h3>KYC Verification</h3>
                  </div>
                  <div>
                    <h5>
                      <svg
                        width="24"
                        height="24"
                        viewBox="0 0 24 24"
                        fill="none"
                        xmlns="http://www.w3.org/2000/svg"
                      >
                        <path
                          fill-rule="evenodd"
                          clip-rule="evenodd"
                          d="M7.367 7.7325C7.781 7.7325 8.117 8.0685 8.117 8.4825C8.117 8.8965 7.781 9.2325 7.367 9.2325H6.426C4.812 9.2325 3.5 10.5435 3.5 12.1565V17.0415C3.5 18.6605 4.816 19.9765 6.435 19.9765H17.575C19.187 19.9765 20.5 18.6635 20.5 17.0515V12.1675C20.5 10.5485 19.183 9.2325 17.566 9.2325H16.634C16.22 9.2325 15.884 8.8965 15.884 8.4825C15.884 8.0685 16.22 7.7325 16.634 7.7325H17.566C20.011 7.7325 22 9.7225 22 12.1675V17.0515C22 19.4915 20.014 21.4765 17.575 21.4765H6.435C3.99 21.4765 2 19.4875 2 17.0415V12.1565C2 9.7165 3.985 7.7325 6.426 7.7325H7.367ZM12.0008 3C12.4148 3 12.7508 3.336 12.7508 3.75L12.75 13.976L14.3858 12.334C14.6778 12.04 15.1518 12.04 15.4458 12.332C15.7388 12.624 15.7398 13.099 15.4478 13.393L12.5385 16.3137C12.5101 16.3429 12.4794 16.3698 12.4466 16.3941L12.5318 16.32C12.4996 16.3527 12.4646 16.382 12.4275 16.4078C12.4048 16.4234 12.3818 16.4376 12.358 16.4506C12.3465 16.4568 12.3344 16.463 12.3222 16.4687C12.3004 16.4791 12.278 16.4885 12.2551 16.4967C12.2436 16.5008 12.2321 16.5046 12.2206 16.5081C12.1924 16.5169 12.1635 16.5239 12.1339 16.5292C12.1272 16.5303 12.1212 16.5313 12.1151 16.5323C12.0912 16.536 12.0663 16.5386 12.0411 16.5399C12.0275 16.5406 12.0142 16.541 12.0008 16.541L11.961 16.538L11.8991 16.5341C11.8947 16.5336 11.8903 16.5329 11.8859 16.5322L12.0008 16.541C11.9561 16.541 11.9118 16.537 11.8683 16.5292C11.8382 16.5239 11.8093 16.5169 11.7811 16.5083C11.7699 16.5047 11.7588 16.5011 11.7478 16.4971C11.7249 16.489 11.7022 16.4796 11.6801 16.4691C11.6666 16.4627 11.6533 16.4559 11.6401 16.4487C11.6217 16.4385 11.6039 16.4277 11.5866 16.4162C11.5747 16.4084 11.5629 16.4 11.5512 16.3913C11.5227 16.3698 11.4957 16.3464 11.4705 16.3212L11.4698 16.32L8.5538 13.393C8.2618 13.099 8.2628 12.624 8.5558 12.332C8.8498 12.04 9.3238 12.04 9.6158 12.334L11.25 13.976L11.2508 3.75C11.2508 3.336 11.5868 3 12.0008 3Z"
                          fill="#4169E1"
                        />
                      </svg>

                      <span>Download All Document</span>
                    </h5>
                  </div>
                </div>

                <div class="verification__tab-table">
                  <TablesKyc />
                </div>
              </div>
            </v-tab-item>
            <!-- transactions  -->
            <v-tab-item>
              <div class="trans__tab">
                <div class="filterTab">
                  <div class="tabs active"><span>All</span></div>
                  <div class="tabs"><span>Credit</span></div>
                  <div class="tabs"><span>Debit</span></div>
                  <div class="tabs"><span>Jollification</span></div>
                </div>
                <SearchArea
                  placeholder="Search by Name, Email & Phone Number"
                />
                <TablesTransaction />
              </div>
            </v-tab-item>
            <!-- card  -->
            <v-tab-item>
              <!-- tab control  -->
              <v-tabs
                v-model="fundingTab"
                background-color="transparent"
                color="var(--primary-color)"
                class="profile__card-tabs"
              >
                <v-tabs-slider color="var(--primary-color)"></v-tabs-slider>
                <v-tab class="profile__card-tab not__profile__card-tabs users">
                  My Cards
                </v-tab>
                <v-tab class="profile__card-tab not__profile__card-tabs users">
                  Virtual Account
                </v-tab>
              </v-tabs>
              <v-divider
                style="margin-bottom: 18px"
                class="profile__card-divider"
              ></v-divider>
              <div class="bank__tab">
                <v-tabs-items v-model="fundingTab">
                  <!-- cards  -->
                  <v-tab-item>
                    <div v-if="hasCard" class="card__wrapper">
                      <div class="card pa-6">
                        <div class="row">
                          <div class="col-9">
                            <h4>5668 **** **** 4990</h4>
                          </div>
                          <div class="col-3">
                            <img src="/images/icons/mastercard.png" alt="" />
                          </div>
                        </div>
                        <div class="card-details">
                          <div class="">
                            <span>03/24</span>
                            <span>JOHN DOE</span>
                          </div>
                          <div class="">
                            <span>123</span>
                          </div>
                          <div class=""></div>
                        </div>
                      </div>
                      <div class="card pa-6">
                        <div class="row">
                          <div class="col-9">
                            <h4>5668 **** **** 4990</h4>
                          </div>
                          <div class="col-3">
                            <img src="/images/icons/visa.png" alt="" />
                          </div>
                        </div>
                        <div class="card-details">
                          <div class="">
                            <span>03/24</span>
                            <span>JOHN DOE</span>
                          </div>
                          <div class="">
                            <span>123</span>
                          </div>
                          <div class=""></div>
                        </div>
                      </div>
                    </div>
                    <div v-else class="noCard__wrapper">
                      <svg
                        width="124"
                        height="124"
                        viewBox="0 0 124 124"
                        fill="none"
                        xmlns="http://www.w3.org/2000/svg"
                      >
                        <path
                          d="M3.875 62C3.875 69.6331 5.37845 77.1914 8.2995 84.2435C11.2206 91.2955 15.502 97.7032 20.8994 103.101C26.2968 108.498 32.7045 112.779 39.7565 115.7C46.8086 118.622 54.3669 120.125 62 120.125C69.6331 120.125 77.1914 118.622 84.2435 115.7C91.2955 112.779 97.7032 108.498 103.101 103.101C108.498 97.7032 112.779 91.2955 115.7 84.2435C118.622 77.1914 120.125 69.6331 120.125 62C120.125 54.3669 118.622 46.8086 115.7 39.7565C112.779 32.7045 108.498 26.2968 103.101 20.8994C97.7032 15.502 91.2955 11.2206 84.2435 8.2995C77.1914 5.37845 69.6331 3.875 62 3.875C54.3669 3.875 46.8086 5.37845 39.7565 8.2995C32.7045 11.2206 26.2968 15.502 20.8994 20.8994C15.502 26.2968 11.2206 32.7045 8.2995 39.7565C5.37845 46.8086 3.875 54.3669 3.875 62Z"
                          fill="#EDF1FF"
                        />
                        <path
                          d="M27.125 44.175C27.125 41.075 29.45 38.75 33.325 38.75H91.45C94.55 38.75 97.65 41.075 97.65 44.175V79.05C97.65 82.15 95.325 84.475 91.45 84.475H33.325C30.225 84.475 27.125 82.15 27.125 79.05V44.175Z"
                          fill="#CFDBFF"
                        />
                        <path
                          d="M27.125 47.2749H96.875V55.7999H27.125V47.2749Z"
                          fill="#FFCA83"
                        />
                        <path
                          d="M76.725 73.6249C76.725 72.0749 78.275 70.5249 79.825 70.5249H88.35C89.9 70.5249 91.45 72.0749 91.45 73.6249V76.7249C91.45 78.2749 89.9 79.8249 88.35 79.8249H79.825C78.275 79.8249 76.725 78.2749 76.725 76.7249V73.6249Z"
                          fill="white"
                        />
                      </svg>
                      <span>User has no card added yet</span>
                    </div>
                  </v-tab-item>
                  <!-- virtual account  -->
                  <v-tab-item>
                    <div v-if="hasCard" class="card__wrapper">
                      <div class="card pa-6 account relative">
                        <div class="row">
                          <div class="col-12">
                            <h4>GUARANTEE TRUST BANK</h4>
                          </div>
                        </div>
                        <div class="card-details">
                          <div class="">
                            <span>Account Number</span>
                            <span>30556828902</span>
                          </div>
                          <div class="">
                            <svg
                              width="20"
                              height="20"
                              viewBox="0 0 20 20"
                              fill="none"
                              xmlns="http://www.w3.org/2000/svg"
                            >
                              <g clip-path="url(#clip0_540_96627)">
                                <path
                                  d="M16.6667 7.5H9.16667C8.24619 7.5 7.5 8.24619 7.5 9.16667V16.6667C7.5 17.5871 8.24619 18.3333 9.16667 18.3333H16.6667C17.5871 18.3333 18.3333 17.5871 18.3333 16.6667V9.16667C18.3333 8.24619 17.5871 7.5 16.6667 7.5Z"
                                  stroke="#4169E1"
                                  stroke-width="2"
                                  stroke-linecap="round"
                                  stroke-linejoin="round"
                                />
                                <path
                                  d="M4.16406 12.5013H3.33073C2.8887 12.5013 2.46478 12.3257 2.15222 12.0131C1.83966 11.7006 1.66406 11.2767 1.66406 10.8346V3.33464C1.66406 2.89261 1.83966 2.46868 2.15222 2.15612C2.46478 1.84356 2.8887 1.66797 3.33073 1.66797H10.8307C11.2728 1.66797 11.6967 1.84356 12.0092 2.15612C12.3218 2.46868 12.4974 2.89261 12.4974 3.33464V4.16797"
                                  stroke="#4169E1"
                                  stroke-width="2"
                                  stroke-linecap="round"
                                  stroke-linejoin="round"
                                />
                              </g>
                              <defs>
                                <clipPath id="clip0_540_96627">
                                  <rect width="20" height="20" fill="white" />
                                </clipPath>
                              </defs>
                            </svg>
                          </div>
                        </div>
                      </div>
                    </div>
                    <div v-else class="noCard__wrapper">
                      <svg
                        width="124"
                        height="124"
                        viewBox="0 0 124 124"
                        fill="none"
                        xmlns="http://www.w3.org/2000/svg"
                      >
                        <path
                          d="M3.875 62C3.875 69.6331 5.37845 77.1914 8.2995 84.2435C11.2206 91.2955 15.502 97.7032 20.8994 103.101C26.2968 108.498 32.7045 112.779 39.7565 115.7C46.8086 118.622 54.3669 120.125 62 120.125C69.6331 120.125 77.1914 118.622 84.2435 115.7C91.2955 112.779 97.7032 108.498 103.101 103.101C108.498 97.7032 112.779 91.2955 115.7 84.2435C118.622 77.1914 120.125 69.6331 120.125 62C120.125 54.3669 118.622 46.8086 115.7 39.7565C112.779 32.7045 108.498 26.2968 103.101 20.8994C97.7032 15.502 91.2955 11.2206 84.2435 8.2995C77.1914 5.37845 69.6331 3.875 62 3.875C54.3669 3.875 46.8086 5.37845 39.7565 8.2995C32.7045 11.2206 26.2968 15.502 20.8994 20.8994C15.502 26.2968 11.2206 32.7045 8.2995 39.7565C5.37845 46.8086 3.875 54.3669 3.875 62Z"
                          fill="#EDF1FF"
                        />
                        <path
                          d="M27.125 44.175C27.125 41.075 29.45 38.75 33.325 38.75H91.45C94.55 38.75 97.65 41.075 97.65 44.175V79.05C97.65 82.15 95.325 84.475 91.45 84.475H33.325C30.225 84.475 27.125 82.15 27.125 79.05V44.175Z"
                          fill="#CFDBFF"
                        />
                        <path
                          d="M27.125 47.2749H96.875V55.7999H27.125V47.2749Z"
                          fill="#FFCA83"
                        />
                        <path
                          d="M76.725 73.6249C76.725 72.0749 78.275 70.5249 79.825 70.5249H88.35C89.9 70.5249 91.45 72.0749 91.45 73.6249V76.7249C91.45 78.2749 89.9 79.8249 88.35 79.8249H79.825C78.275 79.8249 76.725 78.2749 76.725 76.7249V73.6249Z"
                          fill="white"
                        />
                      </svg>
                      <span>User has no card added yet</span>
                    </div>
                  </v-tab-item>
                </v-tabs-items>
              </div>
            </v-tab-item>
            <!-- referral  -->
            <v-tab-item>
              <div class="referral__tab">
                <div class="commision my-5">
                  <span class="tag">Total Commission Earned</span>
                  <span class="value">₦12,000</span>
                </div>
                <SearchArea
                  placeholder="Search by Name, Email & Phone Number"
                />
                <TablesReferral />
              </div>
            </v-tab-item>
            <!-- avtivity log  -->
            <v-tab-item>
              <div class="activity__tab relative">
                <div class="mt-2 right-drawer-container">
                  <div>
                    <div class="right-drawer-title">
                      <div class="intro">
                        <svg
                          width="28"
                          height="28"
                          viewBox="0 0 28 28"
                          fill="none"
                          xmlns="http://www.w3.org/2000/svg"
                        >
                          <g clip-path="url(#clip0_590_82190)">
                            <path
                              d="M13.9999 2.33301C20.4434 2.33301 25.6666 7.55618 25.6666 13.9997C25.6666 20.4432 20.4434 25.6663 13.9999 25.6663C7.55642 25.6663 2.33325 20.4432 2.33325 13.9997H4.66659C4.66659 19.154 8.84559 23.333 13.9999 23.333C19.1543 23.333 23.3333 19.154 23.3333 13.9997C23.3333 8.84534 19.1543 4.66634 13.9999 4.66634C10.7916 4.66634 7.96125 6.28451 6.28242 8.74967H9.33325V11.083H2.33325V4.08301H4.66659V6.99967C6.79459 4.16467 10.1838 2.33301 13.9999 2.33301ZM15.1666 8.16634V13.5155L18.9501 17.299L17.2993 18.9498L12.8333 14.4815V8.16634H15.1666Z"
                              fill="#000831"
                            />
                          </g>
                          <defs>
                            <clipPath id="clip0_590_82190">
                              <rect width="28" height="28" fill="white" />
                            </clipPath>
                          </defs>
                        </svg>
                        <h1 class="">Activity Details</h1>
                      </div>
                    </div>
                  </div>
                </div>

                <div class="timeline">
                  <div class="local__data">
                    <div>
                      <span>IP Address:</span>
                      <span class="activityIp">192.158.1.38</span>
                    </div>
                  </div>
                  <v-divider class="divider"></v-divider>
                  <div class="timelineWrapper">
                    <v-timeline align-top dense>
                      <v-timeline-item
                        v-for="(item, i) in 20"
                        :key="i"
                        color="transparent"
                      >
                        <template v-if="i % 2" v-slot:icon>
                          <svg
                            width="32"
                            height="32"
                            viewBox="0 0 32 32"
                            fill="none"
                            xmlns="http://www.w3.org/2000/svg"
                          >
                            <circle
                              cx="16"
                              cy="16"
                              r="15.5"
                              fill="white"
                              stroke="#D0D0D0"
                            />
                            <g clip-path="url(#clip0_606_81654)">
                              <path
                                d="M20.6735 21.333L8.50772 21.333C8.28465 21.333 8.07073 21.2696 7.913 21.1567C7.75527 21.0439 7.66667 20.8908 7.66667 20.7312L7.66667 11.1015C7.66667 10.9419 7.75528 10.7888 7.913 10.6759C8.07073 10.5631 8.28466 10.4997 8.50772 10.4997L20.6735 10.4997C20.8119 10.4997 20.9482 10.5241 21.0703 10.5708C21.1924 10.6175 21.2964 10.6851 21.3733 10.7675L25.8586 15.5823C25.9508 15.6812 26 15.7974 26 15.9163C26 16.0352 25.9508 16.1515 25.8586 16.2504L21.3733 21.0652C21.2964 21.1476 21.1924 21.2151 21.0703 21.2619C20.9482 21.3086 20.8119 21.333 20.6735 21.333ZM12.713 16.5182L18.6003 16.5182L18.6003 15.3145L12.713 15.3145L12.713 16.5182Z"
                                fill="#1C861C"
                              />
                            </g>
                            <defs>
                              <clipPath id="clip0_606_81654">
                                <rect
                                  width="20"
                                  height="14.1667"
                                  fill="white"
                                  transform="translate(26 23) rotate(-180)"
                                />
                              </clipPath>
                            </defs>
                          </svg>
                        </template>
                        <template v-else v-slot:icon>
                          <svg
                            width="32"
                            height="32"
                            viewBox="0 0 32 32"
                            fill="none"
                            xmlns="http://www.w3.org/2000/svg"
                          >
                            <circle
                              cx="16"
                              cy="16"
                              r="15.5"
                              fill="white"
                              stroke="#D0D0D0"
                            />
                            <g clip-path="url(#clip0_590_82207)">
                              <path
                                d="M16.75 11.7151L20.285 15.2509L12.035 23.5001H8.5V19.9642L16.75 11.7151ZM17.9283 10.5367L19.6958 8.7684C19.8521 8.61218 20.064 8.52441 20.285 8.52441C20.506 8.52441 20.7179 8.61218 20.8742 8.7684L23.2317 11.1259C23.3879 11.2822 23.4757 11.4941 23.4757 11.7151C23.4757 11.936 23.3879 12.148 23.2317 12.3042L21.4633 14.0717L17.9283 10.5367Z"
                                fill="#666B70"
                              />
                            </g>
                            <defs>
                              <clipPath id="clip0_590_82207">
                                <rect
                                  width="20"
                                  height="20"
                                  fill="white"
                                  transform="translate(6 6)"
                                />
                              </clipPath>
                            </defs>
                          </svg>
                        </template>

                        <div class="timeline__wrapper">
                          <h3>
                            <span class="name">John Doe</span> Declined a loan
                            request from
                            <span class="admin">Maxwell Hima</span>
                          </h3>
                          <span class="timeline__date"
                            >Nov 7, 2022 at 09:35 AM Via Web</span
                          >
                        </div>
                      </v-timeline-item>

                      <!-- bottom  -->
                      <v-timeline-item color="transparent">
                        <template v-slot:icon>
                          <svg
                            style="cursor: pointer"
                            width="30"
                            height="30"
                            viewBox="0 0 30 30"
                            fill="none"
                            xmlns="http://www.w3.org/2000/svg"
                          >
                            <rect
                              x="0.5"
                              y="0.5"
                              width="29"
                              height="29"
                              rx="4.5"
                              fill="white"
                              stroke="#D0D0D0"
                            />
                            <g clip-path="url(#clip0_606_81671)">
                              <path
                                d="M15 24L10 19.7572L11.2498 18.6968L15 21.879L18.7502 18.6968L20 19.7572L15 24ZM15 8.121L11.2498 11.3032L10 10.2427L15 6L20 10.2428L18.7502 11.3025L15 8.121Z"
                                fill="#666B70"
                              />
                            </g>
                            <defs>
                              <clipPath id="clip0_606_81671">
                                <rect
                                  width="20"
                                  height="20"
                                  fill="white"
                                  transform="translate(25 5) rotate(90)"
                                />
                              </clipPath>
                            </defs>
                          </svg>
                        </template>
                        <div class="timeline__wrapper">
                          <h3 class="showMore">Show 4 more activity</h3>
                        </div>
                      </v-timeline-item>
                    </v-timeline>
                  </div>
                </div>
              </div>
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
      fundingTab: null,
      paymentTab: null,
      hasCard: true,
      jollificationsTab: 0,
      closeOnContent: false,
      tabItem: [
        "Portfolio",
        "Verification",
        "Transactions",
        "Funding Method",
        "Referrals",
        "Activity Log",
      ],
    };
  },
  mounted() {
    if (this.$route.query.verify)
      this.jollificationsTab = parseInt(this.$route.query.verify);
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

<style scoped lang='scss'>
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
