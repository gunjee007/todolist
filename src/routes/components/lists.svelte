<script lang="ts">
	export let task:string;
    export let onRemoveTask: (task: string) => void;

</script>
<!-- bla = bla.filter((el) => el != "bla") -->
<div class=" flex justify-between items-center pr-3">
	<div class=" flex m-2">
		<input
			type="checkbox"
			class=" w-5 h-5 mr-4 text-[#ff5645] bg-gray-100 border-gray-300 rounded focus:ring-[#ff5645] focus:ring-2 accent-[#ff5645]"
		/>
		<p>{task}</p>
	</div>
	<img src="/images/remove.png" alt="" class="cursor-pointer w-[15px] h-[15px] text-gray-500"  on:click={() => {onRemoveTask(task)}}/>
</div>
