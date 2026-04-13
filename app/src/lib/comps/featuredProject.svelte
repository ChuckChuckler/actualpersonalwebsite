<script lang="ts">
    import { onMount } from "svelte";

    import clickerCursor from "$lib/mikuCursors/Link.cur";

    let {pName, img, desc, completed, time, frontend, backend, repo, demo, id} = $props();
    let visibility = $state("display:none");

    onMount(()=>{
        if(id.includes("0")){
            visibility="display:block";
        }
    });

    function redirect(link:string){
        window.open(link, "_blank");
    }

    export function swap(elementToChange:string){
        if(id.includes(elementToChange)){
            visibility="display:block";
        }else{
            visibility="display:none";
        }
    }
</script>

<div class="bg-[#291d23] box-border p-[15px] rounded-[25px] border-[1.5px] border-[#fae6f0]" style={visibility} id={id}>
    <h1 class="text-center courier text-[#D9FCFF]">{pName}</h1>
    <br>
    <div class="sm:flex justify-between w-[100%] lg:h-[100%] sm:h-[27vw]">
        <img src={img} alt={`${pName} preview`} class="sm:w-[32.5vw] sm:h-[25vw] object-cover rounded-[20px] border-[1.5px] border-[#D9FCFF]">
        <div class="sm:w-[53%] h-[26.5vw] overflow-auto">
            <br class="sm:none">
            <h3 class="text-[#FCF0F6] mplus">{desc}</h3>
            <br>
            <h3 class="text-[#FCF0F6] mplus">{completed}</h3>
            <br>
            <h3 class="text-[#FCF0F6] mplus">Time taken: {time}</h3>
            <br>
            <h3 class="text-[#FCF0F6] mplus">Tech Stack:</h3>
            <p class="text-[#FCF0F6] mplus indent-[5%]">Frontend: {frontend}</p>
            <p class="text-[#FCF0F6] mplus indent-[5%]">Backend: {backend}</p>
            <br>
            <div class="flex justify-around sm:w-[40%] w-[60%] m-auto">
                <button style={`cursor:url(${clickerCursor}),auto`} onclick={function(){redirect(repo)}} class="text-[#FCF0F6] mplus border-[2px] border-[#D9FCFF] rounded-[15px] h-[40px] sm:w-[7.5vw] w-[20vw] bg-[#47303E] hover:bg-[#1C1418]">Repo</button>
                <button style={`cursor:url(${clickerCursor}),auto`} onclick={function(){redirect(demo)}} class="text-[#FCF0F6] mplus border-[2px] border-[#D9FCFF] rounded-[15px] h-[40px] sm:w-[7.5vw] w-[20vw] bg-[#47303E] hover:bg-[#1C1418]">Demo</button>
            </div>
        </div>
    </div>
</div>