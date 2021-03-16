<script>
export default {
  name: 'adjustForTimezone',
  components: {},
  data: () => ({
      currentTime: ''
  }),
  computed: {},
  mounted() {
        this.calculateTime()
  },
  methods: {
      adjustForTimezone(date) {
            let timeOffsetInMS = date.getTimezoneOffset() * 60000;
            date.setTime(date.getTime() - timeOffsetInMS);
            return date
      },
      calculateTime() {
            setInterval(() => {
                  this.currentTime = this.adjustForTimezone(new Date())
            }, 1000)
      }
  }
}
</script>

<template>
    <h1>{{ this.currentTime }}</h1>
</template>

<style scoped>
</style>