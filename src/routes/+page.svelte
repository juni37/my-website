<script>
  import './styles.scss'
  import { onMount } from 'svelte';

  import { book, open_book, arrow, emoji, artist, gear, school, brain, oldsites, cs50, libibkk, projectempower, devbench, github, linkedin, instagram, twitter, discord } from '$lib/images/images';
  
  import Metatags from '$lib/components/Metatags.svelte';
  
  let emojiNum = 2;
  let currentEmoji = emoji[emojiNum];
  function changeEmoji() {
    emojiNum++
    if (emojiNum >= 7) {
      emojiNum = 0
    }
    currentEmoji = emoji[emojiNum]
  }
  let interval = null;
  function rollEmoji() {
    let iteration = 0;
    
    clearInterval(interval);
    interval = setInterval(() => {
      changeEmoji()
    }, 150);
  }

  let projectsSection;
  let project1;
  let project2;
  let project3;
  let project4;

  // GSAP
  // GSAP
  import { gsap } from "gsap/dist/gsap";
  import { ScrollTrigger } from "gsap/dist/ScrollTrigger";
  import { ScrollSmoother } from "$lib/gsap/src/ScrollSmoother";
  gsap.registerPlugin(ScrollTrigger, ScrollSmoother);

  let smoother;
  let aboutTimeline = gsap.timeline();
  onMount(() => {
    if (window.innerWidth >= 900) { // Only use scrollSmoother if on a large enough page
      smoother = ScrollSmoother.create({
        smooth: 0.5,
        effects: true,  
      });
    }

    gsap.to("#header .line-1", {
      y: "10vh",
      scrollTrigger: {
        trigger: "#header",
        start: "top top",
        end: "bottom top",
        scrub: 1.5,
      }
    })
    gsap.to("#header .line-2", {
      y: "10vh",
      scrollTrigger: {
        trigger: "#header",
        start: "top top",
        end: "bottom top",
        scrub: 1,
      }
    })
    if (window.innerWidth > 1250) {
      gsap.to(".navbar", {
        y: "25vh",
        scrollTrigger: {
          trigger: "#header",
          start: "top top",
          end: "top+=750 top",
          scrub: true,
        }
      })
    }
    gsap.to("#arrow", {
      y: "2vh",
      scrollTrigger: {
        trigger: "#header",
        start: "top top",
        end: "bottom top",
        scrub: true,
      }
    })

    aboutTimeline.from("#about .section-1", {
      height: 0,
      duration: 1
    }, "<")
    .from("#about .line-1", {
      opacity: 0,
      y: "0.5em",
      duration: 1
    })
    .from("#about .line-1 .highlight", {
      background: "transparent",
      duration: 1.5
    }, "<")
    .from("#about .line-2", {
      opacity: 0,
      y: "0.5em",
      duration: 1
    })
    .from("#about .line-2 .highlight", {
      background: "transparent",
      duration: 1.5
    }, "<")
    .from("#about .line-3", {
      opacity: 0,
      y: "0.5em",
      duration: 1
    })
    .from("#about .line-3 .highlight", {
      background: "transparent",
      scale: 0,
      duration: 1.5
    }, "<")
    .from("#about .section-2", {
      height: 0,
      duration: 1
    }, "<")
    .from("#about .line-4", {
      opacity: 0,
      y: "0.5em",
      duration: 1
    })
    .from("#about .line-5", {
      opacity: 0,
      y: "0.5em",
      duration: 1
    })
    .from("#about .line-5 .highlight", {
      background: "transparent",
      duration: 1.5
    }, "<")
    .to("#about", {
      duration: 1
    })
    .to("#about", {
      clipPath: "polygon(0 50%, 100% 50%, 100% 50%, 0 50%)",
      duration: 1.5,
    })
    .to("#about", {
      duration: 0.5
    })
    .from("#past-sites .small", {
      opacity: 0,
      y: "0.25em",
      duration: 1,
    })
    .from("#past-sites .big", {
      opacity: 0,
      y: "0.25em",
      duration: 1,
    })
    .from("#past-sites .images", {
      scale: 0,
      opacity: 0,
      duration: 1,
    })
    .to("#past-sites .images", {
      scale: 1.1,
      duration: 2
    })
    .from(".old-site", {
      marginRight: "-35vw",
      duration: 2,
    }, "<")
    .to("#about", {
      duration: 0.5
    })

    if (window.innerHeight >= 900) {
      ScrollTrigger.create({
        trigger: "#about-scroll-section",
        animation: aboutTimeline,
        start: "top top",
        end: "+=4000vh",
        scrub: 0.5,
        pin: true,
      })  
    } else {
      ScrollTrigger.create({
        trigger: "#about-scroll-section",
        animation: aboutTimeline,
        start: "top top",
        end: "+=2000vh",
        scrub: true,
        pin: true,
      })  
    }
  })
