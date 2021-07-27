<script>
    import { createEventDispatcher} from 'svelte';

    let dispatch = createEventDispatcher();

    let userName;
    let userAge;

    const handleSubmit = () => {
        const person = {
            name: userName,
            age: userAge,
            id: Math.random()
        };
        dispatch('addPerson', person);
    }
</script>

<form on:submit|preventDefault={handleSubmit}>
    <input type="text" placeholder="username" bind:value={userName}>
    <input type="number" placeholder="age" bind:value={userAge}>
    <button>Save</button>
</form>
