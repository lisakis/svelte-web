<script>
    export let userName;
    export let userAge;
    export let hidden = true;
    let isAdding = true;
    let list = [];

    const saveName = (name, age) => {
        if (name && age) {
            list.push({id: list.length + 1, name: name, age: age});
            userName = null;
            userAge = null;
        }
    }
</script>

{#if (!hidden)}
    <div class="modal-backdrop" class:addUser={isAdding} on:click|self>
        <div class="modal">
            <slot></slot>
        </div>
    </div>
{/if}

<style>
    .modal-backdrop {
        width: 100%;
        height: 100%;
        position: fixed;
        background: rgba(0, 0, 0, 0.8);
    }

    .modal {
        color: black;
        padding: 10px;
        border-radius: 10px;
        max-width: 400px;
        margin: 10% auto;
        text-align: center;
        background: white;
    }
</style>
