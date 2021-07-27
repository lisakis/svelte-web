<script>
    import PollDetails from './PollDetails.svelte';
    export let polls = [];
</script>
<div class="poll-listing">
    {#each polls as poll (poll.id)}
        <div>
            <PollDetails {poll}/>
        </div>
    {/each}
</div>

<style>

    .poll-listing {
        display: grid;
        grid-template-columns: 1fr 1fr;
        grid-gap: 20px;
    }

</style>
