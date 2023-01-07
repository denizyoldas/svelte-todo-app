<script>
  import { createEventDispatcher } from 'svelte'
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
</div>

<style>
  .todo-item {
    display: flex;
    padding: 12px 16px;
    align-items: center;
    justify-content: space-between;
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
</style>
