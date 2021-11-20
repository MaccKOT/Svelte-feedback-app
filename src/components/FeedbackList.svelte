<script>
  import { FeedbackStore } from '../store/stores.js';
  // import { onMount, onDestroy } from 'svelte';
  import FeedbackItem from './FeedbackItem.svelte';
  import { fade, scale } from 'svelte/transition';

  // let feedback = [];

  //long way to subscribe to store
  //const unsubscribe = FeedbackStore.subscribe((data) => (feedback = data));

  // life cycle methods

  // onMount(() => {
  //   console.log('mounted');
  // });

  // onDestroy(() => {
  //   unsubscribe();
  // });

  // console.log(feedback);
</script>

<!-- $FeedbackStore - direct access of store, no need unsubscribe -->
{#each $FeedbackStore as fb (fb.id)}
  <div in:scale out:fade={{ duration: 500 }}>
    <FeedbackItem item={fb} />
  </div>
{/each}
