<script lang="ts">
    import { onMount } from "svelte";

    import folder from "$lib/personalwebsite_imgs/folder.png"
    import folder_opened from "$lib/personalwebsite_imgs/folder_opened.png"
    import text_file from "$lib/personalwebsite_imgs/text_file.png"

    import Tab from "$lib/comps/tab.svelte";

    import Aboutme from "$lib/comps/aboutme.svelte";
    import Contact from "$lib/comps/contact.svelte";
    import Skillsfolder from "$lib/comps/skillsfolder.svelte";
    import Experiences from "$lib/comps/experiences.svelte";
    import Achievements from "$lib/comps/achievements.svelte";
    import ProjectsFolder from "$lib/comps/projectsFolder.svelte";

    let defaultScreen:string=$state("display:block");

    let visibles:any[] = $state([]);
    let visiblesNames:string[]=$state([]);

    let aboutme:any;
    let aboutmeTab:any;

    let contact:any;
    let contactTab:any;

    let skillsFolder:any;
    let skillsFolderTab:any;

    let experiencesFolder:any;
    let experiencesFolderTab:any;

    let achievementsFolder:any;
    let achievementsFolderTab:any;

    let projectsFolder:any;
    let projectsFolderTab:any;


    let xTargetArr:any[]=$state([aboutme, contact, skillsFolder, experiencesFolder, achievementsFolder, projectsFolder]);
    let tabsArr:any[]=$state([aboutmeTab, contactTab, skillsFolderTab, experiencesFolderTab, achievementsFolderTab, projectsFolderTab]);

    let allTabs:Record<string,string>={
        "about_me.md":"text",
        "contact.md":"text",
        "skills":"folder",
        "experiences":"folder",
        "achievements":"folder",
        "projects":"folder"
    }

    onMount(()=>{
        let idsForClickers = ["aboutme", "contact", "skillsFolder", "experiencesFolder", "achievementsFolder", "projectsFolder"];
        let divsForClickers = [aboutme, contact, skillsFolder, experiencesFolder, achievementsFolder, projectsFolder];
        let namesForClickers = ["about_me.md", "contact.md", "skills", "experiences", "achievements", "projects"];
        
        for(let i:number=0;i<idsForClickers.length;i++){
            let clicker = document.getElementById(idsForClickers[i])
            if(clicker!=null){
                clicker.onclick=function(){
                    showSection(divsForClickers[i], namesForClickers[i]);
                }
            }
        }
    })

    export function hideSection(toDelete:any, toDeleteName:string){
        let arr:any[]=[aboutme, contact, skillsFolder, experiencesFolder, achievementsFolder, projectsFolder];
        if(toDelete=="fromButton"){
            toDelete=arr[Object.keys(allTabs).indexOf(toDeleteName)];
        }
        toDelete.changeVisible("display:none");
        let index=visiblesNames.indexOf(toDeleteName);
        visiblesNames.splice(index,1);
        visibles.splice(index, 1);
        if(visibles.length==0){
            defaultScreen = "display:block";
        }else{
            arr[Object.keys(allTabs).indexOf(visiblesNames[visiblesNames.length-1])].changeVisible("display:block");
        }
    }

    function showSection(toShow:any, toShowName:string){
        defaultScreen="display:none";
        for(let i:number=0;i<visibles.length;i++){
            visibles[i].changeVisible("display:none");
        }
        if(toShow=="fromButton"){
            let arr:any[]=[aboutme, contact, skillsFolder, experiencesFolder, achievementsFolder, projectsFolder];
            toShow=arr[Object.keys(allTabs).indexOf(toShowName)];
        }

        toShow.changeVisible("display:block");
        if(!visiblesNames.includes(toShowName)){
            visibles.push(toShow);
            visiblesNames.push(toShowName);
        }
    }
</script>

<div class="flex justify-around w-[100%] h-[100vh] bg-[#49343fff] ">
    <div class="w-[20%] bg-[#2a1d24ff] border-r-[2px] border-[#f6c4dc]">
        <div class="bg-[#160e12ff] w-[100%] h-[8vh] leading-[8vh]">
            <h1 class="text-[#eca1cf] text-center mplus">☆ avishi's personal website ☆</h1>
        </div>
        <div>
            <div id="projectsFolder" class="flex justify-start box-border p-[10px] bg-[#2a1d24ff] hover:bg-[#21151b]">
                <img src={folder} alt="folder" class="w-[70px] pr-[10px]">
                <h2 class="text-[#fae6f0] block mt-auto mb-auto courier">Projects</h2>
            </div>
            <div id="experiencesFolder" class="flex justify-start box-border p-[10px] bg-[#2a1d24ff] hover:bg-[#21151b]">
                <img src={folder} alt="folder" class="w-[70px] pr-[10px]">
                <h2 class="text-[#fae6f0] block mt-auto mb-auto courier">Experiences</h2>
            </div>
            <div id="skillsFolder" class="flex justify-start box-border p-[10px] bg-[#2a1d24ff] hover:bg-[#21151b]">
                <img src={folder} alt="folder" class="w-[70px] pr-[10px]">
                <h2 class="text-[#fae6f0] block mt-auto mb-auto courier">Skills</h2>
            </div>
            <div id="achievementsFolder" class="flex justify-start box-border p-[10px] bg-[#2a1d24ff] hover:bg-[#21151b]">
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
        <div class="bg-[#89697aff] w-[100%] h-[8vh] leading-[8vh] fixed flex" style="z-index: 10">
            {#each visibles as tab, i}
                <Tab tabname={Object.keys(allTabs)[Object.keys(allTabs).indexOf(visiblesNames[i])]} xFunc={hideSection} xTarget={xTargetArr[i]} clickFunc={showSection} type={allTabs[Object.keys(allTabs)[Object.keys(allTabs).indexOf(visiblesNames[i])]]}></Tab>
            {/each}
        </div>
        <div class="bg-[#89697aff] w-[100%] h-[8vh] leading-[8vh]">
        </div>
        <div class="box-border p-[30px] text-center" style={defaultScreen}>
            <h1 class="text-white text-[100px]">(ó﹏ò｡)</h1>
            <h3 class="text-white text-[20px]">No folder or file open</h3>
        </div>
        <Aboutme bind:this={aboutme}></Aboutme>
        <Contact bind:this={contact}></Contact>
        <Skillsfolder bind:this={skillsFolder}></Skillsfolder>
        <Experiences bind:this={experiencesFolder}></Experiences>
        <Achievements bind:this={achievementsFolder}></Achievements>
        <ProjectsFolder bind:this={projectsFolder}></ProjectsFolder>
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