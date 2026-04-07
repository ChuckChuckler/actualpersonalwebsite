<script lang="ts">
    import { page } from "$app/state";
    import { onMount } from "svelte";
    let {tabname, xFunc, xTarget, clickFunc } = $props()
    
    let visibility:string=$state("display:none");
    let tabForm:any;

    onMount(()=>{
        tabForm.onclick=function(){
            clickFunc(xTarget);
        }
    });

    function deleteTab(){
        visibility="display:none";
        xFunc(xTarget);
    }

    export function showTab(){
        visibility="display:flex";
    }
    
</script>

<div class="bg-[#3b2932] w-[13vw] rounded-t-[20px] justify-around" style={visibility} bind:this={tabForm}>
    <h3 class="text-center text-white mplus">{tabname}</h3>
    <button class="mplus text-white" onclick={deleteTab}>x</button>
</div>

<style>
    .mplus{
        font-family: "M PLUS Rounded 1c", sans-serif;
    }
</style>