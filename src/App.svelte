<script>
  import FeedbackForm from './components/FeedbackForm.svelte';
  import FeedbackList from './components/FeedbackList.svelte';
  import FeedbackStats from './components/FeedbackStats.svelte';

  // initial store
  let feedback = [
    {
      id: 1,
      rating: 10,
      text: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. consequuntur vel vitae commodi alias voluptatem est voluptatum ipsa quae.',
    },
    {
      id: 2,
      rating: 9,
      text: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. consequuntur vel vitae commodi alias voluptatem est voluptatum ipsa quae.',
    },
    {
      id: 3,
      rating: 8,
      text: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. consequuntur vel vitae commodi alias voluptatem est voluptatum ipsa quae.',
    },
  ];

  $: averageRating =
    feedback.reduce((a, { rating }) => a + rating, 0) / feedback.length;

  const deleteFeedback = (e) => {
    // console.log(e.detail); // our data from custom event
    const itemId = e.detail;

    feedback = feedback.filter((item) => item.id !== itemId);
  };

  const addFeedback = (e) => {
    // console.log(e.detail);
    const newFeedback = e.detail;

    feedback = [newFeedback, ...feedback];
  };
</script>

<main class="container">
  <FeedbackForm on:add-feedback={addFeedback} />
  <FeedbackStats count={feedback.length} {averageRating} />
  <FeedbackList {feedback} on:delete-feedback={deleteFeedback} />
</main>

<style>
  :root {
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen,
      Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
  }
</style>
