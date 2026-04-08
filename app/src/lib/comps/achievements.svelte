<script lang="ts">
    import folder from "$lib/personalwebsite_imgs/folder.png";
    import textfile from "$lib/personalwebsite_imgs/text_file.png";
    import { onMount } from "svelte";

    import Achievement from "./achievement.svelte";

    import athenaAward from "$lib/personalwebsite_imgs/hackathons_ysws/athenaward.svg";
    import dvhacks from "$lib/personalwebsite_imgs/hackathons_ysws/dvhacks.jpg";
    import kurius from "$lib/personalwebsite_imgs/hackathons_ysws/kuriushacks.png";
    import hackhumanity from "$lib/personalwebsite_imgs/hackathons_ysws/hackforhumanity.png";

    import nle from "$lib/personalwebsite_imgs/achievement_icons/nleIcon.png";
    import latin from "$lib/personalwebsite_imgs/achievement_icons/latin.png";
    import youngwriters from "$lib/personalwebsite_imgs/achievement_icons/youngwriters.png";
    import history from "$lib/personalwebsite_imgs/achievement_icons/book.png";

    let visibility:string = $state("display:none");

    let coding:any;
    let others:any;

    let fileDirectoryVisibility:string=$state("display:flex");
    let codingAchievementsVisibility:string=$state("display:none");
    let otherAchievementsVisibility:string=$state("display:none");

    type achievement = {
        placement:string,
        img:any,
        year:string
    }

    let codingAchievements:Record<string,achievement>={
        "Hack For Humanity":{
            placement:"14th-42nd Place",
            img:hackhumanity,
            year:"2026"
        },
        "Athena Award":{
            placement:"",
            img:athenaAward,
            year:"2025"
        },
        "DVHacks":{
            placement:"1st Place",
            img:dvhacks,
            year:"2025"
        },
        "KuriusHacks":{
            placement:"3rd Place",
            img:kurius,
            year:"2024"
        }
    };

    let otherAchievements:Record<string,achievement> = {
        "National Latin Exam-- Beginning":{
            placement:"Gold Medal",
            img:nle,
            year:"2023"
        },
        "National Latin Exam-- Intermediate":{
            placement:"Gold Medal",
            img:nle,
            year:"2024"
        },
        "National Latin Exam-- Intermediate Reading Comp.":{
            placement:"Gold Medal",
            img:nle,
            year:"2025"
        },
        "National Latin Exam-- Advanced Poetry":{
            placement:"Gold Medal",
            img:nle,
            year:"2026"
        },
        "Outstanding Achievement in Latin":{
            placement:"",
            img:latin,
            year:"2023"
        },
        "Short story published in Young Writers USA anthology":{
            placement:"",
            img:youngwriters,
            year:"2024"
        },
        "Essay published in school journal of history":{
            placement:"",
            img:history,
            year:"2025"
        }
    }

    onMount(()=>{
        coding.onclick=showCoding;
        others.onclick=showOthers;
    });

    function showCoding(){
        fileDirectoryVisibility="display:none";
        otherAchievementsVisibility="display:none";
        codingAchievementsVisibility="display:block";
    }

    function showOthers(){
        fileDirectoryVisibility="display:none";
        otherAchievementsVisibility="display:block";
        codingAchievementsVisibility="display:none";
    }

    function returnFiles(){
        fileDirectoryVisibility="display:flex";
        codingAchievementsVisibility="display:none";
        otherAchievementsVisibility="display:none";
    }

    export function changeVisible(visible:string){
        visibility=visible;
    }

</script>

<div class="w-[100%] h-[92vh] box-border p-[15px] bg-[#49343fff]" id="achivementsFolder" style={visibility}>
    <div class="justify-between w-[40%] flex" style={fileDirectoryVisibility}>
        <div bind:this={coding} class="text-center rounded-[25px] w-[180px] box-border p-[10px] bg-[#49343f] hover:bg-[#614654]">
            <img src={textfile} alt="textfileimage" class="w-[125px] h-[125px] mr-auto ml-auto mt-[18px]">
            <h3 class="mplus text-white mt-[7px]">coding.md</h3>
        </div>
        <div bind:this={others} class="text-center rounded-[25px] w-[180px] box-border p-[10px] bg-[#49343f] hover:bg-[#614654]">
            <img src={textfile} alt="textfileimage" class="w-[125px] h-[125px] mr-auto ml-auto mt-[18px]">
            <h3 class="mplus text-white mt-[7px]">other.md</h3>
        </div>
    </div>
    
    <div style={codingAchievementsVisibility}>
        <button onclick={returnFiles} class="text-white courier">&lt;&lt; back</button>
        <h1 class="courier text-white text-center">Coding Achievements</h1>
        <br>
        <div class="grid grid-cols-2 gap-[15px]">
            {#each Object.keys(codingAchievements) as achievement}
                <Achievement img={codingAchievements[achievement].img} achievementName={achievement} placement={codingAchievements[achievement].placement} year={codingAchievements[achievement].year}></Achievement>
            {/each}
        </div>
    </div>

    <div style={otherAchievementsVisibility}>
        <button onclick={returnFiles} class="text-white courier">&lt;&lt; back</button>
        <h1 class="courier text-white text-center">Other Achievements</h1>
        <br>
        <div class="grid grid-cols-2 gap-[15px]">
            {#each Object.keys(otherAchievements) as achievement}
                <Achievement img={otherAchievements[achievement].img} achievementName={achievement} placement={otherAchievements[achievement].placement} year={otherAchievements[achievement].year}></Achievement>
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