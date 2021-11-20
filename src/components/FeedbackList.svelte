<script>
  import FeedbackItem from './FeedbackItem.svelte';
  import { fade, scale } from 'svelte/transition';

  export let feedback = [];

  // console.log(feedback);
</script>

{#each feedback as fb (fb.id)}
  <div in:scale out:fade={{ duration: 500 }}>
    <!-- on:delete-feedback - forward custom event to upper component -->
    <FeedbackItem item={fb} on:delete-feedback />
  </div>
{/each}
