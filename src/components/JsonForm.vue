<template>
  <div id="jsonForm">
    <form>
      <h3>Json</h3>
      <textarea class="u-full-width input-form" v-model="text"></textarea>
      <button type="button" @click="update">convert Json to Toml</button>
    </form>
  </div>
</template>

<script>
export default {
  name: 'JsonForm',
  props: ['commonData'],
  data: function () {
    return {
      text: this.commonData
    }
  },
  methods: {
    update () {
      try {
        this.$emit('update', JSON.parse(this.text))
      } catch (error) {
        alert(error)
      }
    },
    applyData (obj) {
      this.text = JSON.stringify(obj, null, 2)
    }
  }
}
</script>
