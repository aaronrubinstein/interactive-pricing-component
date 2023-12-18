<script>
    import { onMount } from 'svelte';
    
    export let max;
    export let value;

    $: progress = (value / max) * 100;

    function updateShading() {
        document.documentElement.style.setProperty('--slider-shade-pct', `${progress}%`);
    }

    onMount(() => {
        updateShading();
    })

</script>

<input 
    type="range" 
    min="0" 
    {max} 
    bind:value 
    on:input={updateShading} >

<style>
    
    input[type="range"] {
        -webkit-appearance: none;
        appearance: none;
        background: transparent;
        cursor: pointer;
        width: 100%;
    }

    input[type="range"]::-webkit-slider-runnable-track {
        height: 8px;
        border-radius: 5px;
        /* background: var(--empty-slider-bar); */
        background: linear-gradient(to right, var(--slider-track-full) var(--slider-shade-pct), var(--slider-track-empty) var(--slider-shade-pct));
    }

    input[type="range"]::-moz-range-track {
        height: 8px;
        border-radius: 5px;
        background: var(--slider-track-empty);
    }

    input[type="range"]::-webkit-slider-thumb {
        -webkit-appearance: none;
        appearance: none;
        height: 40px;
        width: 40px;
        border-radius: 40px;
        background-color: var(--slider-thumb);
        background-image: url('/images/icon-slider.svg');
        background-repeat: no-repeat;
        background-position: center;
        border-radius: 40px;
        box-shadow: 0px 15px 30px 0px rgba(0, 255, 231, 0.60);
        /* to vertically center thumb: margin-top = (track height in pixels / 2) - (thumb height in pixels /2)  */
        margin-top: -16px;
    }

    input[type="range"]::-moz-range-thumb {
        height: 40px;
        width: 40px;
        border-radius: 40px;
        border: none;
        background-color: var(--slider-thumb);
        background-image: url('/images/icon-slider.svg');
        background-repeat: no-repeat;
        background-position: center;
        box-shadow: 0px 15px 30px 0px rgba(0, 255, 231, 0.60);
    }

    input[type="range"]::-webkit-slider-thumb:hover {
        background-color: var(--toggle-hover);
    }

    input[type="range"]::-webkit-slider-thumb:active {
        background-color: var(--slider-thumb-active);
    }

    input[type="range"]::-moz-range-thumb:hover {
        background-color: var(--toggle-hover);
    }

    input[type="range"]::-moz-range-thumb:active {
        background-color: var(--slider-thumb-active);
    }

</style>