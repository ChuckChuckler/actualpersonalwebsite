<script lang="ts">
    import folder from "$lib/personalwebsite_imgs/folder.png";

    let visibility:string = $state("display:none");

    export function changeVisible(visible:string){
        visibility=visible;
    }
</script>

<div class="w-[100%] h-[92vh] box-border p-[15px] bg-[#49343fff]" id="skillsFolder" style={visibility}>
    <div class="flex justify-between w-[40%]">
        <div class="text-center rounded-[25px] w-[180px] box-border p-[10px] bg-[#49343f] hover:bg-[#614654]">
            <img src={folder} alt="folderimage" class="w-[150px] h-[150px] m-auto">
            <h3 class="mplus text-white">Languages</h3>
        </div>
        <div class="text-center rounded-[25px] w-[180px] box-border p-[10px] bg-[#49343f] hover:bg-[#614654]">
            <img src={folder} alt="folderimage" class="w-[150px] h-[150px] m-auto">
            <h3 class="mplus text-white">Frameworks/Tools</h3>
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