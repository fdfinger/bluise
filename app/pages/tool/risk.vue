<template>
  <section class="tool">
    <ToolLayout>
      测试
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
export default class Tool extends Vue {}
</script>
