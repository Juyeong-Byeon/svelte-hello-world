<script>
    import {createEventDispatcher} from 'svelte';
    export let todo;
    export let id;

    const dispatch=createEventDispatcher();

    function onClickDelete(){
        dispatch('delete',{id})
    }

</script>
<li>
    <span>{todo}</span>
   <span>
        <input type="checkbox"/>
        <button type='button' on:click={onClickDelete}>delete</button>
    </span>
</li>

<style>
    li{
        list-style-type: disc;
        width:100%;
        display: flex;
        justify-content: space-between;
    }
</style>