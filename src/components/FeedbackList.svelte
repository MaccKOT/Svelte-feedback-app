<script>
  import FeedbackItem from './FeedbackItem.svelte';
  export let feedback = [];

  // console.log(feedback);
</script>

{#each feedback as fb (fb.id)}
  <!-- on:delete-feedback - forward custom event to upper component -->
  <FeedbackItem item={fb} on:delete-feedback />
{/each}
