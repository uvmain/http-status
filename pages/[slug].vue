<script setup lang="ts">
import { useRoute } from 'vue-router'
import { getReasonPhrase } from 'http-status-codes';

const route = useRoute()
const statusCode = Number(`${route.params.slug}`)
const statusReason = getReasonPhrase(statusCode)

if (statusCode < 200 || statusCode > 299) {
  throw createError({
  statusCode: statusCode,
  statusMessage: statusReason
})
}
</script>

<template>
  <div>
    <h2>{{ statusCode }}</h2>
  </div>
</template>
