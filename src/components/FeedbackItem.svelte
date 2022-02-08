<script>
import Card from "../ui/Card.svelte";
import {createEventDispatcher}  from 'svelte'
export let item;

const dispatch = createEventDispatcher()
const handleDelete = (itemId) =>{
    dispatch('delete-feedback', itemId);
}
</script>

<Card>
    <div class="num-display">
        {item.rating}
    </div>
    <button class="close" on:click={()=> handleDelete(item.id)}>
        X
    </button>
    <div class="text-display">
        {item.text}
    </div>
</Card>

<style>
.num-display {
    position: absolute;
    top: -10px;
    left: -10px;
    width: 50px;
    height: 50px;
    background: #246A73;
    color: #f7d1b5;
    border: 1px #f7d1b5 solid;
    border-radius: 50%;
    padding: 10px;
    text-align: center;
    font-size: 19px;
  }
  .close {
    position: absolute;
    top: 10px;
    right: 20px;
    cursor: pointer;
    background: none;
    border: none;
  }
</style>