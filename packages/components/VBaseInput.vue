<template>
  <van-field
    v-bind="$attrs"
    :value="value"
    v-on="$listeners"
  >
    <template #button>
      <slot />
    </template>
  </van-field>
</template>

<script>
import { Field } from 'vant'
export default {
  name: 'VBaseInput',

  components: {
    [Field.name]: Field
  },

  props: {
    value: {
      type: String,
      default: ''
    }
  }
}
</script>
