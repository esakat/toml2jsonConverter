<template>
  <div id="app">
    <div class="row">
      <h2>Toml ⇆ Json Converter</h2>
    </div>
    <div id=description>
      <p>
        Toml ⇆ Json Converter is a simple online tool.<br>
        This tool can convert Json to Toml, Toml to Json.<br>
        All processings are exected in javascript, so the your data is never sent to an external server.
      </p>
    </div>
    <div class="row">
      <tomlForm class="six columns" :commonData="tomlText" @update="updateData($event)" ref="toml"></tomlForm>
      <jsonForm class="six columns" :commonData="jsonText" @update="updateData($event)" ref="json"></jsonForm>
    </div>
    <hr>
    <div id=licence>
      <p>
        Copyright 2019 esakat.
      </p>
    </div>
  </div>
</template>

<script>
import TOML from '@iarna/toml'

import jsonForm from './components/JsonForm'
import tomlForm from './components/TomlForm'

export default {
  name: 'App',
  components: {
    tomlForm,
    jsonForm
  },
  data: () => ({
    commonData: {
      'title': 'Toml to Json to Yaml',
      'repository': {
        'url': 'https://github.com/esakat/toml2jsonConverter',
        'owner': 'esakat'
      }
    },
    jsonText: '',
    tomlText: ''
  }),
  methods: {
    updateData (obj) {
      this.$refs.toml.applyData(obj)
      this.$refs.json.applyData(obj)
    }
  },
  created () {
    this.jsonText = JSON.stringify(this.commonData, null, 2)
    this.tomlText = TOML.stringify(this.commonData)
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  max-width: 800px;
  margin-right: auto;
  margin-left : auto;
}

.input-form {
  min-height: 20em;
}
</style>
