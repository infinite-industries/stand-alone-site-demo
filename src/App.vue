<template>
  <div style="max-width: 1100px; margin: auto;" class="white lighten-3">
    <v-toolbar class="white lighten-5">
      <v-layout justify-space-around align-center>
      <!-- <v-toolbar-side-icon></v-toolbar-side-icon> -->
      <v-spacer></v-spacer>
      <v-toolbar-title>Sound stories. Sound voices.</v-toolbar-title>
      <v-spacer></v-spacer>
      <v-btn color="blue" class="white--text">Listen</v-btn>
      <v-btn color="red" class="white--text">DONATE</v-btn>
      </v-layout>
    </v-toolbar>
    <v-toolbar class="white lighten-5" dense>
      <v-menu v-for="item in menu_items">
        <v-toolbar-title slot="activator">
          <span>{{ item }}</span>
          <v-icon dark>arrow_drop_down</v-icon>
        </v-toolbar-title>
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
      <v-menu>
        <v-toolbar-title slot="activator">
          <span><font color="blue" size="3">Find By Category</font></span>
          <v-icon dark>arrow_drop_down</v-icon>
        </v-toolbar-title>
      </v-menu>
      <v-menu>
        <v-toolbar-title slot="activator">
          <span><font color="blue" size="3">Find By Date</font></span>
          <v-icon dark>arrow_drop_down</v-icon>
        </v-toolbar-title>
      </v-menu>
      <v-spacer></v-spacer>
      <v-menu>
        <v-toolbar-title>
          <v-icon dark>event</v-icon>
          <span><font color="blue" size="3">Submit An Event</font></span>
        </v-toolbar-title>
      </v-menu>
    </v-toolbar>
    <v-card>
      <v-container white fluid style="min-height: 0;" grid-list-lg>
        <v-layout wrap>
          <v-flex v-for="event in events" xs10 offset-xs1>
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
                      <div><br />
                        {{ event.brief_description }}
                      </div>
                    </v-card-title>
                  </v-flex>
                </v-layout>
              </v-container>
            </v-card>
          </v-flex>
        </v-layout>
      </v-container>
    </v-card>
  </div>
</template>

<script>
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
      events: [
        {
          id: 1,
          title: 'Lorem ipsum dolor sit amet!',
          image: 'https://picsum.photos/300/200?random&sig=121',
          brief_description: 'Phasellus at mollis sem. Quisque ac aliquam arcu. Aliquam dapibus maximus urna eget gravida. Morbi id faucibus eros. Ut sed iaculis felis.'
        },
        {
          id: 2,
          title: 'Nam lectus dui!',
          image: 'https://picsum.photos/300/200?random&sig=122',
          brief_description: 'Fusce ut varius elit. Phasellus malesuada gravida libero. Donec vulputate accumsan hendrerit. Sed vitae sagittis enim, et dictum ex.'
        },
        {
          id: 3,
          title: 'Suspendisse in nulla est!',
          image: 'https://picsum.photos/300/200?random&sig=123',
          brief_description: 'Morbi ex lectus, congue vel mattis sed, facilisis et neque. Sed ante tortor, fringilla at mi in, venenatis tempor felis.'
        },
        {
          id: 4,
          title: 'Nulla a luctus nulla!',
          image: 'https://picsum.photos/300/200?random&sig=124',
          brief_description: 'Sed pharetra, mi non rhoncus blandit, ipsum nisi commodo nunc, sit amet mattis mauris quam vitae mi.'
        },
        {
          id: 5,
          title: 'Donec eget feugiat mi!',
          image: 'https://picsum.photos/300/200?random&sig=125',
          brief_description: 'Aenean quis sapien ac libero blandit suscipit in sit amet nulla. Aenean quis diam nisl.'
        },
        {
          id: 6,
          title: 'Aenean sit amet ullamcorper risus!',
          image: 'https://picsum.photos/300/200?random&sig=126',
          brief_description: 'Mauris sem sem, sodales a elit vitae, ornare volutpat purus. Nullam suscipit augue mauris, a sodales lacus eleifend eget.'
        }
      ],
      clipped: false,
      drawer: true,
      fixed: false,
      items: [{
        icon: 'bubble_chart',
        title: 'Inspire'
      }],
      miniVariant: false,
      right: true,
      rightDrawer: false,
      title: 'Vuetify.js'
    }
  },
  name: 'App',
  components: {
    // EventCard
  }
}
</script>
