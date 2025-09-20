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
      <a href="https://github.com/Isaac-sys-2023" target="_blank" rel="noopener noreferrer">
        <github />
      </a>
      <a href="https://www.linkedin.com/in/isaac-gutierrez-huarachi/" target="_blank" rel="noopener noreferrer">
        <linkedin />
      </a>
      <a href="mailto:gutierrezhuarachiisaac@gmail.com">
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