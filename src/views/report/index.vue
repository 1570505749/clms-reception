<template>
  <div>
    <a-date-picker :default-value="moment(data, dateFormat)" disabled />
  </div>
</template>
<script>
import moment from 'moment'
export default {
  data() {
    this.dateFormat = 'YYYY-MM-DD'
    return {
      data: new Date()
    }
  },
  methods: {
    moment
  }
}
</script>
