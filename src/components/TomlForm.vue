<template>
  <div id="tomlForm">
    <form>
      <h3>Toml</h3>
      <textarea class="u-full-width input-form" v-model="text"></textarea>
      <button type="button" @click="update">convert Toml to Json</button>
    </form>
  </div>
</template>

<script>
import TOML from '@iarna/toml'

export default {
  name: 'TomlForm',
  props: ['commonData'],
  data: function () {
    return {
      text: this.commonData
    }
  },
  methods: {
    update () {
      try {
        this.$emit('update', TOML.parse(this.text))
      } catch (error) {
        alert(error)
      }
    },
    applyData: function (obj) {
      this.text = TOML.stringify(obj)
    }
  }
}
</script>
