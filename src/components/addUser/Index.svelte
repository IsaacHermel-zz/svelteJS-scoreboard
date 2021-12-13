<script>
  import { createEventDispatcher } from "svelte";

  const dispatch = createEventDispatcher();

  let user = {
    name: "",
    points: 0,
  };

  const onSubmit = (e) => {
    e.preventDefault();
    dispatch("adduser", user);
    user = {
      name: "",
      points: 0,
    };
  };
</script>

<form on:submit={onSubmit}>
  <input type="text" placeholder="Nome do jogador..." bind:value={user.name} />
  <input
    type="number"
    placeholder="Pontos do jogador"
    bind:value={user.points}
  />
  <input type="submit" class="btn btn-add" value="Adicionar jogador" />
</form>

<style>
  form {
    position: relative;
    display: flex;
    flex-direction: column;
    flex-wrap: wrap;
    gap: 0.625rem;
    margin-top: 10rem;
    padding: 2rem;
    border: 0;
    border-radius: 0.5rem;
    box-shadow: 0 0 0.313rem 0 rgba(0, 0, 0, 0.25);
  }

  input {
    display: block;
    padding: 0.5rem 1.25rem;
    border: 0;
    border-radius: 0.5rem;
    background: #e5e5e5;
  }

  /* Chrome, Safari, Edge, Opera */
  input::-webkit-outer-spin-button,
  input::-webkit-inner-spin-button {
    -webkit-appearance: none;
    margin: 0;
  }

  /* Firefox */
  input[type="number"] {
    -moz-appearance: textfield;
  }

  .btn {
    padding: 0.75rem 2.25rem;
    background: #e5e5e5;
    font-weight: 700;
    transition: 0.5s;
  }

  .btn:hover {
    background: #a7a7a7;
  }

  .btn-add {
    background: #4659e3;
    color: #ffffff;
  }

  .btn-add:hover {
    background: #2e3ca5;
  }
</style>
