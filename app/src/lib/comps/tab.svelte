<script lang="ts">
    import { page } from "$app/state";
    import { onMount } from "svelte";

    import folder from "$lib/personalwebsite_imgs/folder.png";
    import textfile from "$lib/personalwebsite_imgs/text_file.png";

    import defaultCursor from "$lib/mikuCursors/Normal.cur";
    import clickerCursor from "$lib/mikuCursors/Alternate.cur";

    let { tabname, xFunc, xTarget, clickFunc, type } = $props()

    let iconSrc=$state("");

    let bgColor=$state("background-color:#3b2932");
    
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

    export function changeBgColor(selected:boolean){
        if(selected){
            bgColor="background-color:#3b2932";
        }else{
            bgColor="background-color:#2B1D25";
        }
    }

    function deleteTab(){
        xFunc("fromButton", tabname);
    }
    
</script>

<div class="w-[13vw] rounded-t-[20px] justify-around flex" bind:this={tabForm} style={bgColor}>
    <img src={iconSrc} alt="icon" class="w-[3vw] h-[3vw] mt-auto mb-auto">
    <h3 class="text-center text-white mplus text-[1.2vw]" style={`cursor:url(${defaultCursor}),auto`}>{tabname}</h3>
    <button class="mplus text-white text-[1.5vw]" onclick={deleteTab} style={`cursor:url(${clickerCursor}),auto`}>x</button>
</div>

<style>
    .mplus{
        font-family: "M PLUS Rounded 1c", sans-serif;
    }
</style>