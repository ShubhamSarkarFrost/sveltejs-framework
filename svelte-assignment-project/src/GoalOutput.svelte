<script>
  export let goal = '';
</script>

<h1 class:red={goal.includes('!')}>
  {goal}
</h1>

<style>
  h1 {
    margin-top: 0.5rem;
  }

  .red {
    color: red;
  }
</style>
