<template>
  <v-container>
    <v-row>
      <v-col>
        <v-img
          src="/img/red.jpg"
        />
      </v-col>
    </v-row>
    <v-row
      v-for="(item,i) in images"
      :key="i"
    >
      <v-col>
        <img
          v-lazy="item.src"
        />
      </v-col>
    </v-row>
    <v-row>
      <no-ssr>
        <lazy-component @show="onShowComponent">
          <v-col>
            <v-img
              src="/img/red.jpg"
            />
          </v-col>
        </lazy-component>
      </no-ssr>
    </v-row>
    <template v-if="!!videoId">
      <v-row>
        <v-col>
          <youtube
            :video-id="videoId"
            @ready="ready"
            @ended="ended"
            @playing="playing"
            @error="error"
          />
        </v-col>
      </v-row>
    </template>
  </v-container>
</template>

<script>
export default {
  data () {
    return {
      videoId: '',
      images: [
        {
          src: '/img/red.jpg'
        },
        {
          src: '/img/green.jpg'
        },
        {
          src: '/img/blue.jpg'
        }
      ]
    }
  },
  methods: {
    onShowComponent () {
      console.log('onShowComponent')
      this.videoId = 'nteDXuqBfn0'
    },
    ready () {
      console.log('video ready')
    },
    ended () {
      console.log('video ended')
    },
    playing () {
      console.log('video playing')
    },
    error (e) {
      console.log('video error')
    }
  }
}
</script>
