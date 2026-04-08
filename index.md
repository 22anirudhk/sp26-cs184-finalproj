---
title: Project Gargantua
---

<style>
  :root {
    --card: #ffffff;
    --text: #10202f;
    --muted: #4f6476;
    --accent: #ff8f3d;
    --accent-soft: #ffd79a;
    --border: rgba(16, 32, 47, 0.12);
  }

  .proposal-shell {
    max-width: 980px;
    margin: 0 auto;
  }

  .hero {
    background:
      radial-gradient(circle at 76% 38%, rgba(255, 151, 77, 0.95) 0, rgba(255, 143, 61, 0.55) 8%, rgba(255, 143, 61, 0.15) 16%, rgba(7, 17, 26, 0) 26%),
      linear-gradient(140deg, #08131f 10%, #0e1622 54%, #1f120b 100%);
    color: #f7fbff;
    padding: 2.4rem 2.2rem;
    border-radius: 22px;
    box-shadow: 0 18px 50px rgba(4, 7, 12, 0.28);
    margin-bottom: 1.5rem;
  }

  .proposal-shell .hero p {
    color: rgba(247, 251, 255, 0.92);
    max-width: 44rem;
    margin-bottom: 0;
    font-size: 1.06rem;
    line-height: 1.7;
    text-shadow: none;
    background: rgba(6, 14, 22, 0.72);
    border: 1px solid rgba(255, 255, 255, 0.08);
    border-radius: 14px;
    padding: 1rem 1.1rem;
    backdrop-filter: blur(4px);
  }

  .eyebrow {
    display: inline-block;
    letter-spacing: 0.18em;
    text-transform: uppercase;
    font-size: 0.74rem;
    color: #ffe1bf;
    margin-bottom: 0.65rem;
    font-weight: 700;
  }

  .hero h1 {
    color: #ffffff;
    margin-top: 0;
    margin-bottom: 0.5rem;
    font-size: 2.5rem;
    line-height: 1.05;
    text-shadow: 0 2px 18px rgba(0, 0, 0, 0.32);
  }

  .meta-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
    gap: 1rem;
    margin: 1.4rem 0 1.8rem;
  }

  .meta-card,
  .callout {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 16px;
    padding: 1rem 1.1rem;
    box-shadow: 0 10px 24px rgba(16, 32, 47, 0.06);
    color: var(--text);
  }

  .meta-card strong,
  .callout strong {
    color: var(--accent);
  }

  .callout {
    margin: 1.3rem 0 1.6rem;
    background: linear-gradient(180deg, rgba(255, 143, 61, 0.12), rgba(255, 255, 255, 1));
    border-left: 6px solid var(--accent);
  }

  .proposal-shell h2,
  .proposal-shell h3 {
    margin-top: 1.8rem;
  }

  .proposal-shell h2 {
    border-bottom: 1px solid rgba(0, 0, 0, 0.08);
    padding-bottom: 0.35rem;
  }

  .proposal-shell p,
  .proposal-shell li,
  .proposal-shell td,
  .proposal-shell th {
    color: var(--text);
    line-height: 1.65;
  }

  .proposal-shell table {
    width: 100%;
    border-collapse: collapse;
  }

  .proposal-shell th {
    background: rgba(255, 143, 61, 0.08);
  }

  .proposal-shell th,
  .proposal-shell td {
    padding: 0.8rem 0.9rem;
    border: 1px solid rgba(16, 32, 47, 0.10);
    vertical-align: top;
  }

  .proposal-shell a {
    color: #c95e14;
  }

  .muted {
    color: var(--muted);
  }

  @media (max-width: 700px) {
    .hero {
      padding: 1.6rem 1.25rem;
    }

    .hero h1 {
      font-size: 2rem;
    }
  }
</style>

<div class="proposal-shell" markdown="1">
  <section class="hero">
    <span class="eyebrow">CS 184/284A Final Project Proposal</span>
    <h1>Project Gargantua</h1>
    <p>
      A real-time visualization of an Interstellar-style black hole, with gravitational lensing,
      a glowing accretion disk, and relativistic color and brightness shifts. Our goal is to
      build a physically motivated renderer that is both visually compelling and interactive
      enough to let users orbit around the black hole and observe how extreme gravity warps light.
    </p>
  </section>

