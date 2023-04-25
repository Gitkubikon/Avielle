<script>
  // @ts-nocheck

  import { getCookieValue, onUltraMount, setCookie } from "./utils/shenanigans";
  import { page, updateElements } from "./store";
  import Trailer from "./utils/UltraFocus.svelte";
  import Side from "./routes/nav/Side.svelte";
  import Home from "./routes/Home.svelte";
  import About from "./routes/About.svelte";
  import Cv from "./routes/CV.svelte";
  import Skills from "./routes/Skills.svelte";
  import Contact from "./routes/Contact.svelte";
  import Foo from "./routes/404.svelte";
  import Admin from "./admin/AdminPage.svelte";
  import StyleGuide from "./routes/StyleGuide.svelte";
  import Footer from "./components/Footer.svelte";

  const pages = [
    { id: "Home", component: Home },
    { id: "About", component: About },
    { id: "CV", component: Cv },
    { id: "Skills", component: Skills },
    { id: "Contact", component: Contact },
    { id: "Footer", component: Footer },
    { id: "Foo", component: Foo },
    { id: "Admin", component: Admin },
    { id: "StyleGuide", component: StyleGuide },
  ];

  const getComponent = function () {
    try {
      return pages.find((p) => p.id === $page).component;
    } catch (e) {
      return Foo;
    }
  };

  if (!getCookieValue("token")) {

    setCookie("token", "")

  }

  let currentTry = 0;
  const sequence = ["g", "i", "g", "a", "c", "h", "a", "d"];

  document.addEventListener("keydown", (event) => {
    if (event.key === sequence[currentTry]) {
      currentTry++;
      if (currentTry === sequence.length) {
        page.set("Admin");
        currentTry = 0;
      }
    } else {
      currentTry = 0;
    }
  });
</script>

<main class="w-screen h-screen">
  <!-- <Top /> -->
  <div class="flex flex-row">
    <Side />
    <div id="sectionback">
      <svelte:component this={getComponent()} />
    </div>
  </div>
</main>

<Trailer />
<!-- <Test /> -->

<style>
</style>
