<script setup lang="ts">
import { useRoute } from 'vue-router'
import { getReasonPhrase } from 'http-status-codes';

const route = useRoute()
const statusCode = Number(`${route.params.slug}`)
const statusReason = getReasonPhrase(statusCode)

throw createError({
  statusCode: statusCode,
  statusMessage: statusReason
})
</script>

<template>
  <div>
    <h2>{{ statusCode }}: {{ statusReason }}</h2>
  </div>
</template>
