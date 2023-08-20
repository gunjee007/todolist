<script lang="ts">
	import { onMount } from 'svelte';
	import Lists from './components/lists.svelte';
	// const mongoose = require('mongoose');

	import axios from 'axios';
	let list: string[] = [];
	onMount(() => {
		axios
			.get('http://localhost:3000/todo/list')
			.then(({ data }) => {
				if (data.status === 'success') {
					list = data.result;
				}
			})
			.catch((e) => {
				alert('Network error!');
			});
	});

	let inputValue: string = '';

	const onSubmit = (e: SubmitEvent) => {
		e.preventDefault();
		list = [...list, inputValue];
		inputValue = '';
	};

	const onRemoveTask = (task: string) => {
		list = list.filter((el) => el != task);
	};
</script>

<div class=" w-[500px] absolute bg-white h-[600px] rounded-xl p-10 tracking-wide">
	<div class=" flex items-center">
		<p class=" text-xl font-bold text-[#022162] tracking-wide mr-6">To-Do List</p>
		<img src="/images/icon.png" alt="" width="50px" height="auto" />
	</div>
	<!-- <Add /> -->

	<div class=" flex items-center mt-5">
		<form on:submit={onSubmit}>
			<div class="flex pl-6 w-[410px] rounded-3xl bg-[#edeef0]">
				<input
					type="text"
					bind:value={inputValue}
					class="flex-1 py-3 bg-transparent outline-none placeholder-gray-500"
					placeholder="Add your task"
				/>
				<button type="submit" class=" bg-[#ff5645] px-8 py-3 rounded-3xl text-white font-semibold"
					>ADD</button
				>
			</div>
		</form>
	</div>

	<div class="flex-col mt-5">
		{#each list as li}
			<Lists task={li} {onRemoveTask} />
		{/each}
	</div>
</div>
