<script>
	import {createEventDispatcher} from "svelte"
	let dispatch = createEventDispatcher()
	
	function handleChange() {
			dispatch("message",{
				todo
			})
	}
	export let todo = {id: 1, done:false, text:"Has zero todos" }; 
</script>

<div class:done ={todo.done}>
	<input type=checkbox bind:checked={todo.done}>
	<input type=text on:change={handleChange} bind:value={todo.text} placeholder="What you have to do">
</div>


