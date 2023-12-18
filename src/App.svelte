<script>
    import Slider from './lib/Slider.svelte';
    import Toggle from './lib/Toggle.svelte';

    const plans = [
        {name: '10K pageviews', price: 8 },
        {name: '50K pageviews', price: 12 },
        {name: '100K pageviews', price: 16 },
        {name: '500K pageviews', price: 24 },
        {name: '1M pageviews', price: 36 },
    ];

    let selectedPlan = 2;

    let yearlyBilling = false;
</script>

<header>
    <h1>Simple, traffic-based pricing</h1>
    <p>Sign-up for our 30-day trial. No credit card required.</p>
    <img src="/images/pattern-circles.svg" alt="Circles">
</header>

<main>
    <div class="top-row">
        <span class="plan-name">
            {plans[selectedPlan].name}
        </span>
        <span class="price-container">
            <span class="price">
                ${(yearlyBilling ? (plans[selectedPlan].price - (plans[selectedPlan].price * .25)) : plans[selectedPlan].price)
                    .toLocaleString('en', {minimumFractionDigits: 2, maximumFractionDigits: 2})}
            </span>
            <span class="price-period">
                / {yearlyBilling ? 'year' : 'month'}
            </span>
        </span>
    </div>

    <Slider bind:value={selectedPlan} max={plans.length - 1} />
    
    <div class="billing-controls">
        <span class="billing-option">Monthly Billing</span>
        <Toggle bind:yearlyBilling={yearlyBilling} />
        <span class="billing-option yearly">
            Yearly Billing
            <span class="discount">25% discount</span>
        </span>
    </div>

    <div class="bottom-row">
        <div class="features">
            <div class="feature">
                <img src="/images/icon-check.svg" alt="Check mark">
                <span class="feature-text">Unlimited websites</span>
            </div>
            <div class="feature">
                <img src="/images/icon-check.svg" alt="Check mark">
                <span class="feature-text">100% data ownership</span>
            </div>
            <div class="feature">
                <img src="/images/icon-check.svg" alt="Check mark">
                <span class="feature-text">Email reports</span>
            </div>
        </div>
        <button type="button">Start my trial</button>
    </div>
</main>

<style>
    header {
        margin-top: 104px;
        margin-bottom: 92px;
        position: relative;
    }

    header img {
        position: absolute;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%);
        z-index: -1;
    }
    
    h1 {
        font-size: 28px;
        font-weight: 800;
        text-align: center;
        color: var(--text-and-cta-bg);
        margin-bottom: 12px;
    }

    p {
        font-size: 15px;
        font-weight: 600;
        text-align: center;
        color: var(--text);
    }    
    
    main {
        width: 540px;
        /* height: 397px; */
        border-radius: 8px;
        background: var(--card-bg);
        border-radius: 8px;
        box-shadow: 0px 20px 30px -5px rgba(127, 137, 185, 0.15);
        padding: 40px 48px 0px 48px;
    }

    .top-row {
        display: flex;
        justify-content: space-between;
        align-items: center;
        margin-bottom: 31px;
    }

    .plan-name {
        font-size: 14px;
        font-weight: 800;
        letter-spacing: 2px;
        text-transform: uppercase;
        color: var(--text);
    }

    .price-container {
        display: flex;
        justify-content: space-between;
        align-items: center;
    }

    .price {
        font-size: 40px;
        font-weight: 800;
        letter-spacing: -1px;
        color: var(--text-and-cta-bg);
    }

    .price-period {
        font-size: 16px;
        font-weight: 600;
        color: var(--text);
        margin-left: 8px;
    }

    .billing-controls {
        display: flex;
        justify-content: center;
        align-items: center;
        gap: 16px;
        margin-top: 51px;
        margin-bottom: 40px;
    }

    .billing-option {
        font-size: 12px;
        font-weight: 600;
        color: var(--text);
    }

    .yearly {
        position: relative;
    }

    .discount {
        position: absolute;
        right: -89px;
        width: 80px;
        height: 19px;
        border-radius: 9.5px;
        background: var(--discount-bg);
        font-size: 10px;
        font-weight: 800;
        color: var(--discount-text);
        text-align: center;
        line-height: 19px;
    }

    .bottom-row {
        height: 135px;
        border-top: 1px solid #ECF0FB;
        display: flex;
        justify-content: space-between;
        align-items: center;
    }

    .features {
        display: flex;
        flex-direction: column;
        justify-content: center;
        gap: 11px;
    }

    .feature {
        display: flex;
        align-items: center;
    }

    .feature-text {
        font-size: 12px;
        font-weight: 600;
        color: var(--text);
        margin-left: 16.05px;
    }

    button {
        width: 170px;
        height: 41px;
        border-radius: 20.5px;
        background: var(--text-and-cta-bg);
        font-size: 12px;
        font-weight: 800;
        color: var(--cta-text);
        cursor: pointer;
    }

    button:hover {
        color: #FFF;
    }





</style>