## Title, Summary, and Team Members

**Project Title:** Project Gargantua

**Summary:** We propose to recreate the visual appearance of an Interstellar-inspired black hole in an interactive graphics system. The core of the project is a renderer that bends light around a black hole, produces the characteristic warped accretion disk seen in _Interstellar_, and models relativistic effects such as Doppler shifting, beaming, and gravitational redshift. We want the final result to feel like both a scientific visualization and a polished graphics demo.

**Team Members:**  
Kailash Ranganathan, Anirudh Kotamraju, other 2 will be added soon!

<div class="meta-grid">
  <div class="meta-card">
    <strong>Core visual target</strong><br />
    Interstellar-style black hole with a bright, warped accretion disk and strong lensing.
  </div>
  <div class="meta-card">
    <strong>Planned platform</strong><br />
    WebGL2 / GLSL in the browser, with lightweight JavaScript scaffolding for interaction and deployment.
  </div>
  <div class="meta-card">
    <strong>Why this project</strong><br />
    It sits at the intersection of rendering, physics, numerical methods, and visual storytelling.
  </div>
</div>

## Problem Description

Black holes are often shown in media as simple dark spheres, but their actual appearance is much more interesting. A black hole does not just block light: it bends nearby light rays so strongly that the background, stars, and accretion disk are distorted into multiple warped images. In the case of a spinning black hole, these distortions can become even more dramatic. The famous image of Gargantua in _Interstellar_ is compelling precisely because it makes relativistic optics visible.

The challenge is that this effect is not a standard shading problem. To produce a convincing image, we need to simulate how rays travel through curved spacetime, determine where those rays intersect the accretion disk or background sky, and then account for frequency and intensity shifts caused by relative motion and gravity. We therefore see this project as a rendering problem built on top of general relativity-inspired ray tracing.

Our plan is to start with a physically grounded baseline and then add layers of realism. At minimum, we want a controllable camera moving around a black hole with a warped luminous disk and background star field. If time permits, we want to push toward a spinning Kerr-style model and higher-quality image formation inspired by the DNGR renderer described by James et al.

<div class="callout">
  <strong>Main question:</strong> how close can we get to the visual language of <em>Interstellar</em> while keeping the system interactive and understandable enough to demo live?
</div>

## Goals and Deliverables

### What We Plan to Deliver

Our baseline deliverable is an interactive black hole visualization that runs in the browser and supports camera movement around the scene. The renderer will produce:

- gravitational lensing of a background star field around the black hole,
- a bright accretion disk whose top and bottom are both visible through lensing,
- relativistic color and intensity changes, including Doppler shifting and beaming,
- side-by-side comparisons against simpler versions of the renderer to show what each effect adds.

We also plan to include quantitative or at least structured evaluation. In particular, we want to measure:

- frame rate as a function of render resolution and quality settings,
- visual differences between our baseline and enhanced models,
- whether our images reproduce recognizable features reported in references, such as the asymmetric bright ring and duplicated disk structure.

By the milestone, we expect to have a working lensing prototype and a first disk render. By the final presentation, we want a polished demo that lets viewers move the camera and observe the resulting distortions in real time.

### What We Hope to Deliver

If implementation goes smoothly, we would like to go beyond a basic Schwarzschild-style black hole and approximate a rotating Kerr black hole more closely. Our stretch goals are:

- a more faithful spinning black hole model inspired by Gargantua,
- a better accretion disk appearance driven by temperature or emissive profiles rather than a purely artistic texture,
- support for photon-ring-like higher-order images or more stable beam-based rendering,
- a cinematic camera path that recreates a short Interstellar-style flyby sequence for our video and presentation.

### Questions We Plan to Answer

- Which visual effects matter most for making the render immediately read as a relativistic black hole rather than a generic shader effect?
- How much physical realism can we afford while still keeping the renderer interactive?
- What is the visual gap between a simpler non-rotating model and a more ambitious rotating model?

