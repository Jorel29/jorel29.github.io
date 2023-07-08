<script>
    
    import { slide } from 'svelte/transition';
    export let open = false;
    export let useFocusOut = false;
    export let styleAccordion  = '';
    export let styleSlide  = '';
    export let styleDetails = '';
    const handleClick = () => {
        open = !open
        //want to add an unfocus logic
        if (open){

        }
    };
    const focusOut = () => open = false;
    
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
  
<div class="accordion {styleAccordion}">
    <div class="header">
        {#if useFocusOut}
        <button class="slide {styleSlide}" on:click={handleClick} on:focusout={focusOut}>
            <slot name="head"></slot>
        </button>
        {:else}
        <button class="slide {styleSlide}" on:click={handleClick}>
            <slot name="head"></slot>
        </button>
        {/if}
    </div>
      
    {#if open}
    <div class="details" style={styleDetails} transition:slide>
        <slot name="details">
        </slot>
    </div>
    {:else}
    <script is:inline>document.activeElement.blur();</script>
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
        
        background-color: white;
        border-radius: 50px;
        border-color: transparent;
        transition: 0.35s ease-in-out;
    }
    .slide:focus{
        /*width: 90%;*/
        
        border-width: 5px;
    }
    .details {
        min-width: 20%;
        overflow: hidden;
        
        
        display: flex;
        /*width: 75%*/;
        text-overflow: ellipsis;
        white-space: normal;
        transition: 0.35s ease-in-out;
    }
    .details:hover{
        white-space: normal;
    }
</style>