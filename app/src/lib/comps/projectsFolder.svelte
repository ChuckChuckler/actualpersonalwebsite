<script lang="ts">
    import textfile from "$lib/personalwebsite_imgs/text_file.png";
    import { onMount } from "svelte";

    import FeaturedProject from "./featuredProject.svelte";
    import OtherProject from "./otherProject.svelte";

    import apollo from "$lib/personalwebsite_imgs/previews/apolloPreview.png";
    import notmyelement from "$lib/personalwebsite_imgs/previews/notmyelementPreview.png";
    import weissSchwarz from "$lib/personalwebsite_imgs/previews/weissSchwarzSimulator.png";
    import animalBook from "$lib/personalwebsite_imgs/previews/myAnimalBookPhoto1.png";
    
    import treeAssistant from "$lib/personalwebsite_imgs/otherProjects/treeAssistant.png";
    import punnettPractice from "$lib/personalwebsite_imgs/otherProjects/punnett.png";
    import athena from "$lib/personalwebsite_imgs/otherProjects/athena.png";
    import tldw from "$lib/personalwebsite_imgs/otherProjects/tldw.png";
    import quadratics from "$lib/personalwebsite_imgs/otherProjects/quadratics.png";
    import verbConjugator from "$lib/personalwebsite_imgs/otherProjects/verbconjugator.png";
    import ermify from "$lib/personalwebsite_imgs/otherProjects/ermify.png";
    import sillyText from "$lib/personalwebsite_imgs/otherProjects/sillytext.png";
    import vigenere from "$lib/personalwebsite_imgs/otherProjects/vigenerecipher.png";
    import ptspeller from "$lib/personalwebsite_imgs/otherProjects/ptspeller.png";
    import ermify2 from "$lib/personalwebsite_imgs/otherProjects/ermify2.png";
    import lewisStructure from "$lib/personalwebsite_imgs/otherProjects/lewis.png";
    import gpacalc from "$lib/personalwebsite_imgs/otherProjects/gpacalc.png";
    import astronautRescue from "$lib/personalwebsite_imgs/otherProjects/astronautrescue.png";
    import classifying from "$lib/personalwebsite_imgs/otherProjects/matterClassification.png";
    import personalwebsite1 from "$lib/personalwebsite_imgs/otherProjects/oldPersonalWeb.png";
    import pirateHangman from "$lib/personalwebsite_imgs/otherProjects/piratehangman.png";
    import fortGrumio from "$lib/personalwebsite_imgs/otherProjects/fortgrumio.png";
    import dailycode from "$lib/personalwebsite_imgs/otherProjects/dailyCode.png";
    import complexes from "$lib/personalwebsite_imgs/otherProjects/complexes.png";
    import quotegenerator from "$lib/personalwebsite_imgs/otherProjects/inspoQuotes.png";
    import personalwebsite2 from "$lib/personalwebsite_imgs/otherProjects/alsoOldPersonalWebsite.png";
    import danda from "$lib/personalwebsite_imgs/otherProjects/daphneAndApollo.png";

    let featured:any;
    let others:any;

    let visibility:string = $state("display:none");

    let fileDirectoryVisibility=$state("display:flex");
    let featuredVisibility=$state("display:none");
    let othersVisibility=$state("display:none");

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

    type otherProject={
        preview:any,
        desc:string,
        repo:string,
        demo:string
    }

    let otherProjects:Record<string,otherProject>={
        "Daphne and Apollo":{
            preview:danda,
            desc:"A horror game I made for my Latin project where you play as Daphne running from Apollo in a forest. First time making a 3D game!!",
            repo:"",
            demo:"https://sluggysoup.itch.io/daphne-and-apollo-project"
        },
        "Personal Website #2":{
            preview:personalwebsite2,
            desc:"My second attempt at making a personal website which I abandoned 80% of the way through because I decided I didn't like it",
            repo:"https://github.com/ChuckChuckler/new-personal-web",
            demo:"https://new-personal-web-five.vercel.app/"
        },
        '"Inspirational" Quote Generator':{
            preview:quotegenerator,
            desc:'A simple "inspirational" quote generator that generates wacky, nonsensical, or borderline threatening quotes. All quotes are said by my friends, teachers, or random people I happened to overhear. Made to help me start learning Flutter.',
            repo:"https://github.com/ChuckChuckler/quote-app",
            demo:"https://quote-app-1cdu.vercel.app/"
        },
        "Complexes":{
            preview:complexes,
            desc:"A 2D platformer where users answer personality quiz-style questions, then fight a boss that changes according to their answers. Made for Parthenon.",
            repo:"https://github.com/iisalut/Actual_athena",
            demo:"https://sluggysoup.itch.io/complexes"
        },
        "DailyCode":{
            preview:dailycode,
            desc:"A web app where a daily (although weekly is more feasible) coding prompt is displayed. Users can create accounts and upload projects that they have made adhering to that prompt (games, websites, anything); they can vote on or comment on others' projects as well.",
            repo:"https://github.com/ChuckChuckler/dailyCode/tree/main",
            demo:"https://dailycode-priv-frontend.vercel.app/"
        },
        "Fort Grumio":{
            preview:fortGrumio,
            desc:"Made for my Latin project about Roman forts. Learn Grumio's story, explore Fort Grumio, and talk to GrumioBot! Yes, Grumio from the CLC.",
            repo:"https://github.com/ChuckChuckler/fortgrumio",
            demo:"https://fortgrumio.onrender.com/"
        },
        "Pirate Hangman":{
            preview:pirateHangman,
            desc:"Pirate-themed hangman, but you have to catch the falling letters to guess them! A tiny website for SayCheese, made to fit entirely in a QR code.",
            repo:"https://github.com/ChuckChuckler/piratehangman",
            demo:"https://piratehangman-3rptw3anp-avishi-sharmas-projects.vercel.app/"
        },
        "Personal Website #1":{
            preview:personalwebsite1,
            desc:"My old personal website! Cool design, but lacking in information.",
            repo:"https://github.com/ChuckChuckler/personalwebsite",
            demo:"https://personalwebsite-chi-ashen.vercel.app/"
        },
        "Classifying Matter":{
            preview:classifying,
            desc:"A simple drag-and-drop chemistry game about classifying types of matter.",
            repo:"https://github.com/ChuckChuckler/matter-classification/tree/main",
            demo:"https://matter-classification.onrender.com/"
        },
        "Astronaut Rescue":{
            preview:astronautRescue,
            desc:"A 2D website game where you play as an astronaut escaping a crashing ship, all while practicing your Algebra II solving over C skills.",
            repo:"https://github.com/ChuckChuckler/astronaut-rescue",
            demo:"https://astronaut-rescue.vercel.app/main.html"
        },
        "GPACalc":{
            preview:gpacalc,
            desc:"A weighted GPA calculator that saves users' classes through account creation.",
            repo:"https://github.com/ChuckChuckler/gpacalc-rehaul",
            demo:"https://avishis3939.pythonanywhere.com/"
        },
        "Lewis Structures":{
            preview:lewisStructure,
            desc:"A website for practicing Lewis Structures. Featuring more terrible CSS!",
            repo:"https://github.com/ChuckChuckler/lewis",
            demo:"https://jazzy-pavlova-6f7aba.netlify.app/"
        },
        "Ermify2":{
            preview:ermify2,
            desc:"The sequel. A web app where users can ask questions, and be answered in the most 'erm, actually' way possible. You don't even know what 2+2 is???",
            repo:"https://github.com/ChuckChuckler/ermify2",
            demo:"https://www.youtube.com/watch?v=0SGpE4m_GpM&feature=youtu.be",
        },
        "PTSpeller":{
            preview:ptspeller,
            desc:"A website that spells out user input using elements from the periodic table. Warning: terrible CSS choices.",
            repo:"https://github.com/ChuckChuckler/ptspeller",
            demo:"https://ptspeller.vercel.app/main.html"
        },
        "Vigenere Cipher":{
            preview:vigenere,
            desc:"A Vigenere Cipher encoder/decoder. Works both ways!",
            repo:"https://github.com/ChuckChuckler/vigenerecipher",
            demo:"https://vigenerecipher.vercel.app/encoder.html"
        },
        "SillyText":{
            preview:sillyText,
            desc:"A website where users can get 'silly' versions of the text they input. It inserts emojis after every word.",
            repo:"https://github.com/ChuckChuckler/sillytext",
            demo:"https://silly-text.tiiny.site/"
        },
        "Ermify":{
            preview:ermify,
            desc:"A web app that turns user input into comically eloquent verbage.",
            repo:"https://github.com/ChuckChuckler/ermify",
            demo:"https://www.youtube.com/watch?v=UMbyFLsqkRw&feature=youtu.be"
        },
        "Verb Conjugator":{
            preview:verbConjugator,
            desc:"A website to practice conjugating verbs in Latin. Kind of buggy. Might remake!",
            repo:"https://github.com/ChuckChuckler/verbconjugator",
            demo:"https://verb-conjugates.tiiny.site/"
        },
        "Quadratics":{
            preview:quadratics,
            desc:"Quadratic equations practice website. yay to algebra",
            repo:"https://github.com/ChuckChuckler/quadratics",
            demo:"https://silver-vivian-71.tiiny.site/"
        },
        "TLDW":{
            preview:tldw,
            desc:"A web app that takes a youtube link and summarizes the video.",
            repo:"https://github.com/ChuckChuckler/tldw",
            demo:"https://www.youtube.com/watch?v=-9xCfvGnWGw&feature=youtu.be"
        },
        "Athena":{
            preview:athena,
            desc:"A web app where users can upload notes and take AI-generated practice tests.",
            repo:"https://github.com/ChuckChuckler/athena",
            demo:""
        },
        "Punnett Practice":{
            preview:punnettPractice,
            desc:"A very simple website for practicing punnett squares.",
            repo:"https://github.com/ChuckChuckler/punnettpractice",
            demo:"https://punnettpractice.vercel.app/"
        },
        "TreeAssistant":{
            preview:treeAssistant,
            desc:"A web app that game-ifies the process of planting trees; it returns nearby places for users to plant trees, and grants XP for each tree planted. 3rd place winner of KuriusHacks March 2024.",
            repo:"https://github.com/ChuckChuckler/TreeAssistant",
            demo:"https://devpost.com/software/treeassistant"
        }
    }

    export function changeVisible(visible:string){
        visibility=visible;
    }

    onMount(()=>{
        featured.onclick=showFeatured;
        others.onclick=showOthers;

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
        othersVisibility="display:none";
    }

    function showFeatured(){
        featuredVisibility="display:block";
        othersVisibility="display:none";
        fileDirectoryVisibility="display:none";
    }

    function showOthers(){
        featuredVisibility="display:none";
        othersVisibility="display:block";
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
    
    <div style={othersVisibility}>
        <button onclick={returnFiles} class="text-white courier">&lt;&lt; back</button>
        <br>
        <h1 class="text-white courier text-center text-[30px]">~Other Projects~</h1>
        <br>
        <div class="grid grid-cols-3 gap-[15px]">
            {#each Object.keys(otherProjects) as project}
                <OtherProject pName={project} img={otherProjects[project].preview} desc={otherProjects[project].desc} repo={otherProjects[project].repo} demo={otherProjects[project].demo}></OtherProject>
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