## Schedule

| Week   | Dates                      | Planned Tasks                                                                                                                                                           |
| ------ | -------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Week 1 | April 8 to April 12, 2026  | Finalize references, derive the rendering pipeline, choose coordinate conventions, set up the WebGL/GLSL project, and render a first background-star lensing prototype. |
| Week 2 | April 13 to April 19, 2026 | Implement the accretion disk, add camera controls, tune ray marching / geodesic integration, and prepare milestone visuals plus an updated plan.                        |
| Week 3 | April 20 to April 26, 2026 | Add relativistic color and intensity effects, improve numerical stability and image quality, and compare baseline versus enhanced models.                               |
| Week 4 | April 27 to May 4, 2026    | Polish the demo, record final videos, generate comparison figures, finalize the webpage, and rehearse the live presentation.                                            |

## Resources

### Papers and References

1. Oliver James, Eugénie von Tunzelmann, Paul Franklin, and Kip S. Thorne, ["Gravitational lensing by spinning black holes in astrophysics, and in the movie Interstellar"](https://authors.library.caltech.edu/records/njdcq-95891). This is our primary reference for the visual target and for how the _Interstellar_ team modeled a spinning black hole and accretion disk.
2. Oliver James, Sylvan Dieckmann, Simon Pabst, Paul-George H. Roberts, and Kip S. Thorne, ["Building Interstellar's black hole: the gravitational renderer"](https://authors.library.caltech.edu/records/awp8p-s4d82/latest). This gives more context on the DNGR renderer and the rendering decisions behind Gargantua.
3. Event Horizon Telescope Collaboration, ["First M87 Event Horizon Telescope Results. I. The Shadow of the Supermassive Black Hole"](https://eventhorizontelescope.org/publications/first-m87-event-horizon-telescope-results-i-shadow-supermassive-black-hole). We will use this as a real observational reference for ring structure and black hole appearance.
4. Event Horizon Telescope Collaboration, ["First Sagittarius A\* Event Horizon Telescope Results. I. The Shadow of the Supermassive Black Hole in the Center of the Milky Way"](https://eventhorizontelescope.org/publications/first-sagittarius-event-horizon-telescope-results-i-shadow-supermassive-black-hole). This provides a second observational reference and helps ground our visual expectations beyond film imagery.
5. Jean-Pierre Luminet, ["Image of a spherical black hole with thin accretion disk"](https://ui.adsabs.harvard.edu/abs/1979A%26A....75..228L/abstract). This is a classic reference showing that many key visual features of black hole imagery were studied well before modern film rendering.

### Practical Implementation References

- Eric Bruneton, ["A Real-time High-quality Black Hole Shader"](https://ebruneton.github.io/black_hole_shader/). This is a useful reference for real-time rendering structure, shader organization, and performance-conscious implementation ideas.
- Oskari Seiskari, ["black-hole" WebGL simulation](https://github.com/oseiskar/black-hole). This is a practical reference showing that geodesic-based black hole visualization is feasible in a browser with GLSL.

### Computing Platform and Software

- **Primary platform:** WebGL2 + GLSL, running in Chrome or Firefox.
- **Supporting tools:** JavaScript, optional `three.js` scaffolding for camera interaction and deployment, GitHub Pages for hosting the final webpage, and Python/NumPy for any offline validation plots.
- **Hardware:** Team laptops and any available GPU-capable machines for testing higher-quality settings.

### Starting Point

We are **not** starting from a full black hole renderer that we intend to lightly modify. Our current plan is to use only a minimal browser graphics scaffold for interaction and deployment, while implementing the actual lensing, disk rendering, and relativistic visual effects ourselves. Existing black hole demos will be used as references for validation and feasibility, not as our final submission.

## Expected Deliverable Format

For the final project, we expect to present:

- an interactive live demo,
- rendered stills and short flythroughs,
- comparison figures showing the effect of each major visual component,
- a polished final webpage documenting our technical approach and results.

</div>
