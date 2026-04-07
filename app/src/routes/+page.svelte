<script lang="ts">
    import { onMount } from "svelte";

    import folder from "$lib/personalwebsite_imgs/folder.png"
    import folder_opened from "$lib/personalwebsite_imgs/folder_opened.png"
    import text_file from "$lib/personalwebsite_imgs/text_file.png"

    import Tab from "$lib/comps/tab.svelte";

    import Aboutme from "$lib/comps/aboutme.svelte";
    import Contact from "$lib/comps/contact.svelte";

    let defaultScreen:string=$state("display:block");

    let visibles:any[] = [];

    let aboutme:any;
    let aboutmeTab:any;

    let contact:any;
    let contactTab:any;

    onMount(()=>{
        let aboutMeClicker = document.getElementById("aboutme")
        if(aboutMeClicker!=null){
            aboutMeClicker.onclick=function(){
                showSection(aboutme, aboutmeTab)
            }
        }

        let contactClicker = document.getElementById("contact");
        if(contactClicker!=null){
            contactClicker.onclick=function(){
                showSection(contact, contactTab);
            }
        }
    })

    export function hideSection(toDelete:any){
        toDelete.changeVisible("display:none");
        visibles.splice(visibles.indexOf(toDelete), 1);
        if(visibles.length==0){
            defaultScreen = "display:block";
        }
    }

    function showSection(toShow:any, toShowTab:any){
        defaultScreen="display:none";
        for(let i:number=0;i<visibles.length;i++){
            visibles[i].changeVisible("display:none");
        }
        toShow.changeVisible("display:block");
        toShowTab.showTab();
        visibles.push(toShow);
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
            <div id="contact" class="flex justify-start box-border p-[10px] bg-[#2a1d24ff] hover:bg-[#21151b]">
                <img src={text_file} alt="textfile" class="w-[70px] pr-[10px]">
                <h2 class="text-[#fae6f0] block mt-auto mb-auto courier">contact.md</h2>
            </div>
        </div>
    </div>
    <div class="w-[80%] overflow-auto scrollbar">
        <div class="bg-[#89697aff] w-[100%] h-[8vh] leading-[8vh] fixed flex">
            <Tab bind:this={aboutmeTab} tabname="about_me.md" xFunc={hideSection} xTarget={aboutme}></Tab>
            <Tab bind:this={contactTab} tabname="contact.md" xFunc={hideSection} xTarget={contact}></Tab>
        </div>
        <div class="bg-[#89697aff] w-[100%] h-[8vh] leading-[8vh]">
        </div>
        <br>
        <div class="box-border p-[30px] text-center" style={defaultScreen}>
            <h1 class="text-white text-[100px]">(ó﹏ò｡)</h1>
            <h3 class="text-white text-[20px]">No folder or file open</h3>
        </div>
        <Aboutme bind:this={aboutme}></Aboutme>
        <Contact bind:this={contact}></Contact>
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