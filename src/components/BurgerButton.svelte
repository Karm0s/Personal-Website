<script>

    import DropDownMenu from './DropDownMenu.svelte';
    export let onClick;
    
    let animationBar = '';
    let animationBar2 = '';
    let change = false;

    function handleClick(e){
        change = !change;
        onClick();
    }
</script>

<main on:click={handleClick} class="mt-1 burger">
    <button id="burger-button" class="{change? 'hamburger hamburger--slider is-active': 'hamburger hamburger--slider'}" type="button">
        <span class="hamburger-box">
            <span class="hamburger-inner"></span>
        </span>
    </button>
</main>

<style>
    .burger{
        position: relative;
    }
</style>