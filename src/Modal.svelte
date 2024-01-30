<script>

    export let showModal = false;
    export let isPromo = false;
</script>

{#if showModal}
    <!-- The event handler of the modal is forwarded in the parent element.
    The 'self' event modifier is also used -->
    <div class="backdrop" class:promo={isPromo} on:click|self on:keypress={() => {}}>
        <div class="modal">
            <slot></slot>
        </div>
    </div>
{/if}

<style>
    .backdrop {
        width: 100%;
        height: 100%;
        position: fixed;
        background: rgba(0,0,0,0.8);
    }

    .modal {
        padding: 10px;
        border-radius: 10px;
        max-width: 400px;
        margin: 10% auto;
        text-align: center;
        background: white;
    }

    .promo .modal {
        background: crimson;
        color: white;
    }
</style>