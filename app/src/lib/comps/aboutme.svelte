<script lang="ts">
    import mikuyay from "$lib/personalwebsite_imgs/miku2.jpg";
    import futureEve from "$lib/personalwebsite_imgs/futureEve.png";
    
    let visibility:string = $state("display:none");

    export function changeVisible(visible:string){
        visibility=visible;
    }
</script>

<div class="w-[100%] h-[92vh] box-border p-[15px] bg-[#49343fff]" id="aboutMe" style={visibility}>
    <h1 class="text-[white] text-center text-[3vw] courier">⟡ About Me ⟡</h1>
    <hr class="border-[#cdf6fa] border-[1px] w-[40%] m-auto shadow-[0px_0px_5px_transparent]">
    <br>
    <!--[#abf1f7]-->
    <div class="flex w-[90%] justify-around m-auto p-[15px]">
        <img class="w-[15vw] h-[15vw] rounded-full m-auto border-[1.5px] border-[#cdf6fa]" src={mikuyay} alt="placeholder">
        <div class="w-[70%]">
            <p class="text-[#fae6f0] mplus text-[1.3vw]">I’m a 16 y.o programmer from the US.</p>
            <br>
            <p class="text-[#fae6f0] mplus text-[1.3vw]">I started coding in fourth grade (a term I then associated with various free courses on Grok Learning and badly-designed HTML/CSS websites composed entirely of snippets from w3schools and geeksforgeeks <i>glances at my Clash Royale fan website</i>).</p>
            <br>
            <p class="text-[#fae6f0] mplus text-[1.3vw]">My favorite part of coding is finding creative solutions to problems I face everyday. Whether it be studying for an upcoming test, or something that facilitates my hobbies, or even just sheer boredom, I know I can turn to coding for a solution.</p>
        </div>
    </div>
    <br>
    <hr>
    <br>
    <div class="flex justify-between">
        <div class="border-[2px] border-[#ec89c6] rounded-[12px] w-[50%]">
            <iframe title="favorite songs" data-testid="embed-iframe" style="border-radius:12px" src="https://open.spotify.com/embed/playlist/6Z99HBqeMAzgWFBwcuUikk?utm_source=generator&theme=0" width="100%" height="352" allowfullscreen={false} allow="autoplay; clipboard-write; encrypted-media; fullscreen; picture-in-picture" loading="lazy"></iframe>
        </div>
        <div class="w-[48%]">
            <h3 class="text-center text-[1.5vw]">⭐🎈🔁❌</h3>
            <br>
            <p class="text-[#fae6f0] mplus text-[1.3vw]">➼ huge vocaloid/prsk nerd</p>
            <p class="text-[#fae6f0] mplus text-[1.3vw]">➼ obsessed w/ rui kamishiro</p>
            <p class="text-[#fae6f0] mplus text-[1.3vw]">➼ sleep deprived, jacksfilms, and markiplier enjoyer</p>
            <p class="text-[#fae6f0] mplus text-[1.3vw]">➼ i love music</p>
            <p class="text-[#fae6f0] mplus text-[1.3vw]">➼ D1 javascript/typescript glazer</p>
            <p class="text-[#fae6f0] mplus text-[1.3vw]">➼ ben? yes? no. hohoho</p>
        </div>
    </div>
    <br>
    <hr>
    <br>
    <div class="flex justify-around">
        <img class="w-[49%]" src="https://github-readme-stats.hackclub.dev/api/wakatime?username=2598&api_domain=hackatime.hackclub.com&theme=rose_pine&custom_title=Hackatime+Stats&cache_seconds=0&langs_count=5" alt="hackatime stats">
        <img class="w-[49%] object-cover h-[14.8vw] rounded-[5px] border-[1.5px] border-[#fae6f0]" src={futureEve} alt="future eve by hit music artist sasakure.uk">
    </div>
    <br>
    <div class="bg-black w-[100%] box-border p-[10px] rounded-[15px] m-auto border-[1.5px] border-[#fae6f0]">
        <img class="m-auto w-[100%]" alt="Hackatime activity heatmap" src="https://heatmap.shymike.dev?id=2598&timezone=America%2FNew_York&labels=true&year=current&theme=dark">
    </div>
    <br>
    <p class="text-[1vw] courier text-[#fae6f0] text-center">This website was made with Svelte, Typescript, and Tailwind</p>
    <br>
    <hr>
    <br>
    <h1 class="text-center text-[2.5vw] text-[#fce1f6] courier">❀ Hobbies ❀</h1>
    <br>
    <div class="border-[2px] border-[#abf1f7] box-border p-[10px] grid grid-cols-4 gap-[10px] rounded-[20px] bg-[#455e5e]">
        <div class="h-[60vh] bg-[#1d2429] rounded-[18px] relative box-border p-[13px] overflow-hidden scrollHidden">
            <div class="w-[100%] h-[100%] relative opacity-100 hover:opacity-0 transition-opacity duration-500 ease-out bg-[#1d2429] z-5">
                <h1 class="text-[1.7vw] courier text-[#fce1f6] absolute left-[50%] top-[50%] transform translate-x-[-50%] translate-y-[-50%]">Reading</h1>
            </div>
            <div class="absolute w-[90%] h-[100%] overflow-auto top-5">
                <p class="text-[1.25vw] text-[#fce1f6] bg-[#1d2429] mplus">I  love reading good books, especially classics. Nabokov is my favorite author.<br>I also love reading Greek and Roman poetry. And by extension, I love all things Latin! Currently taking it in school (and hope to take Greek in college). Agricola tres porcos in proelio necavit et sum discipula Linguae Latinae (ദ്ദി˙ᗜ˙)</p>
            </div>
        </div>
        <div class="h-[60vh] bg-[#1d2429] rounded-[18px] relative box-border p-[13px] overflow-hidden scrollHidden">
            <div class="w-[100%] h-[100%] relative opacity-100 hover:opacity-0 transition-opacity duration-500 ease-out bg-[#1d2429] z-5">
                <h1 class="text-[1.7vw] courier text-[#fce1f6] absolute left-[50%] top-[50%] transform translate-x-[-50%] translate-y-[-50%]">Writing</h1>
            </div>
            <div class="absolute w-[90%] h-[100%] overflow-auto top-5">
                <p class="text-[1.25vw] text-[#fce1f6] bg-[#1d2429] mplus">I've been writing maybe longer than I've been coding. I absolutely love writing, especially creative writing. I like writing poems and short stories. And fanfiction. No, you cannot have my Ao3 (◑_◑)</p>
            </div>
        </div>
        <div class="h-[60vh] bg-[#1d2429] rounded-[18px] relative box-border p-[13px] overflow-hidden scrollHidden">
            <div class="w-[100%] h-[100%] relative opacity-100 hover:opacity-0 transition-opacity duration-500 ease-out bg-[#1d2429] z-5">
                <h1 class="text-[1.7vw] courier text-[#fce1f6] absolute left-[50%] top-[50%] transform translate-x-[-50%] translate-y-[-50%]">Drawing</h1>
            </div>
            <div class="absolute w-[90%] h-[100%] overflow-auto top-5">
                <p class="text-[1.25vw] text-[#fce1f6] bg-[#1d2429] mplus">Not much to say here. I like drawing. I'm not particularly exceptional at it, but I like it anyways. My #1 favorite thing to draw is my wife Rui Kamishiro ♡(˃͈ ˂͈ )</p>
            </div>
        </div>
        <div class="h-[60vh] bg-[#1d2429] rounded-[18px] relative box-border p-[13px] overflow-hidden scrollHidden">
            <div class="w-[101%] h-[100%] relative opacity-100 hover:opacity-0 transition-opacity duration-500 ease-out bg-[#1d2429] z-5">
                <h1 class="text-[1.7vw] courier text-[#fce1f6] absolute left-[50%] top-[50%] transform translate-x-[-50%] translate-y-[-50%]">Music</h1>
            </div>
            <div class="absolute w-[90%] h-[100%] overflow-auto top-5">
                <p class="text-[1.25vw] text-[#fce1f6] bg-[#1d2429] mplus">If there was one thing I was just as passionate as coding about, if not more, it would be music. I play piano. I'm a member of both choir and the acapella group at my school. Most of all, I love music theory and making music! Perchance I'll be able to get a Soundcloud or something running sometime soon (˶ˆᗜˆ˵)</p>
            </div>
        </div>
    </div>
    <br>
</div>

<style>
    .scrollHidden{
        scrollbar-width: none;
    }

    .courier{
        font-family: "Courier Prime", monospace
    }

    .mplus{
        font-family: "M PLUS Rounded 1c", sans-serif;
    }
</style>