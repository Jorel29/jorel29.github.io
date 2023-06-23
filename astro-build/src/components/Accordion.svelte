<script>
    export let open = false;
    import { slide } from 'svelte/transition';
    const handleClick = () => open = !open;
    const focusOut =()=> open = false;
</script>
  
<div class="accordion">
    <div class="header">
        <button class="slide" on:click={handleClick} on:focusout={focusOut}>
            <slot name="head"></slot>
        </button>
    </div>
      
    {#if open}
    <div class="details" transition:slide>
        <slot name="details">
        </slot>
    </div>
    {/if}
</div>
  
<style>
    div.accordion {
        margin: 1rem 0;
    }
    
    div.header {
        display:flex;
        width:100%;
    }
    
    button.slide{
        display:flex;
        width: 30%;
        height: 4rem;
        background-color: white;
        border-radius: 0.25rem;
        border-color: transparent;
        transition: 0.35s ease-in-out;
    }
    button.slide:hover{
        width: 100%;
        
    }
    button.slide:focus{
        width: 100%;
        border-color: black;
    }
    div.details {
        background-color: #cecece;
        padding:1rem;
        border-radius: 0.25rem;
    }
</style>