<script>
    
    function remove(index) {
        todoList.splice(index, 1);
        todoList = todoList;
    }
    function complete(index) {
        todoList[index].completed=!todoList[index].completed
    }
let newItem="";
let todoList=[];
function add() {
    if (newItem !=="") {
        todoList = [
            ...todoList,
            {
                Задача:newItem,
                Завершено:false,
            },
        ];
        newItem="";
    }
}
import { Icon } from '../../../../components/Icon.svelte';
 </script>
 <h1>My to-do list</h1>
<main>
    <form on:submit|preventDefault={add}>
    <input bind:value={newItem} placeholder="Enter to-do" />
<button class="add-todo" on:click={add}><span>+</span></button>
</form>
<div class="todos">
    {#each todoList as item, index}
    <span class="todo____text">{item.task}</span>
    <div class="todo____buttons"></div>
    <button class="complete" on:click={() => complete(index)}>
        <Icon name="check-mark" />
        </button>
        <button class="delete" on:click={() => remove(index)}>
        <Icon name="delete" />
        </button>
    {/each}
    </div>
    <div class="todo"></div>

</main>
<style>
    main {

display: flex;
flex-direction: column; align-items: center;
min-height: 100%; padding: 5vmin;
box-sizing: border-box; background: antiquewhite;
    }
form {
width: 100%; max-width: 500px; display: flex;
align-items: center; margin-bottom: 1rem;
}
input { flex-grow: 1; width: 0;
border: none;
border-bottom: 1px solid black;
background: transparent;
box-shadow: none;
font-size: 1.2rem;
margin: 0;
outline: none;
}
.todo {
display: flex;
padding: 20px;
border-radius: 20px;
box-shadow: 00 15px rgb(0 0 0/20%); background-color: hsla(0, 0%, 100%, 0.2); margin-top: 1rem;
font-size: 1.2rem;
justify-content: space-between;
align-items: center;
}
.todo____buttons {
display: flex;
align-items: center;
margin-left: 1rem;
}


button {

background-color: transparent;
border: none;
}
button.delete, button.delete:hover {

color: brown;
transition: color 100ms ease-out;
}
button.complete,
button.complete:hover {

color: cadetblue;
transition: color 100ms ease-out;
}

.todos {

width: 100%;

max-width: 500px;

}
</style>