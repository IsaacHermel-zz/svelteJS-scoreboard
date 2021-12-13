<script>
  import Header from "./components/Header/Index.svelte";
  import User from "./components/User/Index.svelte";
  import AddUser from "./components/addUser/Index.svelte";
  import Footer from './components/Footer/Index.svelte';

  let users = [
    {
      name: "Ferdinand Green",
      points: 120,
    },
    {
      name: "Ellery Porter",
      points: 110,
    },
    {
      name: "Laurel Parham",
      points: 150,
    },
    {
      name: "Tony Badman",
      points: 200,
    },
    {
      name: "Noah Brown",
      points: 240,
    },
  ];

  const addUser = (e) => {
    const newUser = e.detail;
    users = [...users, newUser];
    console.log(users);
  };

  const removeUser = (e) => {
    users = users.filter((user) => user.name !== e.detail);
  };
</script>

<Header />
<AddUser on:adduser={addUser} />
<main>
  {#if users.lenght === 0}
    <p>Sem jogadores!</p>
  {:else}
    {#each users as user}
      <User
        name={user.name}
        points={user.points}
        on:removeplayer={removeUser}
      />
    {/each}
  {/if}
</main>
<Footer/>

<style>
  main {
    display: flex;
    flex-wrap: wrap;
    flex-direction: row;
    justify-content: center;
    gap: 2.5rem;
    width: 100%;
    padding: 6.25rem;
  }
</style>
