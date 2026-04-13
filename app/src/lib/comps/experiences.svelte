<script lang="ts">
    import folder from "$lib/personalwebsite_imgs/folder.png";
    import textfile from "$lib/personalwebsite_imgs/text_file.png";
    import { onMount } from "svelte";

    import defaultCursor from "$lib/mikuCursors/Normal.cur";
    import clickerCursor from "$lib/mikuCursors/Link.cur";
    import backCursor from "$lib/mikuCursors/Alternate.cur";

    import HackathonIcon from "./hackathonIcon.svelte";

    import bp24 from "$lib/personalwebsite_imgs/hackathons_ysws/bp2024.svg";
    import bp25 from "$lib/personalwebsite_imgs/hackathons_ysws/bp2025.png";
    import charger from "$lib/personalwebsite_imgs/hackathons_ysws/chargerhacks.png";
    import counterspell from "$lib/personalwebsite_imgs/hackathons_ysws/counterspell.png";
    import dvhacks from "$lib/personalwebsite_imgs/hackathons_ysws/dvhacks.jpg";
    import highseas from "$lib/personalwebsite_imgs/hackathons_ysws/highseas.png";
    import kuriushacks from "$lib/personalwebsite_imgs/hackathons_ysws/kuriushacks.png";
    import parthenon from "$lib/personalwebsite_imgs/hackathons_ysws/parthenon.png";
    import saycheese from "$lib/personalwebsite_imgs/hackathons_ysws/saycheese.png";
    import wonderland from "$lib/personalwebsite_imgs/hackathons_ysws/wonderland.png";
    import sleepover from "$lib/personalwebsite_imgs/hackathons_ysws/sleepover.webp";
    import hackforhumanity from "$lib/personalwebsite_imgs/hackathons_ysws/hackforhumanity.png";

    type hackathon = {
        image:any,
        link:string
    }

    let hackathonsList:Record<string,hackathon>={
        "Hack for Humanity.exe":{
            image:hackforhumanity,
            link:"https://hack-for-humanity-26.devpost.com/"
        },
        "Parthenon.exe":{
            image:parthenon,
            link:"https://parthenon.hackclub.com/"
        },
        "Blueprint 2025.exe":{
            image:bp25,
            link:"https://bparchive.hackmit.org/2025/"
        },
        "Counterspell Boston.exe":{
            image:counterspell,
            link:"https://counterspell.hackclub.com/"
        },
        "DVHacks.exe":{
            image:dvhacks,
            link:"https://dvhacks25.devpost.com/"
        },
        "saycheese.exe":{
            image:saycheese,
            link:"https://saycheese.hackclub.com/"
        },
        "High Seas.exe":{
            image:highseas,
            link:"https://highseas.hackclub.com/"
        },
        "KuriusHacks.exe":{
            image:kuriushacks,
            link:"https://kuriushacks-march-edition.devpost.com/"
        },
        "Blueprint 2024.exe":{
            image:bp24,
            link:"https://bparchive.hackmit.org/2024/"
        },
        "Wonderland.exe":{
            image:wonderland,
            link:"https://wonderland.hackclub.com/"
        },
        "Chargerhacks.exe":{
            image:charger,
            link:"https://chargerhacks-2023.devpost.com/"
        }
    }

    let visibility:string = $state("display:none");

    let hackathons:any;
    let others:any;

    let iframe:any;

    let fileDirectoryVisibility=$state("display:flex");
    let hackathonVisibility=$state("display:none");
    let othersVisibility=$state("display:none");

    let iframeVisibility=$state("display:none");

    let iframeSrc=$state("https://tailwindcss.com/docs/top-right-bottom-left");

    onMount(()=>{
        hackathons.onclick=showHackathons;
        others.onclick=showOthers;
    })

    export function changeVisible(visible:string){
        visibility=visible;
    }
    
    function showHackathons(){
        fileDirectoryVisibility="display:none";
        othersVisibility="display:none";
        hackathonVisibility="display:block";
    }

    function showOthers(){
        fileDirectoryVisibility="display:none";
        othersVisibility="display:block";
        hackathonVisibility="display:none";
    }

    function returnFiles(){
        hackathonVisibility="display:none";
        othersVisibility="display:none";
        fileDirectoryVisibility="display:flex";
    }

    function hideIframe(){
        iframeVisibility="display:none";
    }

    function updateIframe(link:string){
        iframeSrc=link;
        iframe.onload=function(){
            iframeVisibility="display:block";
        }
    }
</script>

<div class="w-[100%] h-[92vh] box-border p-[15px] bg-[#49343fff]" id="skillsFolder" style={visibility}>
    <div class="justify-between w-[42%] flex" style={fileDirectoryVisibility}>
        <div class="text-center rounded-[25px] w-[15vw] box-border p-[10px] bg-[#49343f] hover:bg-[#614654]" bind:this={hackathons}>
            <img src={folder} alt="folderimage" class="w-[13vw] h-[13vw] m-auto">
            <h3 class="mplus text-white text-[1.3vw]">Hackathons</h3>
        </div>
        <div class="text-center rounded-[25px] w-[15vw] box-border p-[10px] bg-[#49343f] hover:bg-[#614654]" bind:this={others}>
            <img src={textfile} alt="textfileimage" class="md:w-[11vw] md:h-[11vw] h-[9vw] w-[9w] mr-auto ml-auto mt-[18px]">
            <h3 class="mplus text-white text-[1.3vw] mt-[7px]">others.txt</h3>
        </div>
    </div>

    <div style={hackathonVisibility} class="relative">
        <button style={`cursor:url(${backCursor}),auto`} onclick={returnFiles} class="text-white courier md:text-[1.2vw] text-[1.6vw]">&lt;&lt; back</button>
        <br>
        <div class="grid grid-cols-3 md:grid-cols-4">
            {#each Object.keys(hackathonsList) as hackathon}
                <button onclick={function(){updateIframe(hackathonsList[hackathon].link)}}>
                    <HackathonIcon iconImage={hackathonsList[hackathon].image} iconName={hackathon}></HackathonIcon>
                </button>
            {/each}
        </div>
        <div class="fixed w-[70%] h-[90%] top-[5%] left-[50%] transform translate-x-[-50%] translate-y-[-5%] bg-[#1d2429] border-[2px] border-[#abf1f7] rounded-[20px]" style={iframeVisibility}>
            <button class="text-[#abf1f7] ml-[95.5%] mt-[0.125%] text-[25px] mplus" style={`cursor:url(${clickerCursor}),auto`} onclick={hideIframe}>x</button>
            <iframe bind:this={iframe} src={iframeSrc} class="select-none w-[100%] h-[92.5%] absolute bottom-0 left-[50%] transform translate-x-[-50%] rounded-b-[20px]" title="freaky"></iframe>
        </div>
    </div>

    <div style={othersVisibility}>
        <button style={`cursor:url(${backCursor}),auto`} onclick={returnFiles} class="text-white courier md:text-[1.2vw] text-[1.6vw]">&lt;&lt; back</button>
        <h1 class="courier text-center text-white underline text-[25px]">Other</h1>
        <br>
        <div class="w-[60%] m-auto">
            <li class="text-[#fae6f0] mplus text-[18px]">National Latin Honors Society</li>
            <li class="text-[#fae6f0] mplus text-[18px]">Latin Club member</li>
            <li class="text-[#fae6f0] mplus text-[18px]">Acapella club member</li>
            <li class="text-[#fae6f0] mplus text-[18px]">Women in Computer Science member</li>
            <li class="text-[#fae6f0] mplus text-[18px]">Hack Club member</li>
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