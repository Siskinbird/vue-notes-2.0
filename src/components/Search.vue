<template>
<div class="search col-11">
  <b-input-group size="sm" class="mb-2">
    <b-input-group-prepend is-text>
      <b-icon icon="search"></b-icon>
    </b-input-group-prepend>
    <b-form-input type="search" :placeholder="placeholder" v-model="search">
      Ghbdtn
    </b-form-input>
  </b-input-group>
</div>
</template>

<script>
export default {
  props: {
    value: {
      type: String,
      require: true
    },
    placeholder: {
      type: String,
      default: 'Search'
    }
  },
  data() {
    return {search: this.value}
  },
  watch: {
    search(value) {
      this.$emit('search', value)
    }
  }
}
</script>
<style lang="scss" scoped>
  .search {
    margin-right: auto;
    display: flex;
    align-items: center;
    margin-top: 10px;
    margin-left: -15px;
  }
</style>