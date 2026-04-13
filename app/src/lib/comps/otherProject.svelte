<script lang="ts">
    let { pName, img, desc, repo, demo }=$props();

    import clickerCursor from "$lib/mikuCursors/Link.cur";

    function redirect(link:string){
        window.open(link, "_blank");
    }
</script>

<div class="overflow-auto scroll bg-[#291d23] hover:bg-[#1C1418] border-[1.5px] border-[#f6c4dc] box-border p-[15px] rounded-[20px]">
    <h1 class="courier text-center text-[#D9FCFF]">{pName}</h1>
    <br class="sm:none">
    <div class="h-[20vw]">
        <img src={img} alt={pName} class="object-cover border-[1.5px] border-[#D9FCFF] sm:w-[15vw] sm:h-[15vw] w-[25vw] h-[25vw] auto rounded-[15px] m-auto">
        <br>
        <p class="mplus text-[#fae6f0]">{desc}</p>
        <br>
        <div class="flex justify-between sm:w-[100%] m-auto">
            <button style={`cursor:url(${clickerCursor}),auto`} onclick={function(){redirect(repo)}} class="text-[#FCF0F6] mplus border-[2px] border-[#D9FCFF] w-[14vw] rounded-[15px] h-[40px] bg-[#47303E] hover:bg-[#3b2633]">Repo</button>
            <button style={`cursor:url(${clickerCursor}),auto`} onclick={function(){redirect(demo)}} class="text-[#FCF0F6] mplus border-[2px] border-[#D9FCFF] w-[14vw] rounded-[15px] h-[40px] bg-[#47303E] hover:bg-[#3b2633]">Demo</button>
        </div>
        <br>
    </div>
</div>

<style>
    .courier{
        font-family: "Courier Prime", monospace
    }

    .mplus{
        font-family: "M PLUS Rounded 1c", sans-serif;
    }
    .scroll{
        scrollbar-width:none;
    }
</style>