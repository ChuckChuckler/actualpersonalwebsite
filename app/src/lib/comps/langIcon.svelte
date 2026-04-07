<script lang="ts">
    let { iconName, iconImg } = $props();
</script>

<div class="text-center rounded-[25px] w-[150px] box-border p-[10px] bg-[#49343f] leading-[50px] hover:bg-[#614654]">
    <img src={iconImg} alt="html" class="w-[100px] h-[100px] m-auto">
    <h3 class="mplus text-white">{iconName}</h3>
</div>