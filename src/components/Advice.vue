<template>
  <div class="advice">
    <p>"{{ advice }}"</p>
  </div>
</template>

<script>
export default {
  props: ['advice']
}
</script>

<style>
.advice {
  padding: 0 22px 25px 22px;
}

p {
  color: hsl(193, 38%, 86%);
  letter-spacing: -0.5px;
  font-size: 1.75rem;
}
</style>