<template>
  <div class="container mx-auto">
    <h2 class="text-center mt-5 mb-5">My Vue Todo App</h2>

    <!-- input -->
    <div class="text-center">
      <input
        v-model="task"
        type="text"
        placeholder="Enter task"
        class="shadow appearance-none border rounded w-6/12 py-2 px-3 text-grey-darker"
      />
      <button
        @click="submitTask"
        class="bg-gray-300 hover:bg-gray-400 text-gray-800 font-bold py-2 px-4 rounded inline-flex items-center"
      >
        Submit
      </button>
    </div>

    <!-- task table -->
    <div class="container flex justify-center mx-auto mt-5">
      <div class="flex flex-col">
        <div class="w-full">
          <div class="border-b border-gray-200 shadow">
            <table class="divide-y divide-gray-300">
              <thead class="bg-gray-50">
                <tr>
                  <th class="px-6 py-2 text-xs text-gray-500">
                    Task
                  </th>
                  <th class="px-6 py-2 text-xs text-gray-500">
                    Status
                  </th>
                  <th class="px-6 py-2 text-xs text-gray-500">
                    #
                  </th>
                  <th class="px-6 py-2 text-xs text-gray-500">
                    #
                  </th>
                </tr>
              </thead>
              <tbody class="bg-white divide-y divide-gray-300">
                <tr
                  class="whitespace-nowrap"
                  v-for="(task, index) in tasks"
                  :key="index"
                >
                  <td class="px-6 py-4">
                    <div class="text-sm text-gray-900">
                      {{ task.name }}
                    </div>
                  </td>
                  <td class="px-6 py-4">
                    <div class="text-sm text-gray-500">{{ task.status }}</div>
                  </td>

                  <td class="px-6 py-4">
                    <div
                      @click="editTask(index)"
                      class="px-4 py-1 text-sm text-black-600 bg-blue-100 rounded-full"
                    >
                      <span class="fa fa-pen"></span>
                    </div>
                  </td>
                  <td class="px-6 py-4">
                    <div
                      @click="deleteTask(index)"
                      class="px-4 py-1 text-sm text-black-400 bg-red-100 rounded-full"
                    >
                      <span class="fa fa-trash"></span>
                    </div>
                  </td>
                </tr>
              </tbody>
            </table>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String,
  },
  data() {
    return {
      task: '',
      editedTask: null,
      tasks: [
        { name: 'Learn Css', status: 'to-do' },
        { name: 'bom', status: 'to-do' },
      ],
    }
  },
  methods: {
    submitTask() {
      if (this.task.lenght === 0) return

      if (this.editedTask === null) {
        this.tasks.push({ name: this.task, status: 'to-do' })
      } else {
        this.tasks[this.editedTask].name = this.task
        this.editedTask = null
      }
      this.task = ''
    },

    deleteTask(index) {
      this.tasks.splice(index, 1)
    },

    editTask(index) {
      this.task = this.tasks[index].name
      this.editedTask = index
    },
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped></style>
