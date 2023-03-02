# 2023-03-01 Q&A Session

## Josh: any advice to start learning Vulkan?

- Charles: don't be afraid of deleting code
- Owen and Jaker: https://vkguide.dev/
- Wyatt Marvil: https://www.youtube.com/playlist?list=PL0JVLUVCkk-l7CWCn3-cdftR0oajugYvd
- Sam
  - take a look at vulkan.hpp
  - Vulkanize 2023
- Jaker
  - vkguide use VMA and VkBootstrap
  - https://renderdoc.org/vulkan-in-30-minutes.html

## Qisi Wang: Any advice on learning physics/sim in gaming?

- Jaker: depending on whether you want to make you own or integrate a framework
- jb: some videos
  - https://youtu.be/lS_qeBy3aQI
  - https://youtu.be/9IULfQH7E90
- Mike: https://pikuma.com/courses/game-physics-engine-programming
- Charles: Visual
- Jaker: PhysX Visual Debugger

## Lesley: why we don't need to have multiple buffers for temporary buffers when doing multiple passes

- Jaker:
- Mike k: with double buffering we are waiting for VSync
- Charles: triple buffering hide latency when presenting. It doesn't make sense when preparing the frame
  - In most GPU drivers, it is hard to render multiple frames at the same time
- Owen: In my DX12 stuff, when I waiting on the fence of the current frame and already start working on the next frame
- Charles:
  - little practical uses to render multiple frames in the same time
- Sam: https://developer.apple.com/library/archive/documentation/3DDrawing/Conceptual/MTLBestPracticesGuide/TripleBuffering.html
- Mike k: only work on maximum framerate

## Sam: Gamedev vs CAD? What feature of C++ to avoid in personal projects?

- Jaker: I use everything I can
- Charles
  - In work we restrict to a widely supported version
  - In personal projects, I don't create arbituary limitation
- Owen: I don't work on my own stuff unless I see a pain
- Toshi: Template slows build times
- Mike: Cross-platform?
  - Charles: don't worry about it :-)
  - Mike: go as deep as possible
  - Mike k: build stuff to bring to next project
  - Jaker: CMake
  - Lesley: Can be nice to let other devs run code
    - Charles: "Hey friend, do you want to run my code?"
  - Mike k: I build from scratch. Even without CRT. Used to run into a lot of compatibility issues.
  - Charles: C++ does not handle dependencies well
  - Lesley: package manager
  - Charles: we want fast build time but also want codebase we can manage.
    - plugin architecture with hot reloading
    - Scripting language
  - Mike k: vendoring source code of third-party libraries
  - Toshi: Pinning dependencies

## Mike k: what stuff do people do outside realistic rendering

- jb: text rendering
  - pack color and text index into a texel
  - https://jmickle66666666.github.io/blog/techart/2019/12/18/bitmap-font-renderer.html
  - Multiple people: outline font is difficult
  - https://sluglibrary.com/

## Mike: there are different ways of rendering. Rasterization, Ray tracing, Ray Marching, any other big ones?

- Ray casting
- Charles
  - We could do some tricks with scanline
  - vector display for old arcade games https://en.wikipedia.org/wiki/Vectrex
- jb: Alpha compositing of samples to render voxel
- Lesley: radiosity and photon mapping?
  - jb: photon mapping is a fancy light map?
  - Charles: photon mapping is a two-step GI.
    - Sounds like shadow mapping?
  - jb: not a real-time thing
    - Charles: only in baking process
  - Owen: radiosity is similar
    - Mike k: hugh matrix and solve it
    - Toshi: based on finite-element method
    - Charles: Wikipedia says it was developed for heat transfer
    - Radiosity was popular in 90s' games
    - https://web.archive.org/web/20010821025954/http://freespace.virgin.net/hugo.elias/radiosity/radiosity.htm
- jb: text-mode rendering
  - Mike: Doom in text editor
- Owen & Mike: hardware sprite-based consoles

## Jaker: Grass Rendering Method
- Lesley: https://github.com/LesleyLai/GLGrassRenderer
  - Paper: https://www.cg.tuwien.ac.at/research/publications/2017/JAHRMANN-2017-RRTG/JAHRMANN-2017-RRTG-draft.pdf
  - https://iquilezles.org/articles/texturerepetition/
  - Charles: texture bombing https://developer.nvidia.com/gpugems/gpugems/part-iii-materials/chapter-20-texture-bombing
- Lesley: most use billboard
- Procedural Grass in 'Ghost of Tsushima' https://www.youtube.com/watch?v=Ibe1JBF5i5Y

## daniel: How do you do non-photorealistic rendering for games?
- https://twitter.com/xavierck3d/status/1521960048959770624
- jb: can mean a lot of things
- Owen: tone shading
  - https://www.youtube.com/watch?v=mnxs6CR6Zrk
- https://www.kyprianidis.com/p/npar2008/jkyprian-npar2008.pdf
- Charles: artistic pipeline to quickly change things
- jb: https://twitter.com/ianmaclarty/status/1499494878908403712
- https://bgolus.medium.com/the-quest-for-very-wide-outlines-ba82ed442cd9
  - Jump Flood Algorithm
    - Holly: It's really useful for filling between points in point-cloud rendering
      - https://www.lcg.ufrj.br/thesis/renato-farias-MSc.pdf
- https://pages.cs.huji.ac.il/danix-lab/cglab/projects/convpyr/data/convpyr-small.pdf

## Erosion
- https://twitter.com/Th3HolyMoose/status/1627073949606748166
- https://hal.inria.fr/hal-01262376/document

## Lesley: Pain Point of Shading Language
- Charles: a new language won't solve the tooling problem
  - sharing library
  - Toshi: how many libraries for the language
  - Owen: having a package manager
  - jb: stb_include.h
- Mike: cool to have a shader-toy repository
- Lesley: https://lygia.xyz/
- Owen: node-base shading
- https://shadered.org/
- Charles: add types to vectors
- Lesley: I remember a Python library that annotate vec/mat with vector spaces
- https://github.com/EmbarkStudios/rust-gpu

## Holly: curious what kind of code editors people use for shaders
- jb: VSCode recently. Also an ImGui addon https://github.com/BalazsJako/ImGuiColorTextEdit 
- Lesley: CLion
- Holly: Visual Studio feels clunky