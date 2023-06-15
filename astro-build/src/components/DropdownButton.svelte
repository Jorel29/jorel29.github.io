<script>
    import HamburgerIcon from "./HamburgerIcon.svelte";
</script>

<style>
    .dropdown-button{
        cursor: pointer;
        border-radius: 25px;
        max-width: 75px;
        border-color: transparent;
    }
</style>

<button on:click class="dropdown-button">
    <HamburgerIcon/>
</button>