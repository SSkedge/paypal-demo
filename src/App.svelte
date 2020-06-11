<script>
    import {onMount} from 'svelte';

    export let title;
    let success = false;

    onMount(() => {
        paypal.Buttons({
            style: {
                shape: 'rect',
                color: 'silver',
                layout: 'vertical',
                label: 'pay',
            },
            createOrder: function (data, actions) {
                return actions.order.create({
                    purchase_units: [
                        {
                            amount: {
                                currency_code: "GBP",
                                value: "10.00",
                                breakdown: {
                                    item_total: {
                                        currency_code: "GBP",
                                        value: "10.00"
                                    }
                                }
                            },
                            description: "Test Tickets",
                            items: [{
                                name: "Test Ticket",
                                unit_amount: {
                                    value: "5.00",
                                    currency_code: "GBP"
                                },
                                quantity: 2,
                                sku: "TestTkt1"
                            }]
                        }
                    ]
                });
            },
            onApprove: function (data, actions) {
                return actions.order.capture().then(function (details) {
                    success = true;
                });
            }
        }).render('#paypal-button-container');
    })
</script>

<main>
    <div class="container">
        <div class="cartel">
            <div class="border-cartel">
                <h1>{title}</h1>
            </div>
            {#if success}
                <div
                        class="alert-success"
                >
                    <span class="closebtn" onclick="this.parentElement.style.display='none';">&times;</span>
                    Payment Successful
                </div>
            {/if}
            <!-- PayPal Button -->
            <div id="paypal-button-container"></div>
            <!-- PayPal Button -->
        </div>





        <div class="pattern-2">
            <div></div>
            <div class="circle-2"></div>
            <div></div>
            <div class="circle-2"></div>
            <div></div>
            <div class="circle-2"></div>
            <div></div>
            <div class="circle-2"></div>
            <div></div>
            <div class="circle-2"></div>
            <div></div>
            <div class="circle-2"></div>
            <div></div>
            <div class="circle-2"></div>
            <div></div>
            <div class="circle-2"></div>
            <div></div>
            <div class="circle-2"></div>
            <div></div>
            <div class="circle-2"></div>
            <div></div>
            <div class="circle-2"></div>
            <div></div>
            <div class="circle-2"></div>
            <div></div>
            <div class="circle-2"></div>
            <div></div>
            <div class="circle-2"></div>
            <div></div>
            <div class="circle-2"></div>
            <div></div>
            <div class="circle-2"></div>
            <div></div>
            <div class="circle-2"></div>
            <div></div>
            <div class="circle-2"></div>
            <div></div>
            <div class="circle-2"></div>
            <div></div>
            <div class="circle-2"></div>
            <div></div>
            <div class="circle-2"></div>
            <div></div>
            <div class="circle-2"></div>
            <div></div>
            <div class="circle-2"></div>
            <div></div>
            <div class="circle-2"></div>
            <div></div>
            <div class="circle-2"></div>
            <div></div>
            <div class="circle-2"></div>
            <div></div>
            <div class="circle-2"></div>
            <div></div>
            <div class="circle-2"></div>
            <div></div>
            <div class="circle-2"></div>
            <div></div>
            <div class="circle-2"></div>
        </div>
    </div>
</main>

<style>
    main {
        /*text-align: center;*/
        height: 100vh;
        width: 100vw;
        background-color: #7b7887;
        display: flex;
        align-items: center;
        justify-content: center;
    }

    .container {
        width: 85%;
        height: 85%;
        display: grid;
        position: relative;
    }

    h1 {
        color: #7b7887;
        font-size: 3em;
        font-weight: 500;
        text-align: center;
    }

    .alert-success {
        padding: 15px;
        background-color: rgba(17, 158, 28, 0.5);
        color: white;
        margin-bottom: 10px;
    }

    /* The close button */
    .closebtn {
        margin-left: 15px;
        color: white;
        font-weight: bold;
        float: right;
        font-size: 22px;
        line-height: 20px;
        cursor: pointer;
        transition: 0.3s;
    }

    /* When moving the mouse over the close button */
    .closebtn:hover {
        color: black;
    }

    .pattern-2 {
        background-color: #a1dddd;
        display: grid;
        grid-template-columns: repeat(5, 1fr);
        grid-template-rows: repeat(12, 1fr);
        justify-items: center;
        align-items: center;
        z-index: 2;
        box-shadow: 4px 5px 5px 1px rgba(0, 0, 0, 0.24);
    }

    .circle-2 {
        width: 12px;
        height: 12px;
        background: white;
        border-radius: 50%;
    }

    .cartel {
        width: 50%;
        height: 50%;
        position: absolute;
        z-index: 7;
        top: 15%;
        left: 25%;
        background: white;
        color: #c39f65;
        font-family: "Roboto", sans-serif;
        box-shadow: 0px 3px 5px 0px rgba(0, 0, 0, 0.24);
    }

    .cartel p {
        text-align: center;
        padding-top: 0;
    }

    .cartel span {
        font-weight: bold;
    }

    .cartel .border-cartel {
        position: relative;
        width: 95%;
        height: 95%;
        border: 2px solid #c39f65;
        top: 2.5%;
        left: 2.5%;
        display: flex;
        align-items: center;
        justify-content: center;
        margin-bottom: 5%;
        text-transform: uppercase;
        font-size: 28px;
    }

    @media (min-width: 640px) {
        main {
            max-width: none;
        }
    }
</style>