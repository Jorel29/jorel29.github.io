<script>
    export let open = false;
    import { slide } from 'svelte/transition';
    const handleClick = () => open = !open
</script>
  
<div class="accordion">
    <div class="header">
        <button class="slide" on:click={handleClick}>
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
        width: 100%;
        background-color: white;
        border-radius: 0.25rem;
        border-color: transparent;
    }
    button.slide:hover{
        border-color: black;
    }
    
    div.details {
        background-color: #cecece;
        padding:1rem;
        border-radius: 0.25rem;
    }
</style>