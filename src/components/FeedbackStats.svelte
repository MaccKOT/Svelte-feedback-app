<script>
  import { FeedbackStore } from '../store/stores';

  let count = 0;
  let averageRating = 10;

  $: count = $FeedbackStore.length;
  $: averageRating =
    $FeedbackStore.reduce((a, { rating }) => a + rating, 0) / count;
</script>

<div class="feedback-stats">
  <h4>{count} Reviews</h4>
  <h4>Ratings Average: {averageRating}</h4>
</div>

<style>
  .feedback-stats {
    display: flex;
    justify-content: space-between;
    align-items: center;
  }
</style>
