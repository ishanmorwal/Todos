<script>
    let todos = [];
    function add(){
        todos = todos.concat({done: false, text:''});
    }
    function clear(){
        todos = todos.filter(t=>!t.done);
    }
    
    $: remaining = todos.filter(t => !t.done).length;
  
</script>


<div class="container">
    <h1 class="title">
        Todos
    </h1>
    {#each todos as todo}
    <div class:done={todo.done}>
        <input 
        type = checkbox
        bind:checked = {todo.done}
        >
        <input placeholder ="What is to be done?" bind:value ={todo.text}>
    </div>
    {/each}
    
    <p>{remaining} remaining</p>

    <button on:click ={add}>Add task</button>
    <button on:click ={clear}>Clear tasks</button>
</div>


<style>
    
</style>