<script>
	import { onMount } from "svelte";
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

    $: amazing = 0;
</script>
<div class="reveal">
    <div class="slides">
        <p>Revealed</p>
        <section>
            Svelte + RevealJS
            {amazing}
            <button on:click={()=>amazing++}>Reactive AF</button>
        </section>
        <section>Slide 2</section>
    </div>
</div>
<div class="lower">
    <p>Not Revealed</p>
</div>

<style>
    .reveal {
        height: 50%;
    }
    .lower {
        height: 50%;
        background-color: black;
    }
</style>