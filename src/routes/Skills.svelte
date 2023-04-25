<script>
  import { fade, fly } from "svelte/transition";
  import Footer from "../components/Footer.svelte";
  import { content } from "../store";
  import { marked } from "marked";
</script>

<section transition:fly={{ y: 1000 }}>
  <article>
  </article>
  <Footer />
</section>

<style>
  article {
    font-family: sans-serif;
    line-height: 1.5;
    font-size: 16px;
    font-family: "Montserrat", sans-serif;
    resize: none;
    background-color: var(--ctp-base);
    margin: -30px;
    padding: 30px;
    border-radius: 8px;
    color: var(--ctp-mauve);
    padding-bottom: 80px;
  }
</style>
