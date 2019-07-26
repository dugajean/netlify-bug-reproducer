<template>
  <div>
    <form name="myform" data-netlify="true" @submit.prevent="handleSubmit">
      <input type="text" name="name" v-model="name">
      <input type="text" name="email" v-model="email">
      <button type="submit">Submit</button>
      <div v-if="sent">Sent!</div>
    </form>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  data() {
    return {
      name: '',
      email: '',
      sent: false
    }
  },
  methods: {
    handleSubmit() {
      const formData = `form-name=myform&name=${this.name}&email=${this.email}`

      const axiosConfig = {
          header: { 'Content-Type': 'application/x-www-form-urlencoded' }
      }

      axios.post(event.target.action, formData, axiosConfig)
          .then(() => { this.sent = true })
          .catch(() => { this.sent = false })
    }
  }
}
</script>
