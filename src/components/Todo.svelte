<script>
  let tasks = ["Workout (Leg day)", "Learn Svelte", "Cook a meal"];
  let inp = "";
  function handleSubmit() {
    tasks = [...tasks, inp];
    inp = "";
  }
  function handleFinished(a) {
    tasks = tasks.filter((m) => m !== a);
  }

  let colorArray = [
  "#ff2780",
  "#07b2d9",
  "#ffad33",
  "#8c25df"
];

</script>

<div class="row">
  <div class="col2">
    <h1>Todo's</h1>
    <div class="formContainer">
      <form class="inputBox" on:submit|preventDefault={handleSubmit}>
        <input type="text" name="cityname" required="required" bind:value={inp} />
        <span>add your new todo..</span>
      </form>
    </div>

    {#if tasks[0]}
      {#each tasks as name, i}
        <div class="list-block">
          <p style="border-left: 5px solid { colorArray[Math.floor(Math.random() * colorArray.length)]}">{name}</p>
          <button on:click={handleFinished(name)}>End task</button>
        </div>
      {/each}
    {:else}
      <div class="p-3 text-center">
        <h3>Hurrah !! You have no task left today .</h3>
      </div>
    {/if}
  </div>
  <div class="col2 bg" />
</div>

<style>
  * {
    margin: 0;
    padding: 0;
    transition: 0.5s;
  }

  *,
  *:before,
  *:after {
    box-sizing: inherit;
  }

  .row {
    display: flex;
  }

  .col2 {
    width: 50%;
    min-height: 100vh;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
  }
  .bg {
    background-image: url(https://i.pinimg.com/564x/93/76/82/937682649cb79ba7f9dc3a2f455d0229--black-white-pattern-white-patterns.jpg);
  }

  .list-block{
    margin: 10px 0;
    display: flex;
    justify-content: space-between;
    align-items: bottom;
    width: 300px;
  }
  button {
    border: none;
    outline: none;
  }
  p {
    padding: 10px 20px;
    width: 100%;
    border-bottom: 2px solid grey;
  }
  button {
    padding: 10px 20px;
    margin-left: 10px;
    border-radius: 35px;
    background: transparent;
    min-width: fit-content;
    border: 2px solid black;
    transition: 0.5s linear;
    cursor: pointer;
  }
  button:hover {
    background-color: black;
    color: white;
  }
  .formContainer {
    padding: 10px 10px 15px 10px;
    background: white;
    border-radius: 20px;
    z-index: 4;
  }

  .formContainer .inputBox {
    position: relative;
    width: 300px;
    height: 40px;
  }
  .formContainer .inputBox input {
    position: absolute;
    z-index: 1;
    background-color: transparent;
    width: 100%;
    border: 1px solid rgb(187, 121, 0);
    padding: 10px;
    border-radius: 5px;
    font-size: 16px;
    color: #111;
    font-weight: 300;
  }
  .formContainer .inputBox span {
    position: absolute;
    top: 1px;
    left: 1px;
    padding: 10px;
    transition: 0.5s;
  }

  .formContainer .inputBox input:focus ~ span,
  .formContainer .inputBox input:valid ~ span {
    transform: translateX(3px) translateY(-10px);
    font-size: 13px;
    background-color: white;
    padding: 0 8px 0 8px;
    z-index: 2;
  }
</style>
