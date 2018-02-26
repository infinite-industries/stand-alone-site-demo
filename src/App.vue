<template>
  <v-app>
    <div style="max-width: 1100px; margin: auto;" class="white lighten-3">
      <v-toolbar class="white lighten-5">
        <v-layout justify-space-around align-center>
        <!-- <v-toolbar-side-icon></v-toolbar-side-icon> -->
        <v-spacer></v-spacer>
        <v-toolbar-title>Mock-up Community Radio Events Page.</v-toolbar-title>
        <v-spacer></v-spacer>
        <v-btn color="blue" class="white--text">Listen</v-btn>
        <v-btn color="red" class="white--text">DONATE</v-btn>
        </v-layout>
      </v-toolbar>
      <v-toolbar class="white lighten-5" dense>
        <v-menu v-for="(item, index) in menu_items" v-bind:key="index">
          <v-toolbar-items slot="activator">
            <v-btn>{{ item }}<v-icon dark>arrow_drop_down</v-icon></v-btn>
          </v-toolbar-items>
        </v-menu>
      </v-toolbar>
      <v-container>
        <v-layout>
          <v-flex>
            <center>
              <h1>Community Calendar</h1>
            </center>
          </v-flex>
        </v-layout>
      </v-container>
      <v-toolbar>
        <form>
          <input class="placeholder" placeholder="Search..." type="text" value="" style="background:#fafafa; border: 1px solid"/>
          <v-icon>search</v-icon>
        </form>
        <v-toolbar-items>
            <v-btn><font color="blue" size="3">Find By Category<v-icon dark>arrow_drop_down</v-icon></font></v-btn>
            <v-btn><font color="blue" size="3">Find By Date<v-icon dark>arrow_drop_down</v-icon></font></v-btn>
        </v-toolbar-items>
        <v-spacer></v-spacer>
        <v-toolbar-items>
            <v-btn><font color="blue" size="3"><v-icon dark>event</v-icon>Submit An Event</font></v-btn>
        </v-toolbar-items>
      </v-toolbar>
      <v-card>
        <v-container white fluid style="min-height: 0;" grid-list-lg>
          <v-layout wrap>
            <v-flex v-for="(event, index) in events" v-bind:key="index" xs10 offset-xs1>
              <v-card color="blue-grey lighten-5">
                <v-container fluid grid-list-lg>
                  <v-layout row>
                    <v-flex xs5>
                      <v-card-media :src="event.image" height="200px" contain></v-card-media>
                    </v-flex>
                    <v-flex xs7>
                      <v-card-title primary-title>
                        <div class="headline">
                          {{ event.title }}
                        </div>
                      </v-card-title>
                        <div>
                          {{ event.brief_description }}
                        </div>
                        <br />
                        <div>
                          <p>
                            <span v-html="event.when"></span>
                          </p>
                        </div>
                    </v-flex>
                  </v-layout>
                </v-container>
              </v-card>
            </v-flex>
          </v-layout>
        </v-container>
      </v-card>
    </div>
  </v-app>
</template>

<script>

import axios from 'axios'

export default {
  data () {
    return {
      menu_items: [
        'News',
        'Podcasts',
        'Programs',
        'Schedules',
        'Contact',
        'Support',
        'Ways to Listen',
        'Search'
      ],
      events: []
    }
  },
  mounted () {
    const vm = this
    axios.get('http://localhost:3003/events/current/verified?apikey=2019529e-7f8c-44f9-8996-f52a88b2a314')
    .then(function (response) {
      // console.log(response.data.events)
      vm.events = response.data.events
    })
    .catch(function (error) {
      console.log(error)
    })
  },
  name: 'App',
  components: {
    // EventCard
  }
}
</script>
