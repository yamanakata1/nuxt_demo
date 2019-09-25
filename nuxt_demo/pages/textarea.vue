<template>
  <v-container fluid>
    <v-row>
      <v-col cols="12">
        <v-textarea
	  ref="inputText"
          name="input"
          label="Input Text."
          value="This is youtube URL. https://www.youtube.com/watch?v=2uZYKcKHgU0 and, https://youtu.be/0Qv-6fQBFfA"
        ></v-textarea>
      </v-col>
    </v-row>
    <v-row>
      <v-col cols="2">
        <v-btn text @click="convertInputText">
          Convert
        </v-btn>
      </v-col>
      <v-col cols="10">
        <span class="font-weight-light">Convert Youtube URL to Youtube Thumbnail.</span>
      </v-col>
    </v-row>
    <v-row>
      <v-col cols="12">
        <v-card>
          <v-card-text>
	    {{normalText}}
          </v-card-text>
	  <div v-for="(url, index) in thumbnailURLs" :key="index">
	    <img :src="url">
	  </div>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  data () {
    return {
      normalText: '',
      thumbnailURLs: [],
    }
  },
  methods: {
    convertInputText () {
      const str = this.$refs.inputText.value.trim()
      this.setNormalText(str)
      this.setThumbnailURLs(str)
    },
    setNormalText (str) {
      const regex = new RegExp('https://www\\.youtube\\.com/watch\\?v=[a-zA-Z0-9_\\-]+|https://youtu\\.be/[a-zA-Z0-9_\\-]+', 'g')
      this.normalText = str.replace(regex, '')
    },
    setThumbnailURLs (str) {
      const regex = new RegExp('https://www\\.youtube\\.com/watch\\?v=[a-zA-Z0-9_\\-]+|https://youtu\\.be/[a-zA-Z0-9_\\-]+', 'g')
      const regex2 = new RegExp('https://www\\.youtube\\.com/watch\\?v=([a-zA-Z0-9_\\-]+)|https://youtu\\.be/([a-zA-Z0-9_\\-]+)')
      this.thumbnailURLs = str.match(regex).map(v => v.replace(regex2, 'https://img.youtube.com/vi/$1$2/default.jpg'))
    }
  }
}
</script>
