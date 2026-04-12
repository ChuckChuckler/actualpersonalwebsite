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

    let iframe:any;
    let iframeVisibility=$state("display:none");
    let iframeSrc=$state("https://tailwindcss.com/docs/top-right-bottom-left");

    type achievement = {
        placement:string,
        img:any,
        year:string,
        link:string
    }

    let codingAchievements:Record<string,achievement>={
        "Hack For Humanity":{
            placement:"14th-42nd Place",
            img:hackhumanity,
            year:"2026",
            link: "https://devpost.com/software/my-animal-book"
        },
        "Athena Award":{
            placement:"",
            img:athenaAward,
            year:"2025",
            link: "https://athena.hackclub.com/award?id=LCINvIBF"
        },
        "DVHacks":{
            placement:"1st Place",
            img:dvhacks,
            year:"2025",
            link:"https://devpost.com/software/apollo-fa1up2"
        },
        "KuriusHacks":{
            placement:"3rd Place",
            img:kurius,
            year:"2024",
            link:"https://devpost.com/software/treeassistant"
        }
    };

    let otherAchievements:Record<string,achievement> = {
        "National Latin Exam-- Beginning":{
            placement:"Gold Medal",
            img:nle,
            year:"2023",
            link:""
        },
        "National Latin Exam-- Intermediate":{
            placement:"Gold Medal",
            img:nle,
            year:"2024",
            link:""
        },
        "National Latin Exam-- Intermediate Reading Comp.":{
            placement:"Gold Medal",
            img:nle,
            year:"2025",
            link:""
        },
        "National Latin Exam-- Advanced Poetry":{
            placement:"Gold Medal",
            img:nle,
            year:"2026",
            link:""
        },
        "Outstanding Achievement in Latin":{
            placement:"",
            img:latin,
            year:"2023",
            link:""
        },
        "Short story published in Young Writers USA anthology":{
            placement:"",
            img:youngwriters,
            year:"2024",
            link:""
        },
        "Essay published in school journal of history":{
            placement:"",
            img:history,
            year:"2025",
            link:""
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

    function hideIframe(){
        iframeVisibility="display:none";
    }

    function updateIframe(link:string){
        iframeSrc=link;
        iframe.onload=function(){
            iframeVisibility="display:block";
        }
    }

    export function changeVisible(visible:string){
        visibility=visible;
    }

</script>

<div class="w-[100%] h-[92vh] box-border p-[15px] bg-[#49343fff]" id="achivementsFolder" style={visibility}>
    <div class="justify-between w-[42%] flex" style={fileDirectoryVisibility}>
        <div bind:this={coding} class="text-center rounded-[25px] w-[15vw] box-border p-[10px] bg-[#49343f] hover:bg-[#614654]">
            <img src={textfile} alt="textfileimage" class="w-[11vw] h-[11vw] mr-auto ml-auto mt-[18px]">
            <h3 class="mplus text-white text-[1.3vw] mt-[7px]">coding.md</h3>
        </div>
        <div bind:this={others} class="text-center rounded-[25px] w-[15vw] box-border p-[10px] bg-[#49343f] hover:bg-[#614654]">
            <img src={textfile} alt="textfileimage" class="w-[11vw] h-[11vw] mr-auto ml-auto mt-[18px]">
            <h3 class="mplus text-white text-[1.3vw] mt-[7px]">other.md</h3>
        </div>
    </div>
    
    <div style={codingAchievementsVisibility}>
        <button onclick={returnFiles} class="text-white courier">&lt;&lt; back</button>
        <h1 class="courier text-white text-center">Coding Achievements</h1>
        <br>
        <div class="grid grid-cols-2 gap-[15px]">
            {#each Object.keys(codingAchievements) as achievement}
                <button onclick={function(){
                    if(codingAchievements[achievement].link!=""){
                        updateIframe(codingAchievements[achievement].link);
                    }
                }}>
                    <Achievement img={codingAchievements[achievement].img} achievementName={achievement} placement={codingAchievements[achievement].placement} year={codingAchievements[achievement].year}></Achievement>
                </button>
            {/each}
        </div>
        <div class="fixed w-[70%] h-[90%] top-[5%] left-[50%] transform translate-x-[-50%] translate-y-[-5%] bg-[#1d2429] border-[2px] border-[#abf1f7] rounded-[20px]" style={iframeVisibility}>
            <button class="text-[#abf1f7] ml-[95.5%] mt-[0.125%] text-[25px] mplus" onclick={hideIframe}>x</button>
            <iframe bind:this={iframe} src={iframeSrc} class="select-none w-[100%] h-[92.5%] absolute bottom-0 left-[50%] transform translate-x-[-50%] rounded-b-[20px]" title="freaky"></iframe>
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