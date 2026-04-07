<script lang="ts">
    import folder from "$lib/personalwebsite_imgs/folder.png";
    import textfile from "$lib/personalwebsite_imgs/text_file.png";
    import { onMount } from "svelte";

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

    let hackathonsList:Record<string,any>={
        "Hack for Humanity.exe":hackforhumanity,
        "Parthenon.exe":parthenon,
        "Blueprint 2025.exe":bp25,
        "Counterspell Boston.exe":counterspell,
        "DVHacks.exe":dvhacks,
        "saycheese.exe":saycheese,
        "High Seas.exe":highseas,
        "KuriusHacks.exe":kuriushacks,
        "Blueprint 2024.exe":bp24,
        "Wonderland.exe":wonderland,
        "Chargerhacks.exe":charger
    }

    let visibility:string = $state("display:none");

    let hackathons:any;
    let others:any;

    let fileDirectoryVisibility=$state("display:flex");
    let hackathonVisibility=$state("display:none");

    onMount(()=>{
        hackathons.onclick=showHackathons;
    })

    export function changeVisible(visible:string){
        visibility=visible;
    }
    
    function showHackathons(){
        fileDirectoryVisibility="display:none";
        hackathonVisibility="display:block";
    }

    function returnFiles(){
        hackathonVisibility="display:none";
        fileDirectoryVisibility="display:flex";
    }
</script>

<div class="w-[100%] h-[92vh] box-border p-[15px] bg-[#49343fff]" id="skillsFolder" style={visibility}>
    <div class="justify-between w-[40%] flex" style={fileDirectoryVisibility}>
        <div class="text-center rounded-[25px] w-[180px] box-border p-[10px] bg-[#49343f] hover:bg-[#614654]" bind:this={hackathons}>
            <img src={folder} alt="folderimage" class="w-[150px] h-[150px] m-auto">
            <h3 class="mplus text-white">Hackathons</h3>
        </div>
        <div class="text-center rounded-[25px] w-[180px] box-border p-[10px] bg-[#49343f] hover:bg-[#614654]" bind:this={others}>
            <img src={textfile} alt="textfileimage" class="w-[150px] h-[150px] m-auto">
            <h3 class="mplus text-white">others.md</h3>
        </div>
    </div>

    <div style={hackathonVisibility}>
        <button onclick={returnFiles} class="text-white courier">&lt;&lt; back</button>
        <br>
        <div class="grid grid-cols-4">
            {#each Object.keys(hackathonsList) as hackathon}
                <HackathonIcon iconImage={hackathonsList[hackathon]} iconName={hackathon}></HackathonIcon>
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