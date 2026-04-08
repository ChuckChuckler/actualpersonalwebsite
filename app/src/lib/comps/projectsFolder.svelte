<script lang="ts">
    import textfile from "$lib/personalwebsite_imgs/text_file.png";

    let featured:any;
    let others:any;

    let visibility:string = $state("display:none");

    let folderDirectoryVisible="display:flex";

    export function changeVisible(visible:string){
        visibility=visible;
    }
</script>

<div class="w-[100%] h-[92vh] box-border p-[15px] bg-[#49343fff]" id="achivementsFolder" style={visibility}>
    <div style={folderDirectoryVisible} class="justify-between w-[40%]">
        <div class="text-center rounded-[25px] w-[180px] box-border p-[10px] bg-[#49343f] hover:bg-[#614654]" bind:this={featured}>
            <img src={textfile} alt="textfileimage" class="w-[125px] h-[125px] mr-auto ml-auto mt-[18px]">
            <h3 class="mplus text-white mt-[7px]">featured_projects.md</h3>
        </div>
        <div class="text-center rounded-[25px] w-[180px] box-border p-[10px] bg-[#49343f] hover:bg-[#614654]" bind:this={others}>
            <img src={textfile} alt="textfileimage" class="w-[125px] h-[125px] mr-auto ml-auto mt-[18px]">
            <h3 class="mplus text-white mt-[7px]">other_projects.md</h3>
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