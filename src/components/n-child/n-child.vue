<template>
  <view>
	  <view v-for="text in list" :key="text">{{text}}</view>
  </view>
</template>

<script setup lang="ts">
import { getCurrentInstance } from 'vue';

const instance = getCurrentInstance();

const list: string[] = [];

function print(ins: any) {
  const type = ins?.vnode?.type;
  const name = type?.name ?? type?.__name;
  console.log(`child vnode name =`, name);
  list.push(name);

  if (ins?.parent) print(ins?.parent);
}

print(instance);
	

</script>

<script lang="ts">
export default {
  name: 'n-child',
};
</script>
