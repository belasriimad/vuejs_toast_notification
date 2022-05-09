<template>
  <div class="container my-4">
    <div class="row">
      <div class="col-md-12 d-flex justify-content-start">
        <button class="btn btn-sm btn-success me-2"
          @click="successToast">Success</button>
        <button class="btn btn-sm btn-danger me-2"
          @click="dangerToast">Danger</button>
        <button class="btn btn-sm btn-warning me-2"
          @click="warningToast">Warning</button>
        <button class="btn btn-sm btn-info me-2"
          @click="infoToast">Info</button>
      </div>
    </div>
    <div class="toast-container position-absolute" :class="position">
      <div class="toast" :class="show">
        <ToastHeader 
          :toast="toast"
          @hide="hideToast"
        />
        <ToastBody :message="toast.message" />
      </div>
    </div>
  </div>
</template>

<script>
import ToastHeader from './ToastHeader.vue';
import ToastBody from './ToastBody.vue';
import moment from 'moment';

export default {
  data() {
    return {
      toast: {
        icon: '',
        title: '',
        time: '',
        message: '',
        bgColor: '',
      },
      show: '',
      position: '',
      timeout: null
    }
  },
  components:{
    ToastHeader,
    ToastBody
  },
  watch: {
    show() {
      if(this.timeout){
        clearTimeout(this.timeout);
      }
      this.timeout = setTimeout(() => {
        this.show = '';
        this.position = '';
      },3000);
    }
  },
  methods:{
    successToast(){
      this.show = 'show';
      this.position = 'top-0 end-0';
      this.toast = {
        icon: 'fa-solid fa-check me-2',
        time: moment().fromNow(),
        title: 'success',
        bgColor: 'bg-success',
        message: 'Message sent successfully'
      }
    },
    dangerToast(){
      this.show = 'show';
      this.position = 'bottom-0 start-0';
      this.toast = {
        icon: 'fa-solid fa-bolt me-2',
        time: moment().fromNow(),
        title: 'danger',
        bgColor: 'bg-danger',
        message: 'Error try later again'
      }
    },
    warningToast(){
      this.show = 'show';
      this.position = 'top-0 start-50 translate-middle-x';
      this.toast = {
        icon: 'fa-solid fa-exclamation me-2',
        time: moment().fromNow(),
        title: 'warning',
        bgColor: 'bg-warning',
        message: 'Warning check your info'
      }
    },
    infoToast(){
      this.show = 'show';
      this.position = 'bottom-0 end-0';
      this.toast = {
        icon: 'fa-solid fa-info me-2',
        time: moment().fromNow(),
        title: 'info',
        bgColor: 'bg-info',
        message: 'We are away for 2 days'
      }
    },
    hideToast(){
      this.show = '';
      this.position = '';
    },
  }
}
</script>
