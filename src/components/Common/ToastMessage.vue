<script setup>
let isShow = ref(true)
</script>

<template>
    <transition name="slide" v-show="isShow">
        <div class="toast">
            <div class="toast__icon danger">
                <div class="toast__icon-danger"></div>
            </div>
            <div class="toast__content">
                    dfsdf
            </div>
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