<script>
    import HamburgerIcon from "./HamburgerIcon.svelte";
    
</script>

<style>
    .dropdown-button{
        cursor: pointer;
        border-radius: 50%;
        width: 2rem;
        height: 2rem;
        border-color: transparent;
        align-items: center;
        text-align: center;
        background-color: darkslategray;
    }
    .dropdown-button:hover{
        background-color: gray;
    }
</style>

<button on:click class="dropdown-button">
    <HamburgerIcon/>
</button>