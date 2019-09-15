<template>
  <v-layout
    column
    justify-center
    align-center
  >
    <v-flex
      xs12
      sm8
      md8
      class="full-width"
    >
      <v-carousel>
        <v-carousel-item
          v-for="(item,i) in items"
          :key="i"
          :src="item.src"
          reverse-transition="fade-transition"
          transition="fade-transition"
        ></v-carousel-item>
      </v-carousel>

      <v-card>
        <v-toolbar flat>
          <template v-slot:extension>
            <v-tabs
              v-model="tabs"
              fixed-tabs
            >
              <v-tabs-slider></v-tabs-slider>
              <v-tab
                href="#tabs-1"
                class="primary--text"
              >
                <v-icon>mdi-chat</v-icon>
              </v-tab>
              <v-tab
                href="#tabs-2"
                class="primary--text"
              >
                <v-icon>mdi-car-side</v-icon>
              </v-tab>
              <v-tab
                href="#tabs-3"
                class="primary--text"
              >
                <v-icon>mdi-cube-outline</v-icon>
              </v-tab>
            </v-tabs>
          </template>
        </v-toolbar>
        <v-tabs-items v-model="tabs">
          <v-tab-item
            v-for="i in 3"
            :key="i"
            :value="'tabs-' + i"
          >
            <v-card flat>
              <v-card-text v-text="texts[i-1].text"></v-card-text>
            </v-card>
          </v-tab-item>
        </v-tabs-items>
      </v-card>
    </v-flex>
  </v-layout>
</template>

<script>
export default {
  data () {
    return {
      tabs: 'tabs-1',
      items: [
        {
          src: '/img/red.jpg',
        },
        {
          src: '/img/green.jpg',
        },
        {
          src: '/img/blue.jpg',
        },
      ],
      texts: [
        {
          text: 'Tab Text 1.',
        },
        {
          text: 'Tab Text 2.',
        },
        {
          text: 'Tab Text 3.',
        },
      ],
    }
  }
}
</script>
