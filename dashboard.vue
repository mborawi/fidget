<template>
  <v-container grid-list-md fluid >
    <v-layout
      row
      wrap
    >
      <v-flex xs4>
          <v-toolbar color="#254351" dark>
            <v-toolbar-title>Weekly Top Performers</v-toolbar-title>
          </v-toolbar>
          <v-list two-line>
              <v-subheader>
                A list of staff who were precieved by peers to perform well this week
              </v-subheader>
            <template v-for="(item, index) in top_weekly">
              <v-list-tile
                :key="item.title"
                avatar
                ripple
                @click="toggle(index)"
              >
                <v-list-tile-content>
                  <v-list-tile-title>{{ item.name }}</v-list-tile-title>
                  <v-list-tile-sub-title class="text--primary">{{ item.job_title }}</v-list-tile-sub-title>
                  <v-list-tile-sub-title >{{ item.bsl }}</v-list-tile-sub-title>
                </v-list-tile-content>

                <v-list-tile-action>
                  <v-btn
                    small
                    fab
                    flat
                    class="grey"
                    outline
                    disabled
                  >
                    <span class="grey--text">{{item.score}}</span>
                  </v-btn>

                  
                </v-list-tile-action>

              </v-list-tile>
              <v-divider
                v-if="index + 1 < top_weekly.length"
                :key="index"
              ></v-divider>
            </template>
          </v-list>
        </v-card>
      </v-flex>

      <v-flex xs4>
          <v-toolbar color="#00BA9F" dark>
            <v-toolbar-title>Consistent Top Performers</v-toolbar-title>
          </v-toolbar>
          <v-list two-line>
            <v-subheader>
              A list of top staff who appeared on top lists and count of times
            </v-subheader>

            <template v-for="(item, index) in top">
              <v-list-tile
                :key="item.title"
                avatar
                ripple
                @click="toggle(index)"
              >
                <v-list-tile-content>
                  <v-list-tile-title>{{ item.name }}</v-list-tile-title>
                  <v-list-tile-sub-title class="text--primary">{{ item.job_title }}</v-list-tile-sub-title>
                  <v-list-tile-sub-title >{{ item.bsl }}</v-list-tile-sub-title>
                </v-list-tile-content>

                <v-list-tile-action>
                  <v-btn
                    small
                    fab
                    flat
                    class="grey"
                    outline
                    disabled
                  >
                    <span class="grey--text">{{item.count}}</span>
                  </v-btn>

                  
                </v-list-tile-action>

              </v-list-tile>
              <v-divider
                v-if="index + 1 < top_weekly.length"
                :key="index"
              ></v-divider>
            </template>
          </v-list>
        </v-flex>
        <v-flex xs4>
            <v-toolbar color="#A5CD2B" dark>
              <v-toolbar-title>Top BSL Teams</v-toolbar-title>
            </v-toolbar>
            <v-list>
              <v-subheader>
                Best Recognised teams
              </v-subheader>
              <template v-for="(item, index) in top_teams">
                <v-list-tile
                  :key="item.name"
                  avatar
                  ripple
                  @click="toggle(index)"
                >
                  <v-list-tile-content>
                    <v-list-tile-title>{{ item.name }}</v-list-tile-title>
                  </v-list-tile-content>

                  <v-list-tile-action>
                    <v-btn
                      small
                      fab
                      flat
                      class="grey"
                      outline
                      disabled
                    >
                      <span class="grey--text">{{item.score}}</span>
                    </v-btn>

                    
                  </v-list-tile-action>

                </v-list-tile>
                <v-divider
                  v-if="index + 1 < top_teams.length"
                  :key="index"
                ></v-divider>
              </template>
            </v-list>
          </v-flex>
          

    </v-layout>
  </v-container>
</template>

<script>
  export default {
    methods: {
         toggle (index) {
           const i = this.selected.indexOf(index)

           if (i > -1) {
             this.selected.splice(i, 1)
           } else {
             this.selected.push(index)
           }
         }
    },
    data: () => ({
      selected: [2],
      top_teams:[
        {
          name: "ATO Innovation",
          score: 22
        },
        {
          name: "Phoenix",
          score: 20
        },
        {
          name: "Enterprise Testing",
          score: 17
        },
        {
          name: "Risk And Intelligence",
          score: 14
        },
        {
          name: "Workplace Diversity",
          score: 12
        },
        {
          name: "Superfunds",
          score: 8
        },
      ],
      top:[
        {
          bsl: 'IAL',
          job_title: 'EL1 Finance Manager',
          name: 'Sharon Krucler',
          count: "26"
        },
        {
          bsl: 'TCN',
          job_title: 'APS6 Client Engagement',
          name: 'Gavin Grace',
          count: "15"
        },
        {
          bsl: 'ESD',
          job_title: 'EL2 Debt Collection Team Leader',
          name: 'Dean Drum',
          count: "12"
        },
        {
          bsl: 'BRR',
          job_title: 'SES2 Deputy Commissioner',
          name: 'Marcus Zhang',
          count: "11"
        },
        {
          bsl: 'ECCI',
          job_title: 'APS6 Data Scientist',
          name: 'Rebecca Dunn',
          count: "8"
        }
      ],
      top_weekly: [
        {
          bsl: 'ATOF',
          job_title: 'EL1 Finance Manager',
          name: 'Ali Connors',
          score: "8.9"
        },
        {
          bsl: 'SDP',
          job_title: 'APS6 Client Engagement',
          name: 'Jennifer Smith',
          score: "8.8"
        },
        {
          bsl: 'PGI',
          job_title: 'EL2 Debt Collection Team Leader',
          name: 'Sandra Adams',
          score: "8.6"
        },
        {
          bsl: 'EST',
          job_title: 'SES2 Deputy Commissioner',
          name: 'Trevor Hansen',
          score: "8.4"
        },
        {
          bsl: 'SMB',
          job_title: 'APS6 Data Scientist',
          name: 'Britta Holt',
          score: "8.3"
        }
      ]
    })
  }
</script>

<style>

</style>
