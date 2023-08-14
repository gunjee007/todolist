<script>

    let list = "";
    let lists = [];
    const handleClick = () => {
        
    };
    const handleInput = (e) => {
        list = e.target.value
    };
    console.log(list)
</script>

<div class=" flex items-center mt-5">
    <form action="">
        <input type="text" on:input={handleInput} class=" flex pl-6 w-[410px] rounded-3xl py-3 bg-[#edeef0] outline-none relative placeholder-gray-500" placeholder="Add your task" id="">
    </form>
    <button class=" bg-[#ff5645] px-8 py-3 rounded-3xl text-white font-semibold  absolute right-10" on:click={handleClick}>ADD</button>
</div>