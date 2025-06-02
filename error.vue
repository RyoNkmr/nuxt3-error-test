<script setup lang="ts">
import type { NuxtError } from '#app'

const props = defineProps<{ error: NuxtError }>()

const message = computed(() => {
  const message = props.error.message ?? props.error.statusMessage;
  if (message != null && message !== '') {
    return message;
  }
  switch (props.error?.statusCode) {
    case 401:
      return 'ログインしていません。ログインしてください。'
    case 404:
      return 'お探しのページは見つかりませんでした'
    case 403: // 403も想定外？
    case 500:
      return '想定外のエラーが発生しました'
    default:
      return 'こちらのページは表示することが出来ません'
  }
})

const prettify = (error: NuxtError) => {
  const entries = (Object.keys(error) as unknown as Array<keyof typeof error>).map(key => `${key}: ${JSON.stringify(error[key])}`)
  return `{\n${entries.map(entry => `  ${entry}`).join('\n')}\n}`
}
</script>

<template>
  <!--メンテナンス-->
  <div :class="$style.maintenance" v-if="error.statusCode === 503" v-html="error.data" />
  <NuxtLayout v-else>
    <h1>error page</h1>
    <div>
      {{ message }}
    </div>
    <DevOnly>
      <h2 :class="$style.debug__title">Error</h2>
      <pre :class="$style.debug__body">{{ prettify(props.error) }}</pre>
    </DevOnly>
  </NuxtLayout>
</template>

<style lang="scss" module>
.maintenance {
  padding: 16px;

  h1 {
    margin-bottom: 1em;
  }

  p {
    line-height: 1.5;
  }

  a {
    color: initial;
  }
}

.debug {
  &__title {
    color: #333;
    font-size: 16px;
    text-align: center;
  }

  &__body {
    background: #333;
    color: #3a5;
    font-size: 12px;
    padding: 10px;
    line-height: 1.2;
    word-break: break-all;
    white-space: pre-wrap;
    border-radius: 4px;
    margin: 10px;
  }
}
</style>