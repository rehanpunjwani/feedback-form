<script>
import Button from '../ui/Button.svelte';
import Card from '../ui/Card.svelte'  
import RatingSelect from '../ui/RatingSelect.svelte'
import {createEventDispatcher} from 'svelte';
const dispatch = createEventDispatcher();
let text = ''
let min = 10  
let rating = 10;
let btnDisabled=true
let message = '';
const handleInput = ()=>{
    if (text.trim().length <= min){
        message = `Text must be atleast ${min} characters long`
        btnDisabled=true
    }
    else{
        message = null
        btnDisabled=false
    }
}
const handleSelection = (e) => rating = e.detail;
const handleSubmit = () =>{
    if(text.trim().length > min){
        const newFeedback = {
            id: Date.now(),
            text, 
            rating: +rating,
        }
        dispatch('add-feedback', newFeedback) 
        text = ''  
    }
}
</script>
  
  
  <Card>
    <header>
      <h2>How would you rate our service?</h2>
    </header>
  <form on:submit|preventDefault={handleSubmit} >
    <RatingSelect on:rating-selected={handleSelection} />
    <div class="input-group">
      <input type="text" on:input={handleInput} bind:value={text} placeholder="Tell us something that keeps you coming back">
      <Button disabled={btnDisabled} type="submit" >Send</Button>
    </div>
    {#if message}
    <div class="message">
        {message}
    </div>
    {/if}
  </form>
  </Card>
  
  <style>
    header {
      max-width: 400px;
      margin: auto;
    }
  
    header h2 {
      font-size: 22px;
      font-weight: 600;
      text-align: center;
    }
  
    .input-group {
      display: flex;
      flex-direction: row;
      border: 1px solid black;
      padding: 8px 10px;
      border-radius: 8px;
      margin-top: 15px;
    }
  
    input {
      flex-grow: 2;
      border: none;
      font-size: 16px;
      background-color: #fce2cf;
    }
  
    input:focus {
      outline: none;
    }
  
    .message{
      padding-top: 10px;
      text-align: center;
      color: rebeccapurple;
    }
  </style>
  