<script>
    let {img, achievementName, placement, year}=$props();
</script>

<div class="flex justify-around bg-[#291d23] hover:bg-[#1C1418] border-[1.5px] border-[#abf1f7] rounded-[20px] box-border p-[15px] h-[130px]">
    <img class="object-contain w-[100px]" src={img} alt={achievementName}>
    <div class="w-[70%]">
        <h1 class="text-[#fae6f0] mplus">{achievementName}</h1>
        <h2 class="text-[#fae6f0] mplus">{placement}</h2>
        <h3 class="text-[#fae6f0] mplus">{year}</h3>
    </div>
</div>

<style>
    .mplus{
        font-family: "M PLUS Rounded 1c", sans-serif;
    }
</style>