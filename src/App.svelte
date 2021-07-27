<script>
    import Header from './components/Header.svelte'
    import Footer from "./components/Footer.svelte";
    import CreatePollForm from "./components/CreatePollForm.svelte";
    import Tabs from "./shared/Tabs.svelte";
    import PollList from "./components/PollList.svelte";

    let tabs = ['Current Polls', 'Add New Poll'];
    let activeTab = 'Current Polls';

    let polls = [
        {
            id: 1,
            question: 'React or Angular',
            answerA: 'React',
            answerB: 'Angular',
            votesA: 6,
            votesB: 15
        }
    ]

    const tableChange = (e) => {
        activeTab = e.detail;
    }

    const handleAddPoll = (e) => {
        const poll = e.detail;
        polls = [poll, ...polls];
        activeTab = 'Current Polls'
        console.log(e.detail);
    }
</script>
<Header/>
<main>
    <Tabs {activeTab} {tabs} on:tabChange={tableChange}/>
    {#if activeTab === 'Current Polls'}
        <PollList {polls}/>
    {:else if activeTab === 'Add New Poll'}
        <CreatePollForm on:addPoll={handleAddPoll}/>
    {/if}
</main>
<Footer/>

<style>
    main {
        max-width: 1024px;
        margin: 40px auto;
    }
</style>
