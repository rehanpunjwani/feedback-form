<script>
	import FeedbackList from "./components/FeedbackList.svelte";
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
	]
	$: count = feedback.length
	$: average = feedback.reduce((prev, {rating}) => prev + rating, 0)/feedback.length;
const deleteFeedback=(e)=>{
	const id = e.detail;
	feedback = feedback.filter(item=>item.id!==id)
}
</script>

<main class="container">
<FeedbackList {feedback} on:delete-feedback={deleteFeedback} />
</main>

<style>
	
</style>