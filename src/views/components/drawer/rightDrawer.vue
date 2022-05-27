<template>
  <div>
    <!-- 右侧抽屉 -->
    <q-drawer
      side="right"
      v-model="drawerRight"
      :width="200"
      :breakpoint="700"
      bordered
      content-class="bg-grey-3"
    >
      <q-scroll-area class="fit">
        <div class="q-pa-sm">
          <div v-for="n in 50" :key="n">Drawer {{ n }} / 50</div>
        </div>
      </q-scroll-area>
    </q-drawer>
  </div>
</template>

<script lang="ts" setup>
import { ref } from 'vue';

const drawerRight = ref(false);
const showUserInfo = () => {
  drawerRight.value = !drawerRight.value;
};

defineExpose({
  showUserInfo,
});
</script>

<style lang="scss" scoped></style>
