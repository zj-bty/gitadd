<template>
  <div class="footer">
    <p> {{footers}}</p>
  </div>
</template>
<script>
export default {
  name: 'footerName',
  props: {
    footers: {
      type: String,
      default: '底部'
    }
  },
  data () {
    return {}
  }
}
</script>
