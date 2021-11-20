<script>
  let firstName = 'User';
  let lastName = 'Name';
  let color = 'blue';
  let showText = true;
  let users = [
    { id: 1, name: 'John' },
    { id: 2, name: 'Tom' },
    { id: 3, name: 'Mad' },
    { id: 4, name: 'Trevor' },
  ];

  $: name = firstName + ' ' + lastName;

  const toggle = () => {
    color = color === 'blue' ? 'crimson' : 'blue';
    showText = !showText;
  };

  const addUser = () => {
    // users.push({
    //   id: 5,
    //   name: 'New User',
    // }); -- not work

    users = [...users, { id: Math.random() * 100, name: 'New User' }];
  };
</script>

<main>
  <h1 style="color: {color};">Hello {name}!</h1>

  {#if showText}
    <p>Some text to show</p>
  {:else}
    <p>showText is false</p>
  {/if}

  <button type="button" on:click={toggle}>Toggle color</button>

  <ul>
    {#each users as user (user.id)}
      <li>{user.name}</li>
    {/each}
  </ul>
  <button type="button" on:click={addUser}>Add user to array</button>
</main>

<style>
  :root {
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen,
      Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
  }

  main {
    text-align: center;
    padding: 1em;
    margin: 0 auto;
  }

  img {
    height: 16rem;
    width: 16rem;
  }

  h1 {
    color: #ff3e00;
    text-transform: uppercase;
    font-size: 4rem;
    font-weight: 100;
    line-height: 1.1;
    margin: 2rem auto;
    max-width: 14rem;
  }

  p {
    max-width: 14rem;
    margin: 1rem auto;
    line-height: 1.35;
  }

  @media (min-width: 480px) {
    h1 {
      max-width: none;
    }

    p {
      max-width: none;
    }
  }
</style>
