<template>
  <div class="v-form__input-wrapper">
    <v-base-input
      :value="value"
      :placeholder="formModel.rules.placeholder"
      readonly
      :disabled="disabled"
      @touchstart.native.stop="hanldeKeyboardShow"
    />
    <van-number-keyboard
      v-model="numberKeyboardValue"
      :show="isShow"
      :title="formModel.rules.title"
      :theme="formModel.rules.theme"
      :maxlength="formModel.rules.maxlength"
      :z-index="formModel.rules.zIndex"
      :extra-key="formModel.rules.extraKey"
      :close-button-text="formModel.rules.closeButtonText"
      :delete-button-text="formModel.rules.deleteButtonText"
      :close-button-loading="formModel.rules.closeButtonLoading"
      :show-delete-key="formModel.rules.showDeleteKey"
      @blur="isShow = false"
      @hide="e__change"
    />
  </div>
</template>

<script>
import VBaseInput from '../components/VBaseInput.vue'
import { NumberKeyboard } from 'vant'
import formItemBase from '../mixins/formItemBase'

export default {
  name: 'VNumberKeyboard',

  components: {
    [VBaseInput.name]: VBaseInput,
    [NumberKeyboard.name]: NumberKeyboard
  },

  mixins: [formItemBase],

  props: {
    value: {
      type: String,
      default: ''
    }
  },

  data() {
    return {
      isShow: false
    }
  },

  computed: {
    numberKeyboardValue: {
      get() {
        return this.value
      },
      set(val) {
        this.innerValue = val
        this.e__input(val)
      }
    }
  },

  methods: {
    hanldeKeyboardShow(event) {
      if (!this.disabled) this.isShow = true
      window.scrollTo({
        top: event.touches[0].pageY - window.innerHeight / 2,
        left: 0,
        behavior: 'smooth'
      })
    }
  }
}
</script>
