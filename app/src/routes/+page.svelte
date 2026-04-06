<script lang="ts">
    import folder from "$lib/personalwebsite_imgs/folder.png"
    import folder_opened from "$lib/personalwebsite_imgs/folder_opened.png"
    import text_file from "$lib/personalwebsite_imgs/text_file.png"

    import Tab from "$lib/comps/tab.svelte";
    import Aboutme from "$lib/comps/aboutme.svelte";
    import { onMount } from "svelte";

    let aboutme:any;
    let aboutmeTab:any;

    onMount(()=>{
        let aboutme = document.getElementById("aboutme")
        if(aboutme!=null){
            aboutme.onclick=function(){
                showSection("aboutme")
            }
        }
    })

    export function hideSection(toDelete:string){
        if(toDelete=="aboutme"){
            aboutme.changeVisible("display:none");
        }
    }

    function showSection(toShow:string){
        if(toShow=="aboutme"){
            aboutme.changeVisible("display:block");
            aboutmeTab.showTab();
        }
    }
</script>

<div class="flex justify-around w-[100%] h-[100vh] bg-[#49343fff] ">
    <div class="w-[20%] bg-[#2a1d24ff] border-r-[2px] border-[#f6c4dc]">
        <div class="bg-[#160e12ff] w-[100%] h-[8vh] leading-[8vh]">
            <h1 class="text-[#eca1cf] text-center mplus">☆ avishi's personal website ☆</h1>
        </div>
        <div>
            <div class="flex justify-start box-border p-[10px] bg-[#2a1d24ff] hover:bg-[#21151b]">
                <img src={folder} alt="folder" class="w-[70px] pr-[10px]">
                <h2 class="text-[#fae6f0] block mt-auto mb-auto courier">Projects</h2>
            </div>
            <div class="flex justify-start box-border p-[10px] bg-[#2a1d24ff] hover:bg-[#21151b]">
                <img src={folder} alt="folder" class="w-[70px] pr-[10px]">
                <h2 class="text-[#fae6f0] block mt-auto mb-auto courier">Hackathons</h2>
            </div>
            <div class="flex justify-start box-border p-[10px] bg-[#2a1d24ff] hover:bg-[#21151b]">
                <img src={folder} alt="folder" class="w-[70px] pr-[10px]">
                <h2 class="text-[#fae6f0] block mt-auto mb-auto courier">Skills</h2>
            </div>
            <div class="flex justify-start box-border p-[10px] bg-[#2a1d24ff] hover:bg-[#21151b]">
                <img src={folder} alt="folder" class="w-[70px] pr-[10px]">
                <h2 class="text-[#fae6f0] block mt-auto mb-auto courier">Achievements</h2>
            </div>
            <div id="aboutme" class="flex justify-start box-border p-[10px] bg-[#2a1d24ff] hover:bg-[#21151b]">
                <img src={text_file} alt="textfile" class="w-[70px] pr-[10px]">
                <h2 class="text-[#fae6f0] block mt-auto mb-auto courier">about_me.md</h2>
            </div>
            <div class="flex justify-start box-border p-[10px] bg-[#2a1d24ff] hover:bg-[#21151b]">
                <img src={text_file} alt="textfile" class="w-[70px] pr-[10px]">
                <h2 class="text-[#fae6f0] block mt-auto mb-auto courier">contact.md</h2>
            </div>
        </div>
    </div>
    <div class="w-[80%] overflow-auto scrollbar">
        <div class="bg-[#89697aff] w-[100%] h-[8vh] leading-[8vh] fixed flex">
            <Tab bind:this={aboutmeTab} tabname="about_me.md" clickFunc={hideSection}></Tab>
        </div>
        <br>
        <Aboutme bind:this={aboutme}></Aboutme>
    </div>
</div>

<style>
    .scrollbar{
        scrollbar-width: thin;
        scrollbar-color: #ec89c6 #160e12;
    }

    .courier{
        font-family: "Courier Prime", monospace
    }

    .mplus{
        font-family: "M PLUS Rounded 1c", sans-serif;
    }
</style>