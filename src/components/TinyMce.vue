<template>
  <div class="tinymce-editor">
    <editor
      :api-key="apiKey"
      :init="settings"
    />
  </div>
</template>

<script>
import Editor from '@tinymce/tinymce-vue'
export default {
  name: 'TinyMce',
  components: {
    Editor
  },
  mounted () {
    this.emitter.on('write', () => {
      this.insertContent()
    })
  },
  data () {
    return {
      editor: null,
      settings: {
        width: 400,
        height: 400,
        skin: 'borderless',
        content_css: 'dark',
        toolbar_mode: 'undo redo styles bold italic alignleft aligncenter alignright alignjustify | bullist numlist outdent indent',
        setup: (editor) => {
          this.editor = editor
        }
      },
    }
  },
  props: {
    apiKey: String,
    phrases: Array,
    tags: Array
  },
  methods: {
    insertContent () {
      this.editor.insertContent(
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
    },
    randomInt (min, max) {
      return Math.floor(Math.random() * (max - min + 1)) + min
    },
  }
}
</script>
