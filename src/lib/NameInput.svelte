<script lang='ts'>
    export let val: string
    export let selector = 'c'
    
    const handleToggle = (type) => {
        console.log('type', type)
        selector = type
    }
    console.log(selector)

    const classBtn = `w-[60px] ${selector === 'c' ? 'bg-lime-200' : 'bg-indigo-400'} rounded-sm h-[40px]`
    const idBtn = `w-[60px] ${selector === 'i' ? 'bg-lime-200' : 'bg-indigo-400'} rounded-sm h-[40px]`
</script>

<div class='h-[60px] d-flex mb-[5px]'>
    <input 
        class='h-[40px]' 
        name='name' 
        aria-label='name-input' 
        placeholder='Class or ID Name'
        bind:value={val}
    />
    <div class='d-flex inline'>
        <button class={classBtn} on:click={() => handleToggle('c')}>Class</button>
        or
        <button class={idBtn} on:click={() => handleToggle('i')}>ID</button>
    </div>
</div>