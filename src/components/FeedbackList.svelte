<script>
export let feedback =[]
import FeedbackItem from "./FeedbackItem.svelte";

</script>
{#each feedback as fb (fb.id) }
    <FeedbackItem item={fb} on:delete-feedback />
{/each}
