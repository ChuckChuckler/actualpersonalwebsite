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

    import defaultCursor from "$lib/mikuCursors/Normal.cur";

    let defaultScreen:string=$state("display:block");

    let visibles:any[] = $state([]);
    let visiblesNames:string[]=$state([]);

    let lastSelected:string="";
    let currentSelected:string="";

    let aboutme:any;
    let contact:any;
    let skillsFolder:any;
    let experiencesFolder:any;
    let achievementsFolder:any;
    let projectsFolder:any;


    let xTargetArr:any[]=$state([aboutme, contact, skillsFolder, experiencesFolder, achievementsFolder, projectsFolder]);
    let tabsArr:any[]=$state([]);

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
        if(visiblesNames.indexOf(lastSelected)==-1){
            if(visibles.length==0){
                defaultScreen = "display:block";
            }else{
                arr[Object.keys(allTabs).indexOf(visiblesNames[visiblesNames.length-1])].changeVisible("display:block");
                tabsArr[visiblesNames.length-1].changeBgColor(true);
            }
        }else{
            arr[Object.keys(allTabs).indexOf(visiblesNames[visiblesNames.indexOf(lastSelected)])].changeVisible("display:block");
            tabsArr[visiblesNames.indexOf(lastSelected)].changeBgColor(true);
        }
    }

    function showSection(toShow:any, toShowName:string){
        defaultScreen="display:none";
        for(let i:number=0;i<visibles.length;i++){
            visibles[i].changeVisible("display:none");
            tabsArr[i].changeBgColor(false);
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

        tabsArr[visiblesNames.indexOf(toShowName)].changeBgColor(true);

        lastSelected=currentSelected;
        currentSelected=toShowName;
    }
</script>

<div class="flex justify-around w-[100%] h-[100vh] bg-[#49343fff]" style={`cursor:url(${defaultCursor}),auto`}>
    <div class="w-[20%] bg-[#2a1d24ff] border-r-[2px] border-[#f6c4dc]">
        <div class="bg-[#160e12ff] w-[100%] h-[8vh] leading-[8vh]">
            <h1 class="text-[#eca1cf] text-center mplus text-[1.2vw]">☆ avishi's personal website ☆</h1>
        </div>
        <div>
            <div id="projectsFolder" class="flex justify-start box-border p-[10px] bg-[#2a1d24ff] hover:bg-[#21151b]">
                <img src={folder} alt="folder" class="w-[5.5vw] pr-[10px]">
                <h2 class="text-[#fae6f0] block mt-auto mb-auto courier text-[1.3vw]">Projects</h2>
            </div>
            <div id="experiencesFolder" class="flex justify-start box-border p-[10px] bg-[#2a1d24ff] hover:bg-[#21151b]">
                <img src={folder} alt="folder" class="w-[5.5vw] pr-[10px]">
                <h2 class="text-[#fae6f0] block mt-auto mb-auto courier text-[1.3vw]">Experiences</h2>
            </div>
            <div id="skillsFolder" class="flex justify-start box-border p-[10px] bg-[#2a1d24ff] hover:bg-[#21151b]">
                <img src={folder} alt="folder" class="w-[5.5vw] pr-[10px]">
                <h2 class="text-[#fae6f0] block mt-auto mb-auto courier text-[1.3vw]">Skills</h2>
            </div>
            <div id="achievementsFolder" class="flex justify-start box-border p-[10px] bg-[#2a1d24ff] hover:bg-[#21151b]">
                <img src={folder} alt="folder" class="w-[5.5vw] pr-[10px]">
                <h2 class="text-[#fae6f0] block mt-auto mb-auto courier text-[1.3vw]">Achievements</h2>
            </div>
            <div id="aboutme" class="flex justify-start box-border p-[10px] bg-[#2a1d24ff] hover:bg-[#21151b]">
                <img src={text_file} alt="textfile" class="w-[5.5vw] pr-[10px]">
                <h2 class="text-[#fae6f0] block mt-auto mb-auto courier text-[1.3vw]">about_me.md</h2>
            </div>
            <div id="contact" class="flex justify-start box-border p-[10px] bg-[#2a1d24ff] hover:bg-[#21151b]">
                <img src={text_file} alt="textfile" class="w-[5.5vw] pr-[10px]">
                <h2 class="text-[#fae6f0] block mt-auto mb-auto courier text-[1.3vw]">contact.md</h2>
            </div>
        </div>
    </div>
    <div class="w-[80%] overflow-auto scrollbar">
        <div class="bg-[#89697aff] w-[100%] h-[8vh] leading-[8vh] fixed flex">
            {#each visibles as tabElm, i}
                <Tab bind:this={tabsArr[i]} tabname={Object.keys(allTabs)[Object.keys(allTabs).indexOf(visiblesNames[i])]} xFunc={hideSection} xTarget={xTargetArr[i]} clickFunc={showSection} type={allTabs[Object.keys(allTabs)[Object.keys(allTabs).indexOf(visiblesNames[i])]]}></Tab>
            {/each}
        </div>
        <div class="bg-[#89697aff] w-[100%] h-[8vh] leading-[8vh]">
        </div>
        <div class="box-border p-[30px] text-center" style={defaultScreen}>
            <h1 class="text-white text-[10vw]">(ó﹏ò｡)</h1>
            <h3 class="text-white text-[1.8vw]">No folder or file open</h3>
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