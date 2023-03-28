<script>
     let todoItem = ''
     let todoList = []

     function addThis(){
          if (todoItem == ''){
               return;
          }
          todoList = [...todoList,{
               text: todoItem,
               done: false
          }]
          todoItem = "";
     }
     function removeThis(index){
          todoList.splice(index, 1)
          todoList = todoList;
     }
     function removeDone(){
          todoList = todoList.filter (t => !t.done)
     }
     function removeAll(){
          todoList = [];
     }
     $: hasItems = todoList.length;
</script>

<div class="main">
     <form on:submit|preventDefault={addThis}>
          <input bind:value={todoItem} type="text" autofocus>
          <button type="submit"> Add</button>
     </form>
     
     <ul>
          {#each todoList as item, index}
               <li>
                    <input type="checkbox" bind:checked={item.done}>
                    <span class:done={item.done}>{item.text}</span>
                    <span on:click={() => removeThis(index)} on:keypress={() => removeThis(index)} class="remove"></span>
               </li>
          {/each}
     </ul>
     {#if hasItems > 0}
     <div class="removeButton" >
          <button on:click={removeDone}> Remove Done</button>
          <button on:click={removeAll}> Remove All</button>
     </div>
     {/if}
     

</div>


<style>
     
     .main{
          margin: auto;
          padding: 2rem;
          display: block;
          width: 50vw;
          font-family:'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
     }
     form{
          text-align: center;
     }
     li{
          list-style: none;
          text-align: center;
          font-size: 1.7rem;
     }
     button{
          border-radius: 2rem;
          border: rgb(255, 185, 167);
          background-color: rgb(255, 242, 167);
          color: rgb(221, 101, 101);
          font-family:'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
          font-size: 1.7rem;
     }
     .done{
          text-decoration: line-through;
          color: rgb(221, 101, 101);
     }
     .remove{
          height: 1.7rem;
          width: 1.7rem;
          display: inline-block;
          background: url('./images/trashbin.png') no-repeat;
          background-size: 100% auto;
          cursor: pointer;
     }
     .removeButton{
          text-align: center;
     }
     
</style>