<script>
    import HamburgerIcon from "./HamburgerIcon.svelte";
    
</script>

<style>
    .dropdown-button{
        cursor: pointer;
        padding-top: 3px;
        border-radius: 50%;
        width: auto;
        min-width: 50px;
        height: 50px;
        border-color: transparent;
        align-items: center;
        text-align: center;
        background-color: #23153c;
    }
    .dropdown-button:hover{
        background-color: gray;
    }
</style>

<button on:click class="dropdown-button">
    <HamburgerIcon/>
</button>