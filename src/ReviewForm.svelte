<script>
  import { createEventDispatcher } from 'svelte';

  const dispatch = createEventDispatcher();

  let name = '';
  let comment = '';

  const submit = () => {
    if (name && comment) {
      dispatch('addReview', { name, comment });
      name = '';
      comment = '';
    }
  };
</script>

<div class="form">
  <h2>Escribe una reseña</h2>
  <input placeholder="Tu nombre" bind:value={name} />
  <textarea placeholder="Tu comentario" bind:value={comment}></textarea>
  <button on:click={submit}>Enviar</button>
</div>

<style>
  .form {
    margin-bottom: 2rem;
  }

  input, textarea {
    width: 100%;
    padding: 0.8rem;
    margin: 0.5rem 0;
    border: 1px solid #ccc;
    border-radius: 6px;
    font-size: 1rem;
  }

  textarea {
    min-height: 100px;
    resize: vertical;
  }

  button {
    padding: 0.6rem 1.2rem;
    background-color: #0077cc;
    color: white;
    border: none;
    border-radius: 6px;
    cursor: pointer;
    margin-top: 0.5rem;
  }

  button:hover {
    background-color: #005fa3;
  }
</style>
