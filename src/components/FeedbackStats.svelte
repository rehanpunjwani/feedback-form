<script>
    export let average;
    export let count;
</script>

<div class="feedback-stats">
    <h4>{count} Reviews</h4>
    <h4>Rating Average: {average}</h4>
</div>

<style>
    .feedback-stats {
        display: flex;
        justify-content: space-between;
        align-items: center;
    }
</style>