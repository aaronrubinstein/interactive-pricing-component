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
    <img src="images/pattern-circles.svg" alt="Circles">
</header>

<main>
    <div class="upper-section">
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
        
        <span class="price-container-mobile">
            <span class="price">
                ${(yearlyBilling ? (plans[selectedPlan].price - (plans[selectedPlan].price * .25)) : plans[selectedPlan].price)
                    .toLocaleString('en', {minimumFractionDigits: 2, maximumFractionDigits: 2})}
            </span>
            <span class="price-period">
                / {yearlyBilling ? 'year' : 'month'}
            </span>
        </span>
        
        <div class="billing-controls">
            <span class="billing-option">Monthly Billing</span>
            <Toggle bind:yearlyBilling={yearlyBilling} />
            <span class="billing-option yearly">
                Yearly Billing
                <span class="discount">25% discount</span>
                <span class="discount-mobile">25%</span>
            </span>
        </div>
    </div>

    <div class="lower-section">
        <div class="features">
            <div class="feature">
                <img src="images/icon-check.svg" alt="Check mark">
                <span class="feature-text">Unlimited websites</span>
            </div>
            <div class="feature">
                <img src="images/icon-check.svg" alt="Check mark">
                <span class="feature-text">100% data ownership</span>
            </div>
            <div class="feature">
                <img src="images/icon-check.svg" alt="Check mark">
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
        border-radius: 8px;
        background: var(--card-bg);
        box-shadow: 0px 20px 30px -5px rgba(127, 137, 185, 0.15);
    }

    .upper-section {
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

    .price-container-mobile {
        display: none;
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

    .discount, .discount-mobile {
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

    .discount-mobile {
        display: none;
    }

    .lower-section {
        height: 135px;
        border-top: 1px solid #ECF0FB;
        padding: 0 48px;
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
        transition: color .2s;
    }

    button:hover {
        color: #FFF;
    }

    @media (max-width: 570px) {

        header {
            margin-top: 89px;
            margin-bottom: 64px;
            position: relative;
        }
        
        h1 {
            font-size: 20px;
            margin-bottom: 8px;
        }

        p {
            font-size: 13px;
            line-height: 23px;
        }    
        
        main {
            width: 327px;
        }

        .upper-section {
            padding: 34px 24px 0px 24px;
        }

        .top-row {
            justify-content: center;
            margin-bottom: 25px;
        }

        .plan-name {
            font-size: 12px;
            letter-spacing: 1.714px;
        }

        .price-container {
            display: none;
        }

        .price-container-mobile {
            display: flex;
            justify-content: center;
            align-items: center;
            margin-top: 35px;
        }

        .price {
            font-size: 32px;
            letter-spacing: -0.8px;
        }

        .price-period {
            font-size: 14px;
            margin-left: 10px;
        }

        .billing-controls {
            gap: 12px;
            margin-top: 34px;
            margin-bottom: 38px;
            margin-left: -12px;
        }

        .discount {
            display: none;
        }
        
        .discount-mobile {
            display: inline;
            right: -47px;
            width: 41px;
        }

        .lower-section {
            height: 200px;
            padding: 24px 0 32px 0;
            flex-direction: column;
            justify-content: space-between;
            align-items: center;
        }

        .features {
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            gap: 11px;
        }
    }
     
</style>