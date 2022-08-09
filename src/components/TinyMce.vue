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
  props: {
    apiKey: String,
    settings: Object,
  }
}
</script>
