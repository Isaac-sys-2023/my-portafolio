<script setup lang="ts">
import linkedin from '../icons/linkedIn/linkedin.vue';
import github from '../icons/github-mark/github.vue';
import email from '../icons/email/email.vue';

const today = new Date();
const year = today.getFullYear();
</script>

<template>
  <footer>
    <div class="net-icons">
      <a href="">
        <github />
      </a>
      <a href="">
        <linkedin />
      </a>
      <a href="">
        <email />
      </a>
    </div>
    <div>
      <p>Isaac Gutierrez Huarachi © {{ year }}</p>
    </div>
  </footer>
</template>

<style scoped>
.net-icons a {
  display: inline-flex;
  /* o inline-block */
  align-items: center;
  justify-content: center;
}

.net-icons a svg {
  display: block;
  /* elimina espacio fantasma */
}
</style>