</script>

<Metatags/>

<nav class="navbar">
  <a href="#" id="title">
    <h2><span>Y</span><span>U</span><span>J</span><span>U</span><span>N</span> <span>(</span><span>P</span><span>A</span><span>U</span><span>L</span><span>)</span> <span>K</span><span>I</span><span>M</span></h2>
  </a>
  <div id="socials">
    <a href="https://github.com/juni37" target="_blank" rel="noreferrer" aria-label="Go to Paul's Github"><img src={github} alt="github logo"/></a>
    <a href="https://instagram.com/yujunkim_" target="_blank" rel="noreferrer" aria-label="Go to Paul's Instagram"><img src={instagram} alt="instagram logo"/></a>
    <a href="https://discord.com/users/931714990262591499" target="_blank" rel="noreferrer" aria-label="Go to Paul's Discord"><img src={discord} alt="discord logo"/></a>
    <a href="https://linkedin.com/in/yujunkim" target="_blank" rel="noreferrer" aria-label="Go to Paul's LinkedIn"><img src={linkedin} alt="linkedin logo"/></a>
  </div>
</nav>

<header id="header">
  <h1>
    <span class="line line-1">
      <span class="wrapper">
        <span class="content">I tell</span>
      </span>
      <span class="wrapper stories-wrapper">
        <span id="stories" class="highlight content">
          <span class="text">stories</span>
          <img src={book} alt="book emoji" class="emoji" aria-hidden="true"/>
          <img src={open_book} alt="open book emoji" class="emoji" aria-hidden="true"/>
          <img src={book} alt="book emoji" class="emoji" aria-hidden="true"/>
        </span> 
      </span>
      <span class="wrapper">
        <span class="content">on the web</span>
      </span>
    </span>
    <span class="line line-2">
      <span class="wrapper">
        <span class="content">And I'd love to tell</span>
      </span>
      <span class="wrapper yours-wrapper">
        <span id="yours" class="highlight content" on:mouseenter={rollEmoji} on:mouseleave={clearInterval(interval)}>
          <span class="text">yours</span>
          <img src={currentEmoji} class="emoji" alt="emoji" aria-hidden="true"/>
        </span>
      </span>
    </span>
  </h1>
  <div id="arrow">
    <img src={arrow} alt="down arrow"/>
    <img src={arrow} alt="down arrow"/>
  </div>
</header>

