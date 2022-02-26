<script>
	import Todo from "./components/Todo.svelte"
	let todos = [
		{id:1,done:false, text: "finish Svelte Tutorial"},
		{id:2,done:false, text: "build an app"},
		{id:3,done:false, text: "world domination"},
	]	
	function handleMessage (e){
		todos.forEach(todo=>{
			if(e.detail.id == todo.id){
				todo.text = e.detail.text
				todo.done = e.detail.done
				console.log('dale')
			}
			todos=todos
		})
	}
	function add(){
		todos = todos.concat({id: todos.length +1, done:false, text:""})
		console.log(todos)
	}
	function remove(){
		todos = todos.filter(t => !t.done);
	}
  function selectAll(){
    todos.forEach(todo=>{
      todo.done = !todo.done 
    })
    todos = todos
  }
</script>

<h1>Todos</h1>

{#each todos as todo}
	<Todo on:message={handleMessage} {todo}></Todo>
{/each}

<button on:click={add}>Add new</button>
<button on:click={remove}>Remove completed</button>
<!-- <button on:click={selectAll}>Toggle All</button> -->
{todos[0].text}
<style>
 :global(*){
    margin: 0;
    padding: 0;
    box-sizing: border-box;
 }
 main{
   background-color: #E5E5E5;
 }
</style>
