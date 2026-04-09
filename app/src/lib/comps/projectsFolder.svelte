<script lang="ts">
    import textfile from "$lib/personalwebsite_imgs/text_file.png";
    import { onMount } from "svelte";

    import apollo from "$lib/personalwebsite_imgs/previews/apolloPreview.png";
    import notmyelement from "$lib/personalwebsite_imgs/previews/notmyelementPreview.png";
    import weissSchwarz from "$lib/personalwebsite_imgs/previews/weissSchwarzSimulator.png";
    import animalBook from "$lib/personalwebsite_imgs/previews/myAnimalBookPhoto1.png";

    let featured:any;
    let others:any;

    let visibility:string = $state("display:none");

    let fileDirectoryVisibility=$state("display:flex");
    let featuredVisibility=$state("display:none");

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
    })

    function returnFiles(){
        featuredVisibility="display:none";
        fileDirectoryVisibility="display:flex";
    }

    function showFeatured(){
        featuredVisibility="display:block";
        fileDirectoryVisibility="display:none";
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
            <div class="bg-[#291d23] box-border p-[15px] rounded-[25px] border-[1.5px] border-[#fae6f0]">
                <h1 class="text-center courier text-[#D9FCFF]">{project}</h1>
                <br>
                <div class="flex justify-between w-[100%]">
                    <img src={featuredProjects[project].img} alt={`${project} preview`} class="w-[32.5vw] h-[25vw] object-cover rounded-[20px] border-[1.5px] border-[#D9FCFF]">
                    <div class="w-[53%]">
                        <h3 class="text-[#FCF0F6] mplus">{featuredProjects[project].desc}</h3>
                        <br>
                        <h3 class="text-[#FCF0F6] mplus">{featuredProjects[project].completed}</h3>
                        <br>
                        <h3 class="text-[#FCF0F6] mplus">{featuredProjects[project].time}</h3>
                        <br>
                        <h3 class="text-[#FCF0F6] mplus">Tech Stack:</h3>
                        <p class="text-[#FCF0F6] mplus indent-[5%]">Frontend: {featuredProjects[project].techStack.frontend}</p>
                        <p class="text-[#FCF0F6] mplus indent-[5%]">Backend: {featuredProjects[project].techStack.backend}</p>
                        <br>
                        <br>
                        <button class="text-[#FCF0F6] mplus border-[2px] border-[#D9FCFF]">Repo</button>
                        <button class="text-[#FCF0F6] mplus border-[2px] border-[#D9FCFF]">Demo</button>
                    </div>
                </div>
            </div>
            {/each}
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