<template>
  <div>
    <b-nav>
      <b-nav-item disabled>Fancy Quiz App</b-nav-item>
      <b-nav-item disabled>Current {{ numCorrect }} / {{ numTotal }}</b-nav-item>
    </b-nav>
  </div>
</template>>
<script>
export default {
  props: {
    numCorrect: Number,
    numTotal: Number
  }
}
</script>