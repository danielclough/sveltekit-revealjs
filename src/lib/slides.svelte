<script>
	import { onMount } from "svelte";
    import constants from "$lib/constants";
	import Description from "./lower.md";

    const date = new Date();

    onMount(() => {
        Reveal.initialize({
            dependencies: [
                { src: 'plugin/markdown/marked.js' },
                { src: 'plugin/markdown/markdown.js' },
                { src: 'plugin/notes/notes.js', async: true },
                { src: 'plugin/highlight/highlight.js', async: true, callback: function () { hljs.initHighlightingOnLoad(); } }
            ]
        });
    })

    // Fullscreen
    let fullscreen = false;

	function toggleFullscreen() {
        fullscreen = !fullscreen
	}

    $: amazing = 0;
</script>

<div class="reveal" style="height:{fullscreen ? 'calc(100% - 3rem)' : '50%'}">
    <div class="slides">
        <p>Revealed</p>
        <section>
            <h1>
                Svelte + RevealJS 
            </h1>
            <h2>
                (Reactive AF)
            </h2>
            {amazing}
            <br>
            <button on:click={()=>amazing++}>click me</button>
        </section>
        <section>Slide 2</section>
    </div>
</div>

<div class="lower"  style="height:{fullscreen ? '3rem' : '100%'};" >
    <hr>
    <div class="info" style="display: {fullscreen ? 'none' : 'block'};">
        <Description />
    </div>

    <div class="copyright">
        <p style="font-style:italic;">&copy{constants.author} {date.getFullYear()} — {constants.title}: {constants.subtitle}</p>
    </div>
    <button on:click={()=>toggleFullscreen()}>{fullscreen ? "View Details" : "Fullscreen"}</button>
</div>

<style>
    .reveal {
        height: 100%;
    }
    .lower {
        height: 50%;
        background-color: transparent;
    }
    .lower button {
        position:absolute;
        bottom:.3rem;
        right: 1rem;
    }
    .copyright {
        position:absolute;
        bottom:.3rem;
    }
    .copyright p {
        font-size: small;
        padding-left: .5rem;
        color: white;
        margin: 0.25rem;
    }
</style>