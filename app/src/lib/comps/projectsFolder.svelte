<script lang="ts">
    import textfile from "$lib/personalwebsite_imgs/text_file.png";
    import { onMount } from "svelte";

    import FeaturedProject from "./featuredProject.svelte";

    import apollo from "$lib/personalwebsite_imgs/previews/apolloPreview.png";
    import notmyelement from "$lib/personalwebsite_imgs/previews/notmyelementPreview.png";
    import weissSchwarz from "$lib/personalwebsite_imgs/previews/weissSchwarzSimulator.png";
    import animalBook from "$lib/personalwebsite_imgs/previews/myAnimalBookPhoto1.png";
    import { ObjectFlags } from "typescript";

    let featured:any;
    let others:any;

    let visibility:string = $state("display:none");

    let fileDirectoryVisibility=$state("display:flex");
    let featuredVisibility=$state("display:none");

    let featuredIndex:number=0;

    let featured0:any;
    let featured1:any;
    let featured2:any;
    let featured3:any;

    let featuredsArr:any[]=[featured0, featured1, featured2, featured3];

    type techstack={
        frontend:string,
        backend:string
    }

    type featuredProject={
        img:any,
        desc:string,
        completed:string,
        time:string,
        techStack:techstack,
        repo:string,
        demo:string
    }

    let featuredProjects:Record<string,featuredProject>={
        "PRSK Weiss Schwarz Simulator":{
            img:weissSchwarz,
            desc:"An online inventory and pulling simulator for Project Sekai EN Weiss Schwarz. One of my favorite projects I've made to date!",
            completed:"First beta completed Jan 2026",
            time:"38hrs",
            techStack:{
                frontend:"Sveltekit, CSS3, JS",
                backend:"Sveltekit, MongoDB, Crypto (now deprecated :c)",
            },
            repo:"https://github.com/ChuckChuckler/weiss-schwarz-pjsk",
            demo:"https://ws-prsk.vercel.app/"
        },
        "My Animal Book":{
            img:animalBook,
            desc:"An online animal journal that teaches users about endangered animals in their area and how to protect them. Also one of my favorites",
            completed:"First beta completed Feb 2026",
            time:"42hrs",
            techStack:{
                frontend:"Sveltekit, GSAP, Tailwind, CSS3",
                backend:"Sveltekit, MongoDB, bcrypt, a LOT of APIs-- see the github for more info"
            },
            repo:"https://github.com/ChuckChuckler/my-animal-book",
            demo:"https://my-animal-book.vercel.app/"
        },
        "Apollo":{
            img:apollo,
            desc:"A web app that enables transcription of lectures into notes in real time. 1st place winner of DVHacks",
            completed:"Feb 2025 (no deploy link)",
            time:"16hrs (straight with no sleep x_x)",
            techStack:{
                frontend:"HTML5, CSS3, JS",
                backend:"Flask, sqlite, SpeechRecognition, GeminiAPI"
            },
            repo:"https://github.com/ChuckChuckler/apollo",
            demo:"https://devpost.com/software/apollo-fa1up2"
        },
        "That's Not My Element!":{
            img:notmyelement,
            desc:"A 2D chemistry game based on That's Not My Neighbor! featuring elements from the periodic table. Another one of my favorites!",
            completed:"Jan 2025",
            time:"10hrs",
            techStack:{
                frontend:"HTML5, CSS3, JS",
                backend:"none"
            },
            repo:"https://github.com/ChuckChuckler/notmyelement",
            demo:"https://fluffy-sfogliatella-5528a0.netlify.app/main"
        }
    }

    export function changeVisible(visible:string){
        visibility=visible;
    }

    onMount(()=>{
        featured.onclick=showFeatured;
        for(let i:number=0; i<Object.keys(featuredProjects).length;i++){
            let featuredElm=document.getElementById(`featured${i}`);
            if(featuredElm!=null){
                featuredsArr.push(featuredElm);
            }
        }
    });

    function returnFiles(){
        featuredVisibility="display:none";
        fileDirectoryVisibility="display:flex";
    }

    function showFeatured(){
        featuredVisibility="display:block";
        fileDirectoryVisibility="display:none";
    }

    function moveForward(){
        featuredIndex+=1;
        if(featuredIndex==Object.keys(featuredProjects).length){
            featuredIndex=0;
        }
        
        for(let i:number=0;i<featuredsArr.length;i++){
            featuredsArr[i].swap(featuredIndex);
        }
    }

    function moveBackwards(){
        featuredIndex-=1;
        if(featuredIndex==-1){
            featuredIndex=Object.keys(featuredProjects).length-1;
        }
        
        for(let i:number=0;i<featuredsArr.length;i++){
            featuredsArr[i].swap(featuredIndex);
        }
    }
</script>

<div class="w-[100%] h-[92vh] box-border p-[15px] bg-[#49343fff]" id="achivementsFolder" style={visibility}>
    <div style={fileDirectoryVisibility} class="justify-between w-[40%]">
        <div class="text-center rounded-[25px] w-[180px] box-border p-[10px] bg-[#49343f] hover:bg-[#614654]" bind:this={featured}>
            <img src={textfile} alt="textfileimage" class="w-[125px] h-[125px] mr-auto ml-auto mt-[18px]">
            <h3 class="mplus text-white mt-[7px]">featured_projects.md</h3>
        </div>
        <div class="text-center rounded-[25px] w-[180px] box-border p-[10px] bg-[#49343f] hover:bg-[#614654]" bind:this={others}>
            <img src={textfile} alt="textfileimage" class="w-[125px] h-[125px] mr-auto ml-auto mt-[18px]">
            <h3 class="mplus text-white mt-[7px]">other_projects.md</h3>
        </div>
    </div>
    <div style={featuredVisibility}>
        <button onclick={returnFiles} class="text-white courier">&lt;&lt; back</button>
        <br>
        <h1 class="text-white courier text-center text-[30px]">~Featured Projects~</h1>
        <div>
            {#each Object.keys(featuredProjects) as project}
                <FeaturedProject bind:this={featuredsArr[Object.keys(featuredProjects).indexOf(project)]} pName={project} img={featuredProjects[project].img} desc={featuredProjects[project].desc} completed={featuredProjects[project].completed} time={featuredProjects[project].time} frontend={featuredProjects[project].techStack.frontend} backend={featuredProjects[project].techStack.backend} repo={featuredProjects[project].repo} demo={featuredProjects[project].demo} id={`featured${Object.keys(featuredProjects).indexOf(project)}`}></FeaturedProject>
            {/each}
            <div class="w-[90%] m-auto">
                <button class="w-[48%] text-white text-[30px] mplus font-black" onclick={moveBackwards}>&lt;&lt;</button>
                <button class="w-[48%] text-white text-[30px] mplus font-black" onclick={moveForward}>&gt;&gt;</button>
            </div>
        </div>
    </div>
</div>

<style>
    .courier{
        font-family: "Courier Prime", monospace
    }

    .mplus{
        font-family: "M PLUS Rounded 1c", sans-serif;
    }
</style>