<template>
  <div class="w-full h-screen">
    <div class="grid grid-cols-3 h-1/2">
      <div class="h-full m-4">
        <button @click="createMustache">Render</button>
        <textarea
          id="editor"
          class="w-full h-full border-2 border-indigo-600"
          name=""
          cols="30"
          rows="10"
        ></textarea>
      </div>
      <div class="h-full m-4 text-center">
        <h3>JSON</h3>
        <textarea
          id="editorJSON"
          class="w-full h-full border-2 border-indigo-600"
          name=""
          cols="30"
          rows="10"
          :value="jsonExample"
        ></textarea>
      </div>
      <div class="h-full m-4 text-center">
        <h3>Result</h3>
        <div id="result"></div>
      </div>
    </div>
  </div>
</template>
<script>
import Mustache from 'mustache'
export default {
  name: 'MustacheEditor',
  data() {
    return {
      jsonExample: `{
  "aaa": "Colors",
  "items": [
      {"name": "red", "first": true, "url": "#Red"},
      {"name": "green", "link": true, "url": "#Green"},
      {"name": "blue", "link": true, "url": "#Blue"}
  ],
  "empty": false
}`,
    }
  },
  mounted() {
    const view = {
      title: 'Joe',
      calc: function () {
        return 2 + 4
      },
    }

    const output = Mustache.render('{{title}} spends {{calc}}', view)
    console.log(output)
  },
  methods: {
    renderMustage(template, data) {
      console.log(Mustache.parse(template))

      return Mustache.render(template, data)
    },
    createMustache() {
      const code = document.getElementById('editor').value
      const values = document.getElementById('editorJSON').value
      console.log(values)
      document.getElementById('result').innerHTML = this.renderMustage(
        code,
        JSON.parse(values)
      )
    },
  },
}
</script>
