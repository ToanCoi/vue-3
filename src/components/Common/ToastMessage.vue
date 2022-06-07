<script setup>
import { ref, computed } from 'vue';
import Enumeration from '../../js/Enumeration.js';

const isShow = ref(true);

const props = defineProps({
  contentMsg: {
    type: String,
    required: true,
  },

  toastType: {
    type: Number,
    required: true,
  },
});

const getClassByType = computed(() => {
  switch (props.toastType) {
    case Enumeration.ToastType.Success:
        return 'toast__icon-success'
      break;
    case Enumeration.ToastType.Warning:
        return 'toast__icon-warning'
      break;
    case Enumeration.ToastType.Danger:
        return 'toast__icon-danger'
      break;
  }
});
</script>

<template>
  <transition name="slide" v-show="isShow">
    <div class="toast">
      <div class="toast__icon">
        <div :class="getClassByType"></div>
      </div>
      <div class="toast__content">{{ contentMsg }}</div>
      <div class="toast__cancel" @click="isShow = false">
        <div class="toast__icon-cancel"></div>
      </div>
    </div>
  </transition>
</template>

<style scoped>
@import url('../../assets/css/components/toast-message.css');

.slide-leave-active,
.slide-enter-active {
  transition: all 0.3s;
}

.slide-enter,
.slide-leave-to {
  transform: translateX(100%);
  opacity: 0;
}
</style>
