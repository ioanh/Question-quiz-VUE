<template>
  <div>
    <b-jumbotron>  
      <template v-slot:lead v-b>
        {{ currentQuestion.question }}
      </template>
      <hr class="my-4">
      <p>
        List of answers
      </p>
  
      <b-button variant="primary">Submit</b-button>
      <b-button @click="next" variant="success">Next question</b-button>
    </b-jumbotron>
  </div>
</template>>
<script>
export default {
  props: {
    currentQuestion: Object,
    next: Function
  },
  mounted() {
    console.log(this.currentQuestion)
  }
}
</script>