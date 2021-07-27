<script>
    import {createEventDispatcher} from 'svelte';
    const dispatch = createEventDispatcher();

    export let tabs;
    export let activeTab

</script>

<div class="tabs">
    <ul>
        {#each tabs as tab}
            <li on:click={() => {dispatch('tabChange', tab)}}>
                <div class:active={tab === activeTab}>{tab}</div>
            </li>
        {/each}
    </ul>
</div>

<style>

    .tabs {
        margin-bottom: 40px;
    }

    ul {
        display: flex;
        justify-content: center;
        list-style-type: none;
        padding: 0;
    }

    li {
        margin: 0 16px;
        font-size: 18px;
        color: #666;
        cursor: pointer;
    }

    .active {
        color: crimson;
        border-bottom: 2px solid crimson;
        padding-bottom: 8px;
    }
</style>
