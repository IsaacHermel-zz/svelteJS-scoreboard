<script>
  import { createEventDispatcher } from "svelte";

  const dispatch = createEventDispatcher();

  export let name;
  export let points;

  const addPoint = () => {
    points++;
  };
  const removePoint = () => {
    points--;
  };
  const onDelete = () => dispatch("removeplayer", name);
</script>

<div class="card">
  <h1>{name}</h1>
  <h3>Pontos: {points}</h3>
  <div class="btns-row">
    <button class="btn" on:click={addPoint}>+1</button>
    <button class="btn btn-dark" on:click={removePoint}>-1</button>
  </div>
  <button class="btn btn-danger" on:click={onDelete}>Deletar</button>
</div>

<style>
  .card {
    position: relative;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    width: 25rem;
    height: 15rem;
    padding: 1.5rem;
    border: 0;
    border-radius: 0.5rem;
    box-shadow: 0 0 0.313rem 0 rgba(0, 0, 0, 0.25);
  }

  .card .btns-row {
    display: flex;
    gap: 1rem;
  }

  .btn {
    display: block;
    padding: 0.75rem 2.25rem;
    border: 0;
    border-radius: 0.5rem;
    background: #e5e5e5;
    font-weight: 700;
    transition: 0.5s;
  }

  .btn:hover {
    background: #a7a7a7;
  }

  .btn-dark {
    background: #171717;
    color: #ffffff;
  }

  .btn-dark:hover {
    background: #858585;
  }

  .btn-danger {
    position: absolute;
    bottom: 1.5rem;
    right: 1.5rem;
    background: #ff0000;
    color: #ffffff;
  }

  .btn-danger:hover {
    background: #c90000;
  }
</style>
