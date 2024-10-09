<script>
  import Step from "../components/Step.svelte";
  import Mouse from "../components/Mouse.svelte";
  import { onMount } from "svelte";
  // import { typewriter } from "../components/Typewriter.svelte";

  let displayText = "";
  let showTypewriter = false;

  function handleClick() {
    displayText = "Reach out at datafulsystems@gmail.com";
    showTypewriter = true;
  }

  function typewriter(node, { speed = 1 }) {
    const valid =
      node.childNodes.length === 1 &&
      node.childNodes[0].nodeType === Node.TEXT_NODE;

    if (!valid) {
      throw new Error(
        `This transition only works on elements with a single text node child`,
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
      name: "Western Medical Society",
      icon: "fa-solid fa-cart-calendar",
      description: "They help members (medics) build their career",
      link: "https://westernmedicalsociety.org/",
    },
    {
      name: "Leave No Medic Behind Initiative",
      icon: "fa-regular fa-calendar",
      description:
        "The Leave No Medic Behind Initiative Charity Run is a fundraising project by the Association of Medical Students of the University of Nairobi (AMSUN) to meet the financial needs of underprivileged students in the School of Medicine.",
      link: "https://lnmb-run.org/",
    },
    {
      name: "Mshauri YEP",
      icon: "fa-regular fa-calendar",
      description:
        "They resource centers to provide access to libraries , mentorship, digital literacy and vocational skills to children and youths in under resourced areas in Kenya.",
      link: "https://mshauriyep.org/",
    },
    {
      name: "Mhealth 4 Africa",
      icon: "fa-regular fa-calendar",
      description:
        "Their mission is to expand quality healthcare access to under resourced and remote communities through capacity building, innovation, and technology.",
      link: "https://mhealth4africa.org/",
    },
  ];

  let benefits = [
    {
      metric: "Website Development",
      name: "Website Development",
      description:
        "We will help you build a website that will help you reach your target audience and grow your business online.",
    },
    {
      metric: "Custom Enterprise Resource Planning",
      name: "Custom Enterprise Resource Planning",
      description:
        "We will help you build a custom ERP system that will help you manage your business processes and resources more efficiently. Be it payroll, inventory, accounting, point of sale or customer relationship management.",
    },
    {
      metric: "Innovative Data Solutions",
      name: "Innovative Data Solutions",
      description:
        "We will help you craft innovative data solutions that will help you make better decisions and grow your business.",
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
        We are a <span class="text-violet-400">software development agency</span
        >
        who will
        <span class="roboto text-violet-400"
          >help your business grow online</span
        >
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
        <p>{steps[0].description}a</p>
      </Step>
      <Step step={steps[1]}>
        <p>{steps[1].description}</p>
      </Step>
    </div>
    <div class="grid grid-cols-1 lg:grid-cols-2 gap-12 lg:gap-10">
      <Step step={steps[2]}>
        <p>{steps[2].description}</p>
      </Step>
      <Step step={steps[3]}>
        <p>{steps[3].description}</p>
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
