<script>
  import TodoItem from './todo-item.svelte'

  let TODO_LIST = [
  {isDone: false, text: 'Clean the card'},
  {isDone: true, text: 'Go to do gym'},
  ]

  let newTodoInpt = '';

  function addNewToDo() {
    TODO_LIST = [...TODO_LIST, {isDone: false, text: newTodoInpt}]
    newTodoInpt = '';
  }


  function addNewTodoKeydown(e) {
    if(e.keyCode === 13) {
      addNewToDo()  
    }
  }

  function deleteTodoItem(i) {
    TODO_LIST = TODO_LIST.filter((_, index) => index !== i)
  }
</script>

<div class="todo-card">
  <h1>ToDo App</h1>
  <div class="input">
    <input type="text" placeholder="some text" bind:value={newTodoInpt} on:keydown={addNewTodoKeydown} />
    <button on:click={addNewToDo}>+</button>
  </div>

  <div class="todo-list">
    {#if TODO_LIST.length === 0}
      <h3>There is no todo item</h3>
    {/if}

    {#each TODO_LIST as todo, i}
    <TodoItem {...todo} on:delete={() => {deleteTodoItem(i)}} />
    {/each}
  </div>
</div>



<style>
  .todo-card {
    padding: 16px 24px;
    box-shadow: rgba(17, 12, 46, 0.15) 0px 48px 100px 0px;
    border: 1px solid black;
    border-radius: 16px;
    width: 600px;
    height: 450px;
    background-color: #F9F7F7;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
  }

  .todo-list {
    margin-top: 12px;
    padding-top: 16px;
    width: 500px;
    height: 400px;
    overflow-y: auto;
    border-top: 1px solid rgba(0, 0, 0, 0.5);
    display: flex;
    flex-direction: column;
    gap: 30px;
  }

  .input {
    display: flex;
    justify-content: center;
  }

  .input input {
    background-color: #DBE2EF;
    border: 1px solid rgba(177, 177, 177, 0.4);
    border-radius: 5px 0 0 5px;
    padding: 10px;
    width: 300px;
  }


  .input button {
    background-color: #3F72AF;
    border: none;
    color: white;
    font-size: 36px;
    padding: 4px 10px;
    border-radius: 0 5px 5px 0;
    color: #fff;
    font-weight: 500;
    width: 100px;
    margin-left: -2px;
    cursor: pointer;
  }

  .input button:hover {
    opacity: 0.7;
  }
</style>
