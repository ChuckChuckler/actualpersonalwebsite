<script lang="ts">
    import folder from "$lib/personalwebsite_imgs/folder.png";
    import { onMount } from "svelte";

    import html from "$lib/personalwebsite_imgs/icons/languages/html.png";
    import css from "$lib/personalwebsite_imgs/icons/languages/css.png";
    import js from "$lib/personalwebsite_imgs/icons/languages/js.png";
    import ts from "$lib/personalwebsite_imgs/icons/languages/ts.png";
    import java from "$lib/personalwebsite_imgs/icons/languages/java.png";
    import py from "$lib/personalwebsite_imgs/icons/languages/py.png";

    let languages:Record<string,any> = {
        HTML:html,
        CSS:css,
        Javascript:js,
        Typescript:ts,
        Java:java,
        Python:py
    }

    let fileDirectory:any;
    let languagesDirectory:any;
    let frameworksDirectory:any;

    let fileDirectoryVisibility=$state("display:flex");
    let languagesDirectoryVisibility=$state("display:none");
    let frameworksDirectoryVisibility=$state("display:none");

    let skills:any;
    let frameworks:any;

    let visibility:string = $state("display:none");

    onMount(()=>{
        skills.onclick=function(){
            showSkills();
        }

        frameworks.onclick=function(){
            console.log("hi");
        }
    })

    export function changeVisible(visible:string){
        visibility=visible;
    }

    function showSkills(){
        languagesDirectoryVisibility="display:grid";
        fileDirectoryVisibility="display:none";
    }
</script>

<div class="w-[100%] h-[92vh] box-border p-[15px] bg-[#49343fff]" id="skillsFolder" style={visibility}>
    <div class="flex justify-between w-[40%]" bind:this={fileDirectory} style={fileDirectoryVisibility}>
        <div class="text-center rounded-[25px] w-[180px] box-border p-[10px] bg-[#49343f] hover:bg-[#614654]" bind:this={skills}>
            <img src={folder} alt="folderimage" class="w-[150px] h-[150px] m-auto">
            <h3 class="mplus text-white">Languages</h3>
        </div>
        <div class="text-center rounded-[25px] w-[180px] box-border p-[10px] bg-[#49343f] hover:bg-[#614654]" bind:this={frameworks}>
            <img src={folder} alt="folderimage" class="w-[150px] h-[150px] m-auto">
            <h3 class="mplus text-white">Frameworks/Tools</h3>
        </div>
    </div>
    <div bind:this={languagesDirectory} style={languagesDirectoryVisibility} class="grid-cols-5">
        {#each Object.keys(languages) as language}
            <div class="text-center rounded-[25px] w-[150px] box-border p-[10px] bg-[#49343f] leading-[50px] hover:bg-[#614654]">
                <img src={languages[language]} alt="html" class="w-[100px] h-[100px] m-auto">
                <h3 class="mplus text-white">{language}</h3>
            </div>
        {/each}
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