<script lang="ts">
    let { iconName, iconImg } = $props();
</script>

<div class="text-center rounded-[25px] md:w-[150px] w-[15vw] box-border p-[10px] bg-[#49343f] leading-[50px] hover:bg-[#614654]">
    <img src={iconImg} alt="html" class="md:w-[100px] md:h-[100px] w-[12vw] h-[12vw] m-auto">
    <h3 class="mplus text-white md:text-[18px] text-[1.8vw]">{iconName}</h3>
</div>