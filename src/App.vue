<template>
  <header class="">
    <HeaderApp />
  </header>
  <main class="bg-gray-800 h-screen flex flex-col items-center">
    <NoteForm />
  </main>
</template>

<script>
import HeaderApp from "./components/HeaderApp.vue";
import NoteForm from "./components/NoteForm.vue";

export default {
  components: { HeaderApp, NoteForm },
};
</script>
