<script>
  import Step from "../components/Step.svelte";
  import Mouse from "../components/Mouse.svelte";
  import { onMount } from "svelte";
  // import { typewriter } from "../components/Typewriter.svelte";

  let displayText = "";
  let showTypewriter = false;

  function handleClick() {
    displayText = "We are not yet live. Check back in 2 weeks!";
    showTypewriter = true;
  }

  function typewriter(node, { speed = 1 }) {
    const valid =
      node.childNodes.length === 1 &&
      node.childNodes[0].nodeType === Node.TEXT_NODE;

    if (!valid) {
      throw new Error(
        `This transition only works on elements with a single text node child`
      );
    }

    const text = node.textContent;
    const duration = text.length / (speed * 0.01);

    return {
      duration,
      tick: (t) => {
        const i = Math.trunc(text.length * t);
        node.textContent = text.slice(0, i);
      },
    };
  }

  onMount(() => {
    // Resetting the typewriter state when component is mounted
    showTypewriter = false;
  });

  let steps = [
    {
      name: "Webfurl",
      icon: "fa-solid fa-cart-shopping",
      description:
        "WebFurl enables you uncover what technologies have been used to build a web application or page.",
    },
    {
      name: "Eventifurl",
      icon: "fa-regular fa-calendar",
      description:
        "Reduce the burden of confirming payments when managing your event. Save money.",
    },
  ];

  let benefits = [
    {
      metric: "Data-Powered Insights",
      name: "Webfurl",
      description:
        "Uncover the technologies used to build web applications or pages. Harness the power of data to gain insights into the technological landscape of the online world.",
    },
    {
      metric: "Efficient Event Management",
      name: "Eventifurl",
      description:
        "Streamline payment confirmations in event management. Save time and resources by leveraging data to ease the burden of managing events and handling payments.",
    },
    {
      metric: "Innovative Data Solutions",
      name: "Datafurl Features",
      description:
        "Explore the simplicity and power of data with Datafurl. Embrace trial and error to discover innovative data solutions that can enhance your workflow and decision-making processes.",
    },
  ];
</script>

<main class="flex flex-col flex-1 p-4">
  <!-- <Mouse /> -->
  <section
    id="introPage"
    class="grid grid-cols-1 lg:grid-cols-2 hap-10 ml-8 py-8 sm:py-14"
  >
    <div
      class="flex flex-col lg:justify-center lg:text-left gap-6 md:gap-8 lg:hap-10"
    >
      <h2 class="font-semibold text-4xl sm:text-5xl md:text-6xl">
        This is <span class="roboto text-violet-400">Datafurl</span> <br />
        Unfurl <span class="roboto text-violet-400">your data</span>
      </h2>
      <p class="text-base sm:text-lg md:text-xl">
        We are focused on harnessing <span class="text-violet-400"
          >the power of simple data</span
        >
        but open to
        <span class="roboto text-violet-400">trial and error</span>
      </p>
      <button
        on:click={handleClick}
        class="blueShadow mx-auto lg:mr-auto lg:ml-0 text-base sm:text-lg md:text-xl roboto relative overflow-hidden px-6 py-3 group rounded-full bg-white text-slate-950"
      >
        <div
          class="absolute top-0 right-full w-full h-full bg-violet-400 opacity-20 group-hover:translate-x-full z-0 duration-200"
        />
        <h4 class="relative z-9">Get in touch &rarr;</h4>
      </button>
      {#if showTypewriter}
        <div transition:typewriter>{displayText}</div>
      {/if}
    </div>
    <div class="relative shadow-2xl grid place-items-center sm: pt-10">
      <img
        src={"images/spin.gif"}
        alt="Spinning Loading Running GIF"
        class="object-cover z-[2] max-h-[70vh]"
      />
    </div>
  </section>
  <section id="focus" class="py-20 lg:py-32 flex flex-col gap-24">
    <div class="flex flex-col gap-2 text-center">
      <h6 class="text-large sm:text-xl md:text-2xl">Our target areas.</h6>
      <h3 class="font-semibold text-3xl sm:text-4xl md:text-5xl">
        Curious to <span class="roboto text-violet-400">see</span> our work?
      </h3>
    </div>
    <a
      href="https://www.youtube.com/watch?v=dQw4w9WgXcQ"
      target="_blank"
      class="mx-auto px-4 py-2 rounded-md border border-solid border-white flex items-center gap-2 -mb-4 sm:-mb-0 -mt-10 hover:border-violet-700 duration-200"
    >
      <i class="fa-regular fa-circle-play" />
      <p>Watch the video</p>
    </a>
    <div class="grid grid-cols-1 lg:grid-cols-2 gap-12 lg:gap-10">
      <Step step={steps[0]}>
        <p>
          WebFurl enables you <strong class="text-violet-400"
            >uncover what technologies</strong
          > have been used to build a web application or page.
        </p>
      </Step>
      <Step step={steps[1]}>
        <p>
          Reduce the burden of <strong class="text-violet-400"
            >confirming payments</strong
          > when managing your event. Save money.
        </p>
      </Step>
    </div>
  </section>
  <section
    id="about"
    class="py-20 pt-10 lg:pt-16 lg:py-32 flex flex-col gap-16 sm:gap-20 md:gap-24 relative"
  >
    <!-- <div class="z-[-1] bg-violet-950 w-screen left-1/2 -translate-x-1/2 top-0 h-full absolute"> </div> -->
    <div
      class="flex flex-col gap-2 text-center relative before:absolute before:top-0 before:left-0 before:w-2/3 before:h-1.5 before:bg-violet-700 after:absolute after:bottom-0 after:right-0 after:w-2/3 after:h-1.5 after:bg-violet-700 py-4"
    >
      <h6 class="text-large sm:text-xl md:text-2xl">Want to know more?</h6>
      <h3 class="font-semibold text-3xl sm:text-4xl md:text-5xl">
        A bit <span class="roboto text-violet-400">about</span> us.
      </h3>
    </div>
    <p class="mx-auto roboto font-semibold text-lg sm:text-xl md:text-2xl">
      We are . . .
    </p>
    <div class="flex flex-col gap-20 w-full mx-auto max-w-[800px]">
      {#each benefits as benefit, index}
        <div class="flex gap-6 sm:gap-8">
          <p
            class="roboto text-4xl sm:text-5xl md:text-6xl text-slate-500 font-semibold"
          >
            0{index + 1}
          </p>
          <div class="flex flex-col gap-6 sm:gap-8">
            <h3 class="text-2xl sm:text-3xl md:text-5xl">
              {benefit.name}
            </h3>
            <p>{benefit.description}</p>
          </div>
        </div>
      {/each}
    </div>
    <h5 class={" text-2xl sm:text-3xl font-semibold text-center roboto "}>
      The <span class="text-violet-400">Complete</span> Package
    </h5>
    <!-- <div
      class="flex flex-col overflow-x-scroll gap-10 max-w-[800px] mx-auto w-full"
    >
    </div> -->
    <div class="mx-auto -mt-12 italic sm:hidden opacity-50">
      <p>Scroll to see more &rarr;</p>
    </div>
    <p class="mx-auto">So why not start?</p>
  </section>
  <!-- <Mouse /> -->
</main>
