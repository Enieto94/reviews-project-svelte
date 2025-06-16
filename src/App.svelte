<script>
  import ReviewForm from './ReviewForm.svelte';
  import ReviewList from './ReviewList.svelte';
  import ReviewView from './ReviewView.svelte';
  import { onMount } from 'svelte';
  import { getStoredReviews, saveReviews } from './lib/storage.js';

  let reviews = [];
  let selectedReview = null;

  onMount(() => {
    reviews = getStoredReviews();
  });

  const addReview = (review) => {
    reviews = [...reviews, review];
    saveReviews(reviews);
  };

  const viewReview = (index) => {
    selectedReview = reviews[index];
  };

  const goBack = () => {
    selectedReview = null;
  };
</script>
<style>
  main {
    max-width: 600px;
    margin: 2rem auto;
    font-family: 'Segoe UI', sans-serif;
    padding: 1rem;
    background: #f9f9f9;
    border-radius: 12px;
    box-shadow: 0 0 10px rgba(0,0,0,0.1);
  }

  h1 {
    text-align: center;
    color: #333;
  }
</style>

<main>
  <h1>Reseñas</h1>
  {#if selectedReview}
    <ReviewView review={selectedReview} on:back={goBack} />
  {:else}
    <ReviewForm on:addReview={event => addReview(event.detail)} />
    <ReviewList {reviews} on:view={e => viewReview(e.detail)} />
  {/if}
</main>
