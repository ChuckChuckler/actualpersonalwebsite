<script lang="ts">
    let { iconName, iconImage } = $props();
</script>

<div class="text-center rounded-[25px] box-border p-[10px] bg-[#49343f] leading-[50px] hover:bg-[#614654]">
    <img src={iconImage} alt="html" class="object-contain md:h-[8vw] h-[100px] m-auto">
    <h3 class="mplus text-white md:text-[1.2vw] text-[1.7vw]">{iconName}</h3>
</div>