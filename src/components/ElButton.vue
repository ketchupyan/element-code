<template>
  <button
  :disabled="disabled" 
  @click="handleClick"
  class="el-button" 
  :class="[type?'el-button--'+type:'',
  size?'el-button--'+size:'',
  {
    'is-disabled':disabled,
    'is-loading' : loading,
    'is-plain' : plain
  }]">
    <i v-if="loading" class="el-icon-loading"></i>
    <i @click="handleInnerClicks" :class="'el-icon-'+icon" v-if="icon&&!loading"></i>
    <span v-if="$slots.default"></span>  <slot></slot>
  </button>
</template>
<script>
export default {
    props: {
      type: {
        type: String,
        default: 'default'
      },
      size: String,
      icon: {
        type: String,
        default: ''
      },
      disabled: Boolean,
      loading: Boolean,
      plain: Boolean,
      autofocus: Boolean,
    },
    methods: {
      handleClick (evt) {
      this.$emit('click', evt)
    },
    handleInnerClicks(evt) {
      this.$emit('click', evt)
    },
    }
}
</script>

<style>

</style>

