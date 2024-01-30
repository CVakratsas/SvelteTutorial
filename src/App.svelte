<script>
	import Modal from './Modal.svelte';
	import AddPersonForm from './AddPersonForm.svelte';

	let showModal = false;

	const toggleModal = () => {
		showModal = !showModal;
	}

	let people = [
    { name: 'yoshi', beltColour: 'black', age: 25, id: 1 },
    { name: 'mario', beltColour: 'orange', age: 45, id: 2 },
    { name: 'luigi', beltColour: 'brown', age: 35, id: 3 }
  ];

  const handleClick = (id) => {
	people = people.filter((person) => person.id != id)
  }
</script>

<!-- The modal has two props: The first is the message prop and the second is the showModal prop,
which is a short notation of writing showModal={showModal} when the name is the same as the var passed -->
<Modal {showModal} on:click={toggleModal}>
	<AddPersonForm />
</Modal>

<main>
	<!-- 'once' event modifier is used -->
	<button on:click|once={toggleModal}>Open modal</button>
	{#each people as person (person.id)}
		<div>
			<h4>{person.name}</h4>
			{#if person.beltColour === 'black'}
				<p><strong>MASTER NINJA</strong></p>
			{/if}
			<p>{person.age} years old, {person.beltColour} belt</p>
			<button on:click={() => handleClick(person.id)}>Delete</button>
		</div>
	{:else}
		<p>There are no people to show...</p>
	{/each}
</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
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