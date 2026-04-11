<script lang="ts">
    import { page } from "$app/state";
    import { onMount } from "svelte";

    import folder from "$lib/personalwebsite_imgs/folder.png";
    import textfile from "$lib/personalwebsite_imgs/text_file.png";

    let { tabname, xFunc, xTarget, clickFunc, type } = $props()

    let iconSrc=$state("");
    
    let tabForm:any;

    onMount(()=>{
        tabForm.onclick=function(){
            clickFunc("fromButton",tabname);
        }
        if(type=="text"){
            iconSrc=textfile;
        }else{
            iconSrc=folder;
        }
    });

    function deleteTab(){
        xFunc("fromButton", tabname);
    }
    
</script>

<div class="bg-[#3b2932] w-[13vw] rounded-t-[20px] justify-around flex" bind:this={tabForm}>
    <img src={iconSrc} alt="icon" class="w-[2.2vw] h-[2.2vw] mt-auto mb-auto">
    <h3 class="text-center text-white mplus cursor-default">{tabname}</h3>
    <button class="mplus text-white" onclick={deleteTab}>x</button>
</div>

<style>
    .mplus{
        font-family: "M PLUS Rounded 1c", sans-serif;
    }
</style>