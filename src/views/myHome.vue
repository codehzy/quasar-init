<template>
  <div>
    <q-layout
      view="lHh lpr lFf"
      container
      style="height: 100vh"
      class="shadow-2 rounded-borders"
    >
      <q-header elevated>
        <q-toolbar>
          <q-btn
            flat
            round
            dense
            icon="menu"
            class="q-mr-sm"
            @click="toggleDraw"
          />
          <q-avatar>
            <img src="https://cn.vitejs.dev/logo.svg" @click="showUserInfo" />
          </q-avatar>

          <q-toolbar-title>应用</q-toolbar-title>

          <q-btn flat round dense icon="whatshot" />
        </q-toolbar>
      </q-header>
      <swiperView />

      <leftDrawer ref="LeftDrawer" />
      <rightDrawer ref="RightDrawer" />

      <userRegister />
    </q-layout>
  </div>
</template>

<script lang="ts" setup>
import { ref } from 'vue';
import userRegister from './components/register/userRegister.vue';
import leftDrawer from './components/drawer/leftDrawer.vue';
import rightDrawer from './components/drawer/rightDrawer.vue';
import swiperView from './components/swiper/swiperView.vue';

const LeftDrawer = ref();
const RightDrawer = ref();

const toggleDraw = () => {
  LeftDrawer.value.toggleLeftDraw();
};

const showUserInfo = () => {
  RightDrawer.value.showUserInfo();
};
</script>

<style lang="scss" scoped>
:deep(.q-page) {
  min-height: 300px !important;
}
</style>
