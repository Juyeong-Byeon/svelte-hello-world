<script>
    import Todo from './Todo.svelte';
    let inputText='';
    let todos=[];

    function onClickAddTodo(event){
        if(inputText){
            todos=[
            ...todos,
            {
                id:Date.now(),
                todo:inputText,
            }
        ]
        inputText='';
        }
    }

    function onClickDeleteTodo(event){
        todos=todos.filter((item)=>item.id!==event.detail.id);
    }
</script>
<div>
    <input type='text' bind:value={inputText}/>
    <button type='button' on:click={onClickAddTodo}>add</button>
    <ol> 
        {#each todos as todo(todo.id)}
            <Todo {...todo} on:delete={onClickDeleteTodo}/>    
        {/each}
    </ol>
</div>

<style>
    div{
        padding-top:5rem;
		width: 20rem;
	}
    input{
        width:80%;
    }
</style>