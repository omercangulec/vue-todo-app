<template>
  <div class="flex flex-col items-center gap-8 pt-5">
    <button
      @click="showForm"
      class="bg-teal-600 py-1.5 mt-3 px-3 rounded-lg text-stone-100 hover:bg-teal-700 transition-all tracking-wider"
    >
      {{ !isAddNoteShow ? "&plus; Show" : "&minus; Hide" }} Note Form
    </button>
    <div v-if="isAddNoteShow" class="flex flex-col items-center w-80">
      <input
        class="rounded-t-lg border border-stone-200 px-3 py-1 text-sm transition-all duration-300 placeholder:text-stone-400 focus:outline-none focus:ring focus:ring-teal-400 md:px-4 md:py-2 w-full"
        v-model="todo"
        type="text"
      />
      <button
        class="bg-teal-600 py-1.5 px-3 rounded-b-lg text-stone-100 hover:bg-teal-700 transition-all tracking-wider w-full"
        @click="addTodo(todo, isCompleted)"
      >
        Add task
      </button>
    </div>

    <div v-if="todos.length" class="bg-teal-900 p-5 rounded-md mx-10 w-96">
      <ul class="grid grid-cols-1 gap-2">
        <li
          v-for="(todo, idx) in todos"
          :key="todo"
          class="bg-stone-200 text-stone-900 py-3 px-2 text-center rounded-md flex items-center justify-between gap-7"
        >
          <span
            :class="{
              'text-gray-500 line-through': todo.completed,
            }"
            >{{ todo.todo }}</span
          >
          <div class="flex items-center gap-1">
            <button
              @click="($event) => completed(idx)"
              class="bg-teal-600 text-stone-100 w-6 h-6 rounded-full"
            >
              &plus;
            </button>
            <button
              @click="($event) => deleteTodo(idx)"
              class="bg-red-600 text-stone-100 w-6 h-6 rounded-full"
            >
              &times;
            </button>
          </div>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      todo: "",
      todos: [],
      isAddNoteShow: false,
    };
  },

  methods: {
    addTodo(todo, completed) {
      if (this.todo.length > 0) {
        this.todos.push({
          todo: todo,
          completed: completed,
        });
        this.todo = "";
      }
    },

    deleteTodo(idx) {
      this.todos.splice(idx, 1);
    },

    completed(idx) {
      this.todos[idx].completed = !this.todos[idx].completed;
    },

    showForm() {
      this.isAddNoteShow = !this.isAddNoteShow;
    },
  },
};
</script>
