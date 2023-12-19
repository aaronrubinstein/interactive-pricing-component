<script>
    export let yearlyBilling;
</script>

<label class="switch">
    <input type="checkbox" bind:checked={yearlyBilling}>
    <span class="slider"></span>
</label>

<style>    
    .switch {
        position: relative;
        display: inline-block;
        width: 43px;
        height: 22px;
    }

    .switch input { 
        opacity: 0;
        width: 0;
        height: 0;
    }

    .slider {
        position: absolute;
        cursor: pointer;
        top: 0;
        left: 0;
        right: 0;
        bottom: 0;
        border-radius: 22px;
        background: var(--toggle-bg);
        transition: background-color .4s;
    }

    .slider:before {
        position: absolute;
        content: "";
        height: 14px;
        width: 14px;
        border-radius: 50%;
        left: 4px;
        bottom: 4px;
        background-color: #FFF;
        transition: .4s;
    }

    input:checked + .slider:before {
        transform: translateX(21px);
        background-color: #FFF;
    }

    .switch:hover .slider {
        background: var(--toggle-hover);
    }
    
</style>