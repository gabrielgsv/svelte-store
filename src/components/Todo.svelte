<script>
  import TodoItem from "./TodoItem.svelte";

  import { tasks } from "../store";

  let task = "";

  const addTask = () => {
    tasks.update(() => [...$tasks, task])
    task = "";
  };
</script>

<form class="form" on:submit|preventDefault={addTask}>
  <input bind:value={task} type="text" class="form__field" />
  <button class="form__button">Add</button>
</form>

<TodoItem list={$tasks} />

<style>
  .form__field {
    border: 1px solid #dcdcdc;
    border-radius: 50px;
    color: #333333;
    font-family: Arial, sans-serif;
    font-size: 2rem;
    padding: 1rem 2rem;
    margin-right: 0.5rem;
    vertical-align: middle;
    width: 400px;
  }
  .form__field:focus {
    outline: none;
  }
  .form__button {
    background: #00cc99;
    border: none;
    border-radius: 10px;
    color: #ffffff;
    display: inline-block;
    font-family: Arial, sans-serif;
    padding: 1rem;
  }
  .form__button:focus {
    outline: none;
  }
  .form__button:hover {
    cursor: pointer;
  }
</style>
