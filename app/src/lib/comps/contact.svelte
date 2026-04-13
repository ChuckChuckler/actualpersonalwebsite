<script lang="ts">
    import github from "$lib/personalwebsite_imgs/github.png";
    import email from "$lib/personalwebsite_imgs/email.png";
    import { onMount } from "svelte";

    import defaultCursor from "$lib/mikuCursors/Normal.cur";
    import clickerCursor from "$lib/mikuCursors/Link.cur";

    let githubLink:any;

    onMount(()=>{
        githubLink.onclick=function(){redirect("https://github.com/ChuckChuckler")};
    });

    let visibility:string = $state("display:none");

    export function changeVisible(visible:string){
        visibility=visible;
    }

    function redirect(link:string){
        window.open(link, "_blank");
    }
</script>

<div class="w-[100%] h-[92vh] box-border p-[15px] bg-[#49343fff]" id="contact" style={visibility}>
    <h1 class="text-[white] text-center text-[2.5vw] courier">⟡ Contact ⟡</h1>
    <hr class="border-[#cdf6fa] border-[1px] w-[40%] m-auto shadow-[0px_0px_5px_transparent]">
    <br>
    <div class="grid grid-rows-2 gap-[30px] w-[65%] h-[30vw] m-auto bg-[#291d23] box-border p-[20px] rounded-[15px] border-[1.5px] border-[#fae6f0]">
        <div class="flex justify-around w-[50%] bg-[#291d23]">
            <img src={github} alt="github icon" class="w-[10vw] h-[10vw] mt-auto mb-auto ml-[2vw]">
            <div class="m-auto pl-[20px]">
                <h3 class="text-[1.5vw] text-[#fae6f0] mplus block mt-auto mb-auto" style={`cursor:url(${defaultCursor}),auto`}>Github</h3>
                <h1 bind:this={githubLink} class="text-[2.2vw] courier text-[#fae6f0] block mt-auto mb-auto hover:underline" style={`cursor:url(${clickerCursor}),auto`}>ChuckChuckler</h1>
            </div>
        </div>
        <div class="flex justify-around w-[70%] bg-[#291d23]">
            <img src={email} alt="email icon" class="w-[10vw] h-[10vw] mt-auto mb-auto ml-[2vw]">
            <div class="m-auto pl-[20px]">
                <h3 class="text-[1.5vw] text-[#fae6f0] mplus block mt-auto mb-auto" style={`cursor:url(${defaultCursor}),auto`}>Email</h3>
                <h1 class="text-[2.2vw] courier text-[#fae6f0] block mt-auto mb-auto">avishi39sharma@gmail.com</h1>
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