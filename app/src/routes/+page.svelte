<script>
    import folder from "$lib/personalwebsite_imgs/folder.png"
    import folder_opened from "$lib/personalwebsite_imgs/folder_opened.png"
    import text_file from "$lib/personalwebsite_imgs/text_file.png"
    import { text } from "@sveltejs/kit";
</script>

<div class="flex justify-around w-[100%] h-[100vh] bg-[#49343fff] ">
    <div class="w-[20%] bg-[#2a1d24ff] border-r-[2px] border-[#f6c4dc]">
        <div class="bg-[#160e12ff] w-[100%] h-[8vh] leading-[8vh]">
            <h1 class="text-[#eca1cf] text-center">☆ avishi's personal website ☆</h1>
        </div>
        <div>
            <div class="flex justify-start box-border p-[10px] bg-[#2a1d24ff] hover:bg-[#21151b]">
                <img src={folder} alt="folder" class="w-[70px] pr-[10px]">
                <h2 class="text-[#fae6f0] block mt-auto mb-auto">Projects</h2>
            </div>
            <div class="flex justify-start box-border p-[10px] bg-[#2a1d24ff] hover:bg-[#21151b]">
                <img src={folder} alt="folder" class="w-[70px] pr-[10px]">
                <h2 class="text-[#fae6f0] block mt-auto mb-auto">Hackathons</h2>
            </div>
            <div class="flex justify-start box-border p-[10px] bg-[#2a1d24ff] hover:bg-[#21151b]">
                <img src={folder} alt="folder" class="w-[70px] pr-[10px]">
                <h2 class="text-[#fae6f0] block mt-auto mb-auto">Skills</h2>
            </div>
            <div class="flex justify-start box-border p-[10px] bg-[#2a1d24ff] hover:bg-[#21151b]">
                <img src={folder} alt="folder" class="w-[70px] pr-[10px]">
                <h2 class="text-[#fae6f0] block mt-auto mb-auto">Achievements</h2>
            </div>
            <div class="flex justify-start box-border p-[10px] bg-[#2a1d24ff] hover:bg-[#21151b]">
                <img src={text_file} alt="textfile" class="w-[70px] pr-[10px]">
                <h2 class="text-[#fae6f0] block mt-auto mb-auto">about_me.md</h2>
            </div>
            <div class="flex justify-start box-border p-[10px] bg-[#2a1d24ff] hover:bg-[#21151b]">
                <img src={text_file} alt="textfile" class="w-[70px] pr-[10px]">
                <h2 class="text-[#fae6f0] block mt-auto mb-auto">contact.md</h2>
            </div>
        </div>
    </div>
    <div class="w-[80%] overflow-auto scrollbar">
        <div class="bg-[#89697aff] w-[100%] h-[8vh] leading-[8vh] fixed">
        </div>
        <br>
        <div class="w-[100%] h-[92vh] box-border p-[15px]" id="aboutMe">
            <br>
            <h1 class="text-[white] text-center text-[30px]">About Me</h1>
            <hr class="border-[#cdf6fa] border-[1px] w-[40%] m-auto shadow-[0px_0px_5px_transparent]">
            <br>
            <!--[#abf1f7]-->
            <div class="flex w-[90%] justify-around m-auto p-[15px]">
                <img class="w-[15vw] h-[15vw] rounded-full m-auto" src="https://img.spoonflower.com/c/11944215/p/f/m/a3oLNXHeS8aDuCgBdpbOC_MQqZY4x0873vwjHuO3UISqbKFNJLp1/Aqua%20Solid.jpg" alt="placeholder">
                <div class="w-[70%]">
                    <p class="text-[#fae6f0]">I’m a 16 y.o programmer from the US.</p>
                    <br>
                    <p class="text-[#fae6f0]">I started coding in fourth grade (a term I then associated with various free courses on Grok Learning and badly-designed HTML/CSS websites composed entirely of snippets from w3schools and geeksforgeeks <i>glances at my Clash Royale fan website</i>).</p>
                    <br>
                    <p class="text-[#fae6f0]">My favorite part of coding is finding creative solutions to problems I face everyday. Whether it be studying for an upcoming test, or something that facilitates my hobbies, or even just sheer boredom, I know I can turn to coding for a solution.</p>
                </div>
            </div>
            <br>
            <div class="flex">
                <div class="border-[2px] border-[#ec89c6] rounded-[12px] w-[50%]">
                    <iframe title="favorite songs" data-testid="embed-iframe" class="rounded-[12px]" src="https://open.spotify.com/embed/playlist/6Z99HBqeMAzgWFBwcuUikk?utm_source=generator&theme=0" width="100%" height="352" frameBorder="0" allowfullscreen={false} allow="autoplay; clipboard-write; encrypted-media; fullscreen; picture-in-picture" loading="lazy"></iframe>
                </div>
                <div class="w-[48%]">
                    <h3 class="text-center">⭐🎈🔁❌</h3>
                    <p class="text-center text-white">i love tsukarui</p>
                    <p class="text-[#fae6f0]">➼ huge vocaloid/prsk nerd</p>
                    <p class="text-[#fae6f0]">➼ obsessed w/ rui kamishiro</p>
                    <p class="text-[#fae6f0]">➼ sleep deprived, jacksfilms, and markiplier enjoyer</p>
                    <p class="text-[#fae6f0]">➼ ben? yes? no. hohoho</p>
                </div>
            </div>
            <br>
            <div class="border-[2px] border-[#abf1f7] box-border p-[10px] grid grid-cols-4 gap-[10px] rounded-[20px] bg-[#455e5e]">
                <div class="h-[350px] bg-[#f7dfeb] rounded-[18px]">
                    <h1 class="m-auto block">Reading</h1>
                </div>
                <div class="h-[350px] bg-[#f7dfeb] rounded-[18px]">

                </div>
                <div class="h-[350px] bg-[#f7dfeb] rounded-[18px]">

                </div>
                <div class="h-[350px] bg-[#f7dfeb] rounded-[18px]">

                </div>
            </div>
            <br>
        </div>
    </div>
</div>

<style>
    .scrollbar{
        scrollbar-width: thin;
        scrollbar-color: #ec89c6 #160e12;
    }
</style>