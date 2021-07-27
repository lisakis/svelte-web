<script>
	import Modal from './Modal.svelte';
	import AddPersonForm from './AddPersonForm.svelte';

	let hidden = true;
	
    let list = [
        {id: 1, name: 'George', age: 26},
        {id: 2, name: 'John', age: 20},
        {id: 3, name: 'Ronaldo', age: 30}
    ]

    const deleteName = (id) => {
        list = list.filter(listItem => listItem.id !== id);
    }

    const toggleModal = () => {
        hidden = !hidden;
    }

    const addPerson = (e) => {
        const person = e.detail;
        list = [person, ...list];
    }

</script>

<Modal {hidden} on:click={toggleModal}>
    <AddPersonForm on:addPerson={addPerson} />
</Modal>

<header>
	<div>Home</div>
	<div><button on:click={toggleModal}>Add user</button></div>
</header>
<main>
    <div class="wrapper">
        <table>
            <thead>
            <tr>
                <th>id</th>
                <th>name</th>
                <th>age</th>
                <th>actions</th>
            </tr>
            </thead>
            <tbody>
            {#each list as list (list.id)}
                <tr>
                    <td>{list.id}</td>
                    <td>{list.name}</td>
                    <td>{list.age}</td>
                    <td>
                        <button on:click={() => {deleteName(list.id)}}>X</button>
                    </td>
                </tr>
            {/each}
            </tbody>
        </table>
    </div>
</main>

<style>

	header {
		display: flex;
		justify-content: space-between;
		margin: 0 50px;
	}
    main {
        text-align: center;
        padding: 1em;
        max-width: 240px;
        margin: 0 auto;
    }

    .wrapper {
        margin: 0 50px;
    }

    table {
        width: 100%;
    }

    h1 {
        color: #ff3e00;
        text-transform: uppercase;
        font-size: 4em;
        font-weight: 100;
    }

    @media (min-width: 640px) {
        main {
            max-width: none;
        }
    }
</style>
