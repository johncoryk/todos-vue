<template>
  <div id="app">
    <h1 class="title">Vue Todos</h1>
    <div class="container">
      <TodoList />
    </div>
    <section class="footer-info">
      <p>Double click to edit a todo, you know the rest 😎</p>
      <p>
        Made with ♥️ by
        <a href="https://github.com/johncoryk">Cory Kelley</a>
      </p>
    </section>
  </div>
</template>

<script>
import TodoList from './components/TodoList.vue';

export default {
  name: 'App',
  components: {
    TodoList,
  },
};
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  font-size: 1.7rem;
  background-color: #333;
}

.container {
  max-width: 700px;
  width: 95vw;
  margin: 3rem auto 2rem;
  padding: 2rem;
  background-color: #eee;
  -webkit-box-shadow: 7px 7px 15px -8px rgba(0, 0, 0, 0.62);
  -moz-box-shadow: 7px 7px 15px -8px rgba(0, 0, 0, 0.62);
  box-shadow: 7px 7px 15px -8px rgba(0, 0, 0, 0.62);
}

.title {
  font-size: 7rem;
  font-weight: bold;
  color: #eee;
  text-align: center;
  margin-top: 5rem;
}

.footer-info {
  font-size: 0.95rem;
  color: #eee;
  text-align: center;
}

.footer-info a {
  color: #bbb;
}

.footer-info a:hover {
  color: #f26e50;
}
</style>
