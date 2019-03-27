<template>
  <v-container grid-list-md fluid >
    <v-flex xs12>
      <v-card class="indigo lighten-4">
        <v-card-title primary-title>
          <div>
            <div class="display-1 mb-0 indigo--text text--darken-2">Skit Dashhood <span class="headline mb-0 grey--text text--darken-3" > WFA ATOP </span> 
            </div>

            <div class="subheading grey--text text--darken-3"> 
              <v-icon color="indigo darken-2">home</v-icon> 
              EL2H Data Scientist
            </div>
            <div class="subheading grey--text text--darken-3"> <v-icon color="indigo darken-2">credit_card</v-icon> AGS  No.: 564228221</div>
          </div>
        </v-card-title>
        
      </v-card>
    </v-flex>
    <v-container grid-list-md fluid >
      <v-layout row wrap>
        <v-flex xs4 class="amber lighten-4 pa-3">
          <v-data-table
          disable-initial-sort
            hide-actions
            :headers="headers"
            :items="performances"
            class="elevation-1"
          >
            <template v-slot:items="props" >
              <tr :class="getColor(props.item.agg_score,props.item.own_score )">
              <td>{{ props.item.week_date }}</td>
              <td class="text-xs-right" >{{ props.item.agg_score }}</td>
              <td class="text-xs-right">{{ props.item.own_score }}</td>
              </tr>
            </template>
          </v-data-table>
        </v-flex>
        <v-flex xs8 elevation=1>
          <v-card>
              <v-toolbar card dense class="amber lighten-2 red--text">
                <v-toolbar-title>
                  <span class="title text-uppercase">Performance</span>
                </v-toolbar-title>
                <v-spacer></v-spacer>
                <v-checkbox v-model="EndabledAll" label="Score all" color="red"></v-checkbox>
              </v-toolbar>

              <v-card-text>
                <v-layout justify-space-between  mb-3>
                  <v-flex text-xs-left>
                    <v-slider
                    v-model="evaluation.self"
                    color="green darken-2"
                    label="Self Evaluation"
                    max=10
                    step=0.5
                    ticks="always"
                    ></v-slider>
                    <v-layout row>
                    <v-flex class="pr-3">
                    <v-slider
                    v-model="evaluation.manager"
                    color="blue darken-2"
                    label="Carlos Sand"
                    max=10
                    step=0.5
                    ticks="always"
                    ></v-slider> 
                  </v-flex>  
                    <v-flex shrink style="width: 60px">
                     <v-text-field
                       v-model="evaluation.manager"
                       class="mt-0"
                       hide-details
                       single-line
                       type="number"
                     ></v-text-field>
                   </v-flex>
                 </v-layout>
                    <v-slider
                    v-model="evaluation.colleague1"
                    color="red darken-2"
                    label="Dave Ludlum"
                    max=10
                    step=0.5
                    ticks="always"
                    ></v-slider>
                    <v-slider
                    v-model="evaluation.colleague2"
                    color="red darken-2"
                    label="Amy Dale"
                    max=10
                    step=0.5
                    ticks="always"
                    ></v-slider>
                    <v-slider
                    v-model="evaluation.subord1"
                    color="amber darken-2"
                    label="Mike Adams"
                    max=10
                    step=0.5
                    ticks="always"
                    ></v-slider>
                  </v-flex>
                </v-layout>

              </v-card-text>
              <v-card-actions>
                <v-btn color="green darken-3 white--text" >Submit<v-icon right dark>check_circle_outline</v-icon></v-btn>
                <v-btn color="red darken-3 white--text" >Clear<v-icon right dark>cancel</v-icon></v-btn>
              </v-card-actions>
            </v-card>
        </v-flex>
      </v-layout>
    </v-container>
  </v-container>
</template>

<script>
  export default {
    methods: {
      getColor:function(own,total){
        if (own > total){
          return "red--text text-lighten-2";
        }else if (total > own){
          return "green--text text-lighten-2";
        }
        return "green lighten-4 green--text text-lighten-1";


      }
    },
    data: () => ({
      EndabledAll: true,
      evaluation: {self:0, manager:0, colleague1:0,colleague2:0, subord1:0},
      headers: [
                { text: 'Week', value: 'week_date', align: 'center', class: 'green--text text--darken-3 subheading' },
                { text: 'Total Score', value: 'agg_score', align: 'center', class: 'green--text text--darken-3 subheading' },
                { text: 'Self Evaluation', value: 'own_score' , align: 'centre', class: 'green--text text--darken-3 subheading'}
              ],
      performances: [
        {
          week_date: "25-Mar-2019",
          agg_score: 8.5,
          own_score: 8,
        },
        {
          week_date: "18-Mar-2019",
          agg_score: 9.1,
          own_score: 8.4,
        },
        {
          week_date: "11-Mar-2019",
          agg_score: 7,
          own_score: 6.8,
        },
        {
          week_date: "25-Feb-2019",
          agg_score: 9,
          own_score: 9,
        },
        {
          week_date: "11-Feb-2019",
          agg_score: 8,
          own_score: 9,
        },
        {
          week_date: "04-Feb-2019",
          agg_score: 8,
          own_score: 9,
        },
        {
          week_date: "28-Jan-2019",
          agg_score: 8,
          own_score: 9,
        }
      ],


    })
  }
</script>

<style>

</style>
