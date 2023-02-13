<script>
  import { createEventDispatcher } from 'svelte'
  import IoMdTrash from 'svelte-icons/io/IoMdTrash.svelte'

  export let isDone = false;
  export let text = "Todo Item"


  const dispatch = createEventDispatcher()

  function isDoneHandle() {
    isDone = !isDone;
  }
</script>


<div class="todo-item">
  <div>
    <input type="checkbox" checked={isDone} name="isDone" on:change={isDoneHandle} />
  </div>
  <div class="content">
    <h3 class:is-done={isDone}>{text}</h3>
  </div> 

  <div class="action">
    <button on:click={() => dispatch('delete')}>
      <IoMdTrash />
    </button>
  </div>
</div>

<style>
  .todo-item {
    display: flex;
    padding: 20px;
    align-items: center;
    justify-content: space-between;
    background-color: #DBE2EF;
    border-radius: 5px;
  }

  .content {
    display: flex;
    align-items: center;
    justify-content: flex-end;
  }


  .is-done {
    text-decoration: line-through;  
  }


  input[type="checkbox"] {
    width: 24px;
    height: 24px;
    color: green;
  }

  .action {
    display: flex;
    align-items: center;
    justify-content: flex-end;
  }

  .action button {
    border: none;
    background-color: transparent;
    cursor: pointer;
    width: 48px;
    height: 48px;
  }

  .action button:hover {
    color: red;
  }
</style>
