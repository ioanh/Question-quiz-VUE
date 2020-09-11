<template>
  <div>
    <b-nav>
      <b-nav-item disabled>Fancy Quiz App</b-nav-item>
      <b-nav-item disabled>Current {{ index + 1 }}/10</b-nav-item>
    </b-nav>
  </div>
</template>>
<script>
export default {
  props: {
    index: Number
  }
}
</script>