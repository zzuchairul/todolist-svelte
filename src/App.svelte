<script>
  let todos = ["Wake Up", "Eat"];
  let newTodo = "";
  let history = ["Menambahkan Eat", "Menambahkan Wak Up"];

  function addTodo(item) {
    todos = [...todos, item];
    newTodo = "";
    addHistory(true, item);
  }

  function removeTodo(item) {
    todos = todos.filter((elem) => elem !== item);
    addHistory(false, item);
  }

  function addHistory(status, item) {
    let pesan = status ? `Menambahkan ${item}` : `${item} selesai`;
    history = [pesan, ...history];
  }
</script>

<div class="row">
  <div class="todo-list">
    <label>
      <input type="text" bind:value={newTodo} placeholder="what will you do" />
      <button on:click={() => addTodo(newTodo)}>Add</button>
    </label>

    <ul>
      {#each todos as todo}
        <li>
          {todo} <button on:click={() => removeTodo(todo)}>Done</button>
        </li>
      {/each}
    </ul>
  </div>

  <div class="history">
    <h3>History</h3>
    <ol>
      {#each history as hist}
        <li>
          {hist}
        </li>
      {/each}
    </ol>
  </div>
</div>

<style>
  .row {
    display: flex;
    justify-content: space-evenly;
  }

  .todo-list {
    border: 1px solid;
    width: 40%;
    height: 80vh;
  }

  .history {
    border: 1px solid;
    width: 40%;
    height: 80vh;
  }

  .history h3 {
    display: flex;
    justify-content: center;
  }
</style>
