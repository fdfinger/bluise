<template>
  <div>
    <div class="flex">
      <div class="w-1/5 bg-gray-200">
        <ul class="py-4">
          <!-- <li class="pl-4 py-2 hover:bg-gray-300 cursor-pointer">
            <span class="text-gray-700">Menu Item 1</span>
            <ul class="pl-4 mt-2">
              <li class="pl-4 py-2 hover:bg-gray-300 cursor-pointer">
                <span class="text-gray-700">Submenu Item 1</span>
              </li>
              <li class="pl-4 py-2 hover:bg-gray-300 cursor-pointer">
                <span class="text-gray-700">Submenu Item 2</span>
              </li>
            </ul>
          </li> -->
          <li
            class="pl-4 py-2 hover:bg-gray-300 cursor-pointer"
            v-for="(item, index) in list"
            :key="index"
            :class="{ 'bg-gray-300': $route.path === item.path }"
          >
            <nuxt-link :to="item.path" class="text-gray-700">{{ item.title }}</nuxt-link>
          </li>
        </ul>
      </div>
      <div class="w-4/5 bg-white pl-2">
        <slot />
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { Vue } from 'nuxt-property-decorator';

export default class Tool extends Vue {
  list = [{ title: '风险计算', path: '/tool/risk' }];
}
</script>
