<script lang="ts">
	import { localStorageStore } from '@skeletonlabs/skeleton'
	import type { Writable } from 'svelte/store';

	let inputName = ""
	let inputPhoneNumber = ""

	interface Contact {
		name: string
		phoneNumber: string
	}

	const contactStore: Writable<Contact[]> = localStorageStore("contactStore", [])

	function addContact() {

		$contactStore = [
			{
				name: "",
				phoneNumber: ""
			},
			...$contactStore
		]
	}


</script>

<div class="container h-full mx-auto flex justify-center items-center">
	<div class="space-y-5">
		<h1 class="h1">Contact List</h1>
		<p>All your contacts in one persistent state!</p>
		<label class="label">
			<span>Name</span>
			<input class="input" type="text" placeholder="Name" bind:value={inputName}>
		</label>
		<label class="label">
			<span>Phone Number</span>
			<input class="input" type="text" placeholder="Phone Number" bind:value={inputPhoneNumber}>
		</label>
		<button type="button" class="btn variant-filled">Add Contact</button>
		<hr>
		<h2 class="h2">Your Contacts</h2>
	</div>
</div>