<main>
  <div id="about-scroll-section">
    <section id="about">
      <div class="inner">
        <h2>So... who am I?</h2>
        <h3 class="section-1">
          <span class="line line-1">
            I'm a 
            <span class="highlight" style="color: #FDD641;">
              <span class="highlight-content">
                <img src={artist} alt="artist emoji" aria-hidden="true"/>
                Digital Designer
              </span>
            </span>
            ,
          </span>
          <span class="line line-2">
            <span class="highlight" style="color: #CDC4D6;">
              <span class="highlight-content">
                <img src={gear} alt="gear emoji" aria-hidden="true"/>
                Web Developer
              </span>
            </span>
            , and
          </span>
          <span class="line line-3">
            <span class="highlight" style="color: #FFCE7C;">
              <span class="highlight-content">
                <img src={school} alt="school emoji" aria-hidden="true"/>
                Student
              </span>
            </span>
          </span>
        </h3>
        <h3 class="section-2">
          <span class="line line-4">
            But mostly, I'm a
          </span>
          <span class="line line-5">
            <span class="highlight" style="color: #FF6DC6;">
              <span class="highlight-content">
                <img src={brain} alt="brain emoji" aria-hidden="true"/>
                Problem Solver
              </span>
            </span>
            ...
          </span>
        </h3>
      </div>
    </section>
    <section id="past-sites">
      <h2>
        <span class="small">...and I'm always</span>
        <span class="big">learning</span>
      </h2>
      <div class="images">
        {#each oldsites as site (site.number)}
          <img src={site.image} id={`site${site.number}`} alt={`old site ${site.number}`} class="old-site"/>
        {/each}
      </div>
    </section>
  </div>
  
  <section id="projects" bind:this={projectsSection}>
    <h2>Projects</h2>
    <span aria-hidden="true">Projects</span>
    <div id="scroller">
      <article class="project" bind:this={project2}>
        <a href="https://devbench.kr/" target="_blank" rel="noreferrer" aria-label="go to featured website">
          <img src={devbench} alt="DevBench, A Community for Korean Youth Developers - website screenshot"/>
        </a>
        <a href="https://devbench.kr/" target="_blank" rel="noreferrer" class="project-title">
          <h3>DevBench: A Community for Korean Youth Developers</h3>
        </a>
      </article>
      <article class="project" bind:this={project3}>
        <a href="https://libibkk.com/" target="_blank" rel="noreferrer" aria-label="go to featured website">
          <img src={libibkk} alt="LIBIBKK, Korean Top 1 Minecraft Looting server - a  website screenshot"/>
        </a>
        <a href="https://libibkk.com/" target="_blank" rel="noreferrer" class="project-title">
          <h3>LIBIBKK Server</h3>
        </a>
      </article>
      <article class="project" bind:this={project4}>
        <a href="https://empowerfsa.xyz/" target="_blank" rel="noreferrer" aria-label="go to featured website">
          <img src={projectempower} alt="Project: Empower at Fulton Science Academy - website screenshot"/>
        </a>
        <a href="https://empowerfsa.xyz/" target="_blank" rel="noreferrer" class="project-title">
          <h3>Project: Empower at Fulton Science Academy</h3>
        </a>
      </article>
      <article class="project" bind:this={project1}>
        <a href="https://cs50.paulkim.me/hello_world" target="_blank" rel="noreferrer" aria-label="go to featured website">
          <img src={cs50} alt="CS50 at Fulton Science Academy - website screenshot"/>
        </a>
        <a href="https://cs50.paulkim.me/hello_world" target="_blank" rel="noreferrer" class="project-title">
          <h3>CS50 at Fulton Science Academy</h3>
        </a>
      </article>
    </div>
  </section>
  <section id="contact">
    <div id="contact-wrapper">
      <h2>I'd love to work with you</h2>
      <div id="contact-content">
        <div id="contact-info">
          <p>Do you have a wonderful idea and want to make it into reality? <br/> Reach out with a contact form - I'd love to hear from you. </p>
          <div>
            <div class="contact-info-line">
              <h3>Social Media</h3>
              <div class="contact-social-media">
                <a href="https://github.com/juni37" target="_blank" rel="noreferrer" aria-label="Go to Paul's Github"><img src={github} alt="github logo"/></a>
                <a href="https://instagram.com/yujunkim_" target="_blank" rel="noreferrer" aria-label="Go to Paul's Instagram"><img src={instagram} alt="instagram logo"/></a>
                <a href="https://discord.com/users/931714990262591499" target="_blank" rel="noreferrer" aria-label="Go to Paul's Discord"><img src={discord} alt="discord logo"/></a>
                <a href="https://linkedin.com/in/yujunkim" target="_blank" rel="noreferrer" aria-label="Go to Paul's LinkedIn"><img src={linkedin} alt="linkedin logo"/></a>
              </div>
            </div>
            <div class="contact-info-line">
              <h3>Email</h3>
              <a href="mailto:%68%65%6c%6c%6f%40%70%61%75%6c%6b%69%6d%2e%6d%65">hello at paulkim.me</a>
            </div>
            <div class="contact-info-line">
              <h3>Location</h3>
              <a href="https://maps.app.goo.gl/9iFjT4JcVkot4qX3A" target="_blank" rel="noreferrer">Metro Atlanta Area - Georgia</a>
            </div>
            <div class="contact-info-line">
              <h3>Resume</h3>
              <a href="https://resume.paulkim.me" target="_blank" rel="noreferrer">Not much, but it's honest work.</a>
            </div>
            <div class="contact-info-line">
              <h3>Blog</h3>
              <a href="https://blog.paulkim.me/" target="_blank" rel="noreferrer">I write tech-savvy stuff!</a>
            </div>
          </div>
        </div>
        <form name="contact-form" acceptCharset="utf-8" action="https://formsubmit.co/iam@paulkim.me" method="POST">
          <fieldset>
            <input type="text" name="name" id="your-name" placeholder="Your Name" required/>
            <input type="email" name="email" id="your-email" placeholder="Your@Email.com" required/>
          </fieldset>
          <textarea name="message" id="message" placeholder="Message" required/>
          <input type="submit" value="Submit"/>
          <input type="hidden" name="_next" value="https://paulkim.me">
        </form>
      </div>
    </div>
  </section>
</main>