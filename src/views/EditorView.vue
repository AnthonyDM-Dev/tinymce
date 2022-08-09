<template>
  <div id="editor">
    <TinyMce
      :api-key="tinyApiKey"
      :settings="settings"
    />
    <button class="editor__button" @click="writeRandomPhrase"><p>Write</p></button>
  </div>
</template>

<script>
import TinyMce from '../components/TinyMce.vue'
export default {
  name: 'EditorView',
  components: {
    TinyMce
  },
  data () {
    return {
      settings: {
        width: 400,
        height: 400,
        skin: 'borderless',
        content_css: 'dark',
        toolbar_mode: 'undo redo styles bold italic alignleft aligncenter alignright alignjustify | bullist numlist outdent indent',
      },
      phrases: [
        'To be or not to be: that is the question',
        'Tis better to have loved and lost than never to have loved at all',
        'Tread softly because you tread on my dreams',
        'Two roads diverged in a wood, and I... I took the road less traveled by',
        'If I should die, think only this of me',
        'Water, water, everywhere, nor any drop to drink',
        'Season of mists and mellow fruitfulness',
        'I wandered lonely as a cloud'
      ],
      tags: [
        'p', 'h1', 'h2', 'h3', 'h4', 'h5', 'h6'
      ]
    }
  },
  methods: {
    randomInt (min, max) {
      return Math.floor(Math.random() * (max - min + 1)) + min
    },
    writeRandomPhrase () {
      window.tinymce.activeEditor.insertContent(
        this.addRandomTag(this.generateTextFromArray(this.phrases))
      )
    },
    generateTextFromArray (array) {
      return array[this.randomInt(0, array.length - 1)]
    },
    addRandomTag (text) {
      const randomTag = this.generateTextFromArray(this.tags)
      const openTag = '<' + randomTag + '>'
      const endTag = '</' + randomTag + '>'
      return openTag + text + endTag
    }
  },
  computed: {
    tinyApiKey () {
      return process.env.VUE_APP_TINY_API_KEY
    }
  }
}
</script>

<style lang="scss" scoped>
@import '../assets/styles/editor.scss';
</style>
