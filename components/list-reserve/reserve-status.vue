<template>
  <div>
    Status:
    <strong v-if="!status && !isFinished()" class="accent--text"
      >Reserved</strong
    >
    <strong v-else-if="!status && isFinished()" class="success--text"
      >Finished</strong
    >
    <strong v-else class="error--text">Cancelled</strong>
  </div>
</template>

<script>
export default {
  props: {
    status: Boolean,
    date: String,
  },

  methods: {
    isFinished() {
      const now = new Date()
      return this.date < now
    },
  },
}
</script>

<style></style>
