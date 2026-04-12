<script lang="ts">
    import folder from "$lib/personalwebsite_imgs/folder.png";
    import { onMount } from "svelte";

    import LangIcon from "./langIcon.svelte";
    
    import html from "$lib/personalwebsite_imgs/icons/languages/html.png";
    import css from "$lib/personalwebsite_imgs/icons/languages/css.png";
    import js from "$lib/personalwebsite_imgs/icons/languages/js.png";
    import ts from "$lib/personalwebsite_imgs/icons/languages/ts.png";
    import java from "$lib/personalwebsite_imgs/icons/languages/java.png";
    import py from "$lib/personalwebsite_imgs/icons/languages/py.png";

    import node from "$lib/personalwebsite_imgs/icons/frameworks/nodejs.png";
    import gsap from "$lib/personalwebsite_imgs/icons/frameworks/gsap.png";
    import mongo from "$lib/personalwebsite_imgs/icons/frameworks/mongodb.svg";
    import react from "$lib/personalwebsite_imgs/icons/frameworks/react.png";
    import tailwind from "$lib/personalwebsite_imgs/icons/frameworks/tailwind.svg";
    import svelte from "$lib/personalwebsite_imgs/icons/frameworks/svelte.png";
    import express from "$lib/personalwebsite_imgs/icons/frameworks/expressjs.svg";
    import flask from "$lib/personalwebsite_imgs/icons/frameworks/flask.png";
    import godot from "$lib/personalwebsite_imgs/icons/frameworks/godot.png";

    let languages:Record<string,any> = {
        "HTML.png":html,
        "CSS.png":css,
        "Javascript.png":js,
        "Typescript.png":ts,
        "Java.png":java,
        "Python.png":py
    }

    let frameworksDict:Record<string,any>={
        "NodeJS.png":node,
        "GSAP.png":gsap,
        "MongoDB.png":mongo,
        "React.png":react,
        "Tailwind.png":tailwind,
        "Svelte.png":svelte,
        "ExpressJS.png":express,
        "Flask.png":flask,
        "Godot.png":godot
    }

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
            showFrameworks();
        }
    })

    export function changeVisible(visible:string){
        visibility=visible;
    }

    function showSkills(){
        languagesDirectoryVisibility="display:block";
        fileDirectoryVisibility="display:none";
        frameworksDirectoryVisibility="display:none";
    }

    function showFrameworks(){
        frameworksDirectoryVisibility="display:block";
        languagesDirectoryVisibility="display:none";
        fileDirectoryVisibility="display:none";
    }

    function returnFiles(){
        frameworksDirectoryVisibility="display:none";
        languagesDirectoryVisibility="display:none";
        fileDirectoryVisibility="display:flex";
    }
</script>

<div class="w-[100%] h-[92vh] box-border p-[15px] bg-[#49343fff]" id="skillsFolder" style={visibility}>
    <div class="flex justify-between w-[42%]" style={fileDirectoryVisibility}>
        <div class="text-center rounded-[25px] w-[15vw] box-border p-[10px] bg-[#49343f] hover:bg-[#614654]" bind:this={skills}>
            <img src={folder} alt="folderimage" class="w-[13vw] h-[13vw] m-auto">
            <h3 class="mplus text-[1.3vw] text-white">Languages</h3>
        </div>
        <div class="text-center rounded-[25px] w-[15vw] box-border p-[10px] bg-[#49343f] hover:bg-[#614654]" bind:this={frameworks}>
            <img src={folder} alt="folderimage" class="w-[13vw] h-[13vw] m-auto">
            <h3 class="mplus text-[1.3vw] text-white">Frameworks/Tools</h3>
        </div>
    </div>

    <div style={languagesDirectoryVisibility}>
    <button onclick={returnFiles} class="text-white courier">&lt;&lt; back</button>
    <br>
        <div class="grid grid-cols-5">
            {#each Object.keys(languages) as language}
                <LangIcon iconName={language} iconImg={languages[language]}></LangIcon>
            {/each}
        </div>
    </div>

    <div style={frameworksDirectoryVisibility}>
    <button onclick={returnFiles} class="text-white courier">&lt;&lt; back</button>
    <br>
        <div class="grid grid-cols-5">
            {#each Object.keys(frameworksDict) as framework}
                <LangIcon iconName={framework} iconImg={frameworksDict[framework]}></LangIcon>
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