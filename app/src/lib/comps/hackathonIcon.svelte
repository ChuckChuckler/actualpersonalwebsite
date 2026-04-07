<script lang="ts">
    let { iconName, iconImage } = $props();
</script>

<div class="text-center rounded-[25px] box-border p-[10px] bg-[#49343f] leading-[50px] hover:bg-[#614654]">
    <img src={iconImage} alt="html" class="object-contain h-[100px] m-auto">
    <h3 class="mplus text-white">{iconName}</h3>
</div>