<script>
  import Todo from "./Todo.svelte";
</script>

<div class="header"></div>
<h1>My Todo App</h1>
<Todo />
<div class="footer"></div>

<style>
     h1{
          color: rgb(221, 101, 101);
          font-family:'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
          text-align:center ;
     }
     .footer, .header{
          background: url(images/hamster.png);
          height: 10rem;

     }
     .footer{   
          margin-top: auto;
     }
     :global(body){
          min-height: 100vh;
          display: flex;
          flex-direction: column;

     }
</style>
