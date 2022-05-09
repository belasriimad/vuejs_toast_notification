<template>
  <div class="toast-header text-white" :class="toast.bgColor">
    <i :class="toast.icon"></i>
    <strong class="me-auto">{{toast.title}}</strong>
    <small>{{toast.time}}</small>
    <button type="button" class="btn-close btn-close-white"
      @click="$emit('hide')"></button>
  </div>
</template>

<script>
export default {
  emits: ['hide'],
  props:{
    toast: {
      type: Object,
      default: function () {
        return { 
          toast: {
            icon: '',
            title: '',
            time: '',
            message: '',
            bgColor: '',
          },
        }
      }
    }
  }
}
</script>
