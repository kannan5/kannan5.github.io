<script>
  import "../app.css";
  import Footer from "../components/Footer.svelte";
  import Header from "../components/Header.svelte";
  let y;
  let innerHeight = 0;
  let innerWidth = 0;

  function goToTop() {
    document.body.scrollIntoView();
  }
</script>

<div
  class={"fixed bottom-0 w-full duration-200 flex p-10 z-[10] " +
    (y > 0
      ? " opacity-full pointer-events-auto "
      : " pointer-events-none opacity-0 ")}
>
  <button
    on:click={goToTop}
    class="ml-auto rounded-full text-violet-400 px-3 sm:px-4 hover:bg-slate-80 cursor-pointer"
  >
    <i class="fa-solid fa-arrow-up"></i>
  </button>
</div>
<Header {y} />
<slot />
<Footer />
<svelte:window bind:scrollX={y} bind:innerHeight bind:innerWidth />
