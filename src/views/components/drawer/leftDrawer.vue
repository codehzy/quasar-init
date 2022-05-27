<template>
  <div>
    <!-- 左侧抽屉 -->
    <q-drawer
      side="left"
      v-model="drawerLeft"
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

const drawerLeft = ref(false);

const toggleLeftDraw = () => {
  drawerLeft.value = !drawerLeft.value;
};

defineExpose({
  toggleLeftDraw,
});
</script>

<style lang="scss" scoped></style>
