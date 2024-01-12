<template>
  <section class="tool">
    <div class="py-24 md:py-36 mx-auto flex flex-wrap flex-col md:flex-row items-center">
      工具主页
    </div>
  </section>
</template>

<script lang="ts">
import { Component, Vue } from 'nuxt-property-decorator';

@Component({
  // Called to know which transition to apply
  transition() {
    return 'slide-left';
  },
})
export default class Tool extends Vue {
  list = [];
}
</script>
