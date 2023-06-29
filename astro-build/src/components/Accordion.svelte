<script>
    
    import { slide } from 'svelte/transition';
    export let { open } = false;
    export let styleAccordion = '';
    export let styleSlide = '';
    export let styleDetails = '';
    const handleClick = () => open = !open;
    const focusOut = () => open = false;

    const styleAcc = styleAccordion;
    const styleSl = styleSlide;
    const styleDet = styleDetails;

    /*function slide2Axis(node, { duration = 400, maxWidth=75, maxHeight}){
        return {
            duration,
            css: t => {
                if (t < maxWidth) {
                    return `width: ${t}%`
                } else {
                    return `height: ${t}%`
                }
                     
            }
        }
    }*/
</script>
  
<div class="accordion {styleAcc}">
    <div class="header">
        <button class="slide {styleSl}" on:click={handleClick} on:focusout={focusOut}>
            <slot name="head"></slot>
        </button>
    </div>
      
    {#if open}
    <div class="details" style={styleDet} transition:slide>
        <slot name="details">
        </slot>
    </div>
    {/if}
</div>
  
<style>
    div.accordion {
        margin: 1rem 0;
        color: black;
    }
    
    div.header {
        display:flex;
        width:100%;
    }
    
    .slide{
        /*width: 30%;*/
        height: 4rem;
        background-color: white;
        border-radius: 50px;
        border-color: transparent;
        transition: 0.35s ease-in-out;
    }
    .slide:focus{
        width: 90%;
        border-color: black;
        border-top: black;
        border-right: black;
        border-width: 5px;
    }
    .details {
        min-width: 20%;
        overflow: hidden;
        background-color: #cecece;
        padding:1rem;
        border-radius: 0.25rem;
        display: block;
        /*width: 75%*/;
        text-overflow: ellipsis;
        white-space: normal;
        transition: 0.35s ease-in-out;
    }
    .details:hover{
        white-space: normal;
    }
    slot{
        width: 100%;
    }
    slot:hover{
        transition: 0.35s ease-in-out;
    }
</style>