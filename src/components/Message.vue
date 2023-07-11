<template>
  <div class="message">
    <b-alert v-model="showDismiss" variant="danger">
      <h4>{{message}}</h4>
    </b-alert>
  </div>
</template>

<script>
export default {
  props: {
    message: {
      type: String,
      required: true,
      default: 'default message'
    },
    showDismiss: {
      type: Boolean
    }
  }
}
</script>