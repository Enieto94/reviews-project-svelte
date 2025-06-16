<script>
  export let reviews = [];
  import { createEventDispatcher } from 'svelte';
  const dispatch = createEventDispatcher();

  const view = (index) => {
    dispatch('view', index);
  };
</script>

<div class="list">
  <h2>Lista de Reseñas</h2>
  {#if reviews.length === 0}
    <p>No hay reseñas aún.</p>
  {:else}
    <ul>
      {#each reviews as review, index}
        <li>
          <div class="info">
            <strong>{review.name}</strong>
            <p>{review.comment.slice(0, 60)}...</p>
          </div>
          <button on:click={() => view(index)}>Ver</button>
        </li>
      {/each}
    </ul>
  {/if}
</div>

<style>
  .list ul {
    list-style: none;
    padding: 0;
  }

  .list li {
    background: #fff;
    padding: 1rem;
    border: 1px solid #ddd;
    border-radius: 8px;
    margin-bottom: 1rem;
    display: flex;
    justify-content: space-between;
    align-items: center;
  }

  .info {
    flex-grow: 1;
  }

  button {
    padding: 0.4rem 0.8rem;
    background-color: #444;
    color: white;
    border: none;
    border-radius: 6px;
    cursor: pointer;
  }

  button:hover {
    background-color: #222;
  }
</style>
