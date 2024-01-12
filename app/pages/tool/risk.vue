<template>
  <section class="tool">
    <ToolLayout>
      <form class="w-full max-w-sm">
        <label for="amount" id="amount-label" class="md:flex md:items-center mb-6">
          <div class="md:w-1/3">
            <span class="block text-gray-500 font-bold md:text-right mb-1 md:mb-0 pr-4">
              本金
            </span>
          </div>
          <div class="md:w-2/3">
            <input
              type="number"
              id="amount"
              min="0"
              aria-labelledby="amount-label"
              v-model="form.amount"
              placeholder="本金"
              class="bg-gray-200 appearance-none border-2 border-gray-200 rounded w-full py-2 px-4 text-gray-700 leading-tight focus:outline-none focus:bg-white focus:border-purple-500"
            />
          </div>
        </label>
        <label for="current" id="current-label" class="md:flex md:items-center mb-6">
          <div class="md:w-1/3">
            <span class="block text-gray-500 font-bold md:text-right mb-1 md:mb-0 pr-4">
              当前价位
            </span>
          </div>
          <div class="md:w-2/3">
            <input
              type="number"
              id="current"
              min="0"
              aria-labelledby="current-label"
              v-model="form.current"
              placeholder="当前价位"
              class="bg-gray-200 appearance-none border-2 border-gray-200 rounded w-full py-2 px-4 text-gray-700 leading-tight focus:outline-none focus:bg-white focus:border-purple-500"
            />
          </div>
        </label>
        <label
          for="stopLossPercentage"
          id="stopLossPercentage-label"
          class="md:flex md:items-center mb-6"
        >
          <div class="md:w-1/3">
            <span class="block text-gray-500 font-bold md:text-right mb-1 md:mb-0 pr-4">
              止损百分比
            </span>
          </div>
          <div class="md:w-2/3">
            <input
              type="range"
              id="stopLossPercentage"
              min="0"
              aria-labelledby="stopLossPercentage-label"
              v-model="form.stopLossPercentage"
              placeholder="止损百分比"
              class="w-full h-4 bg-gray-200 rounded-lg appearance-none focus:outline-none focus:bg-blue-300 focus:ring-2 focus:ring-blue-500"
            />
          </div>
        </label>
        <p class="text-red-500 text-xs italic text-right">止损比{{ form.stopLossPercentage }} %</p>
        <p>
          <span>风险值:</span>
          {{ risk }}
        </p>
        <p>
          <span>止损位:</span>
          {{ stopLoss }}
        </p>
      </form>
    </ToolLayout>
  </section>
</template>

<script lang="ts">
import { Component, Vue } from 'nuxt-property-decorator';
import ToolLayout from '@/components/tool/tool-layout.vue';

@Component({
  components: {
    ToolLayout,
  },
  // Called to know which transition to apply
  transition() {
    return 'slide-left';
  },
})
export default class Tool extends Vue {
  form = {
    amount: 1000, // 本金
    current: 1, // 当前价位
    stopLossPercentage: 2, // 止损
    risk: 0, // 风险
  };

  get risk(): string {
    const { current, amount, stopLossPercentage } = this.form;
    return (((amount / current) * stopLossPercentage) / 100).toFixed(2);
  }

  get stopLoss(): string {
    const { current, stopLossPercentage } = this.form;
    return ((current * (100 - stopLossPercentage)) / 100).toFixed(2);
  }

  mathRisk(): void {
    const { current, amount, stopLossPercentage } = this.form;
    this.form.risk = ((amount / current) * stopLossPercentage) / 100;
  }
}
</script>
