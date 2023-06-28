<script>
    
    import { slide } from 'svelte/transition';
    export let { open } = false;
    const handleClick = () => open = !open;
    const focusOut = () => open = false;

</script>
  
<div class="accordion">
    <div class="header">
        <button class="slide" on:click={handleClick} on:focusout={focusOut}>
            <slot name="head"></slot>
        </button>
    </div>
      
    {#if open}
    <div class="details"  transition:slide>
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
    
    .slide{
        transform: translate(-50%,0%);
        
        width: 30%;
        height: 4rem;
        background-color: white;
        border-radius: 0.25rem;
        border-color: transparent;
        transition: 0.35s ease-in-out;
    }
    .details:hover{
        width: 50%;
        transition: 0.1s ease-in-out;
    }
    .slide:focus{
        width: 70%;
        border-color: black;
        border-top: black;
        border-right: black;
        border-width: 5px;
    }
    .details {
        background-color: #cecece;
        padding:1rem;
        border-radius: 0.25rem;
        display: block;
        transform: translate(-50%,0%);
        width: 30%;
        transition: 0.35s ease-in-out;
    }
</style>