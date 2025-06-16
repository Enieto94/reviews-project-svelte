<script>
  export let review;
  import { createEventDispatcher } from 'svelte';
  const dispatch = createEventDispatcher();

  const goBack = () => {
    dispatch('back');
  };
</script>

<div class="review">
  <h2>Ver Reseña</h2>
  <p><strong>{review.name}</strong></p>
  <p>{review.comment}</p>
  <button on:click={goBack}>Volver</button>
</div>

<style>
  .review {
    background: #fff;
    padding: 1.2rem;
    border: 1px solid #ccc;
    border-radius: 8px;
  }

  p {
    margin: 0.5rem 0;
  }

  button {
    margin-top: 1rem;
    padding: 0.6rem 1.2rem;
    background-color: #555;
    color: white;
    border: none;
    border-radius: 6px;
    cursor: pointer;
  }

  button:hover {
    background-color: #333;
  }
</style>
