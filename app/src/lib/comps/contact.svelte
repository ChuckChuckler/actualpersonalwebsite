<script lang="ts">
    import github from "$lib/personalwebsite_imgs/github.png";

    let visibility:string = $state("display:none");

    export function changeVisible(visible:string){
        visibility=visible;
    }
</script>

<div class="w-[100%] h-[92vh] box-border p-[15px] bg-[#49343fff]" id="aboutMe" style={visibility}>
    <h1 class="text-[white] text-center text-[30px] courier">⟡ Contact ⟡</h1>
    <hr class="border-[#cdf6fa] border-[1px] w-[40%] m-auto shadow-[0px_0px_5px_transparent]">
    <br>
    <div class="grid grid-rows-2 gap-[20px]">
        <div class="flex justify-around bg-red-500">
            <img src={github} alt="github icon" class="w-[125px]">
            <h1 class="courier text-[#fae6f0] text-[30px] block mt-auto mb-auto">ChuckChuckler</h1>
        </div>
        <div class="flex justify-around bg-red-500">
            <img src={github} alt="email icon" class="w-[125px]">
            <h1 class="courier text-[#fae6f0] text-[30px] block mt-auto mb-auto">avishi39sharma@gmail.com</h1>
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