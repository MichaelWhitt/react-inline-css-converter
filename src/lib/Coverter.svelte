<script lang="ts">
    import { loop_guard } from "svelte/internal";



    let leftInput = ''

    const formatInput = (val: string) => {
        //<span id='page-title' style={{left: '11%', weight: 500, fontSize: 700, textAlign: 'center', coolName: "thing", size: 500px}}>
        let styleString: string
        if (val.includes('style={{')) {
            const indexOfStyleString = val.indexOf('style=')
            styleString = val.slice(indexOfStyleString + 8, val.lastIndexOf('}}'))
            const valArray = styleString.split(',').map( v => v.trim() + ';')
            return valArray
        }
        return val.split(',')
    }
  
</script>
  
<div class='h-[80%] w-[60%] flex flex-col items-center gap-[50px]'>
    <h1 class="text-4xl text-indigo-400">React Inline CSS Converter</h1>
    <div class="border-2 solid rounded border-white h-[80%] w-[100%] flex flex-col justify-center p-5">
        <div class='flex gap-5 justify-evenly'>
            <textarea bind:value={leftInput} class='w-[400px] h-[400px] rounded resize-none'/>
            <div class='w-[400px] h-[400px] rounded bg-[#111] border-2'>
                <div class='text-indigo-300'>.className {'{'}</div>
                {#each formatInput(leftInput) as item}
                    <div class='text-indigo-500 ml-5'>{item}</div>
                {/each}
                <div class='text-indigo-300'>{'}'}</div>
            </div>
        </div>
    </div>
</div>

