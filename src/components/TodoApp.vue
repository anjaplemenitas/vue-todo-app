<template>
  <div class="container mx-auto">
    <h2 class="text-center mt-5 mb-5">My Vue Todo App</h2>

    <!-- input -->
    <div class="text-center">
      <input
        type="text"
        placeholder="Enter task"
        class="shadow appearance-none border rounded w-6/12 py-2 px-3 text-grey-darker"
      />
      <button
        class="bg-gray-300 hover:bg-gray-400 text-gray-800 font-bold py-2 px-4 rounded inline-flex items-center"
      >
        Submit
      </button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String,
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped></style>
