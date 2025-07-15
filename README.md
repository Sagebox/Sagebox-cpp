<h1 align="center">Sagebox for Rust</h1>

<p align="center">
   <img src="https://user-images.githubusercontent.com/70604831/174466253-c4310d66-c687-4864-9893-8f0f70dd4084.png">
</p>


# A High-Performance, Procedural GUI Designed for Rapid, Creative Development

Sagebox is a GUI architecture and set of tools that let you add windows, graphic controls, and graphical output to your Rust programs using linear, procedural code, without any boilerplate or the overhead of an event-driven framework. 

As a persistent (i.e. similar to retained, but with no need to manage redraws) set of GUI tools, Sagebox was built from scratch as a cross-platform, comprehensive GUI, enabling the creation of high-performance, GUI control-based applications, fun-with-graphics programs, and console-mode projects with added GUI controls.

Sagebox drops cleanly into existing code or new projects when rapidly prototyping or exploring creative ideas.

Sagebox is also designed for education, hobbyist, and general creative, freeform development and rapid prototyping without the need to write a lot of interface code just to add a button, slider, or other control (or to remove them).

> Sagebox has been used professionally in the tech industry by companies like Pentair and Pioneer, and most recently in the semiconductor field at ASML, where it was called “that magic program.” <br> 

[Click here to see examples on Youtube](https://www.youtube.com/@projectsagebox6835)
   <br>
## Scalable, Easy-to-Use Procedural GUI Tools

Sagebox is a procedural-first GUI toolkit that lets you build console-mode programs or full graphical applications using straightforward, linear code. 

Tools and Controls in Sagebox start simple and can scale as you want to do more.  Additional options for more complexity can be added in as needed through the use of keywords in the function call.

Sagebox manages its own environment, so you don't have to keep track of any of the controls or widgets that are launched, unless you want to.

> Although this page focuses on procedural examples, Sagebox fully supports event-driven programming for applications built around (or that prefer) that model, and is designed to fully support both models depending on the design of your program.

> This initial beta is based on the Windows version to showcase Sagebox’s core architecture ahead of the Linux release and gather community feedback.  <br /> See [Sagebox Roadmap](#sagebox-roadmap)  and [About This Release](#about-this-release--where-were-at-and-where-were-going) for details.

## Quick Examples (Sagebox in a Nutshell)

To create quick controls such as buttons, sliders, or text widgets, etc., this is typically done with two lines of code: one line to define the control, and one line to use it.

For example, if you want a slider and a button, all you need are these two lines of code:


```Rust
let box_slider = Sagebox::dev_slider("box size");
let my_button = Sagebox::dev_button("Press me");
```

![output-dev-slider-box-0](https://user-images.githubusercontent.com/70604831/174466571-6d968e7b-3e87-4cfa-8060-602137041084.png)

The above code uses the Dev Window controls (one of a few ways to create controls in Sagebox), which creates a slider labeled ***"box size"***, with a default range of 0-100 and default value of 0, followed up by a separate button.

Sagebox puts these in a window for you, and will delete them later when the program ends or the window is dismissed.
When you want to use the controls, you can just call <i>**`box_slider.get_pos()`**</i> and <i>**`my_button.pressed()`**</i>.  You can also use <i>**`my_slider.moved()`**</i> to determine if the slider has been moved since the last time checked.


For example,

```rust
let box_size = box_slider.get_pos();
if my_button.pressed() { println!("Button was pressed!"); }
```

You can set a custom range and default value of the slider by using keywords and chaining them together when you create the slider:


```rust
// Create a slider with some keywords.  The _s form denotes scaleability, to keep the simple form simple.

let box_slider = Sagebox::dev_slider_s("Box Size",kw::range((10,500)) + kw::default(150));
```

![output-dev-slider-box-150](https://user-images.githubusercontent.com/70604831/174466616-fed9d593-d165-458f-9c55-84ba93524adf.png)


Now the slider has a range of 10-500, and a default of 150, as shown in the image above.  You can also use floating-point sliders.

With other slider functions, the slider can be told to fill a memory value (e.g. <i>`&mut i32`</i> or <i>`&mut f32`</i>) as it is moved, so there’s no need to call <i>**box_slider.get_pos()**</i>. This can abstract the GUI from routines that use the slider's real-time position without knowing about the slider or GUI.

Sliders, radio buttons, checkboxes, input boxes, list-boxes, and other controls are all this easy to use, and can be scaled to more complexity.


With various widgets, you can call up color selectors, date pickers, formatted message boxes, image view & image before/after windows, and so-forth.

This basically represents Sagebox in a nutshell -- all examples for Sagebox (even the larger, more comprehensive ones), use the above approach, just with more Sagebox tools and functions.


## Simple and Powerful
![output-cpp-basics-light](https://user-images.githubusercontent.com/70604831/174572814-6cc3092e-d171-420d-b3e7-a9f73d40992c.png)

By adding just a few more lines of code, more tools can be created. 

The above examples show using Sagebox functions as easy library calls, from basic controls (left), to graphics with and without controls (right) &ndash;
all with just simple function calls without event-driven or GUI programming, representing a small amount of the overall code that stays out of the way and doesn't require any programming or GUI environment. 

The middle image, for example, is a one-line function call:

```rust
Sagebox::image_view_before_after(&image1,&image2);
```

This can be called as a single function call, with no prior Sagebox initalization. Keyword elements can be added to extend its functionality, and the returned object can be kept by the program to manage the new window, or simply discarded to let Sagebox manage it on your program's behalf while the code continues on. 
<br /><br />

# Getting Started

### Install with Cargo

```sh
    cargo add sagebox
```

### With `Cargo.toml`

```sh
    [dependencies]
    sagebox = "0.1.0"
```
### Simple Program Example

```rust
use sagebox::*

fn main{
    let window = Sagebox::new_window();
    window.write("Hello World!");
    window.wait_close();               // Wait for user to close the window
}
```

#### For a more fun version with a 100pt font centered in the window, just use <i>`write_s()`</i> and add a couple keywords:

```rust
    window.write_s("Hello World", kw::font(100) + kw::center());
```

#### Or set the font size within the text:
```rust
    window.write_s("{100}Hello World",kw::center());
```

---
## Support Active Development

**Sagebox is actively developed and welcomes early support from developers and contributors.**

> Sagebox was developed as a free, powerful and comprehensive GUI that is also very easy to use.<br>
> It is free to use in personal and commercial Rust projects.<br>
> Contributions keep it free and also keep it growing.  (See [Sagebox Roadmap](#sagebox-roadmap))
<br>

<p align="center">
  <a href="https://github.com/sponsors/your-username">
    <img src="https://img.shields.io/badge/Sponsor_on_GitHub-💖-e05d44?style=for-the-badge&logo=github" alt="GitHub Sponsors"/>
  </a>
  &nbsp;
  <a href="https://github.com/your-username/sagebox">
    <img src="https://img.shields.io/badge/Sagebox_Project-🌿-20c997?style=for-the-badge&logo=rust" alt="Sagebox on GitHub"/>
  </a>
</p>

<p align="center">
  <em>Consider sponsoring (or adding a star to the project) to help fund continued development.</em>
</p>

---

## Table of Contents
- [Why Sagebox? — Fun with Coding and Creative Programming](#why-sagebox--fun-with-coding-and-creative-programming)
  - [Designed to stay out of the way of your code](#designed-to-stay-out-of-the-way-of-your-code)
- [Using Sagebox in Console Mode](#using-sagebox-in-console-mode)   
- [Fun with Graphics](#fun-with-graphics)
- [Standalone and 3rd-Party Widgets](#standalone-and-3rd-party-widgets)
  - [Embedding Widgets into Graphical Windows](#embedding-widgets-into-graphical-windows)
- [Fast Real-Time 3-D GPU Graphics (short-term roadmap item)](#fast-real-time-3-d-gpu-graphics-short-term-roadmap-item)
- [High Performance Computing: Super-Fast AVX, Multi-Threading Functions (short-term roadmap item)](#high-performance-computing-super-fast-avx-multi-threading-functions-short-term-roadmap-item)
- [Event-Driven Architecture for Large-Scale Applications (in final integration)](#event-driven-architecture-for-large-scale-applications-in-final-integration)
- [About This Release — Where We’re At and Where We’re Going](#about-this-release--where-were-at-and-where-were-going)
- [Sagebox Roadmap](#sagebox-roadmap)
- [Support Sagebox](#support-sagebox)


<br />
<br />

## Why Sagebox? — Fun with Coding and Creative Programming

Like many programmers, I wanted to code creatively while I design. Sagebox was built as a powerful toolset to quickly add (and just as easily remove) graphic controls, widgets, and other elements without the overhead of event-driven or complex GUI boilerplate. 

Sagebox originated as a powerful GUI toolbox from real-world industry work to produce prototypes and finished products rapidly without sacrificing code quality. 

Sagebox scales with your needs to expand into your overall program, or use it as a development tool that can compile out at runtime.

This approach can make programming more enjoyable by enabling more freeform, exploratory or ad-hoc-style coding, allowing you to concentrate more on the code you want to write rather than the interface code just to have a button, slider, color selector, or whatever else is needed.

 
## Designed to stay out of the way of your code

Sagebox can be added to existing Rust code without changing its structure or setup, and you don’t need to write or orient your code a “Sagebox program” to start using it. It works with native Rust types (like `i32`, `f32`, `(i32,i32)`) and integrates cleanly alongside other libraries, including other GUIs.

<br />
<br />

## Using Sagebox in Console Mode

![output-console-mode](https://user-images.githubusercontent.com/70604831/174466676-d8cec449-a241-4402-9b7e-0e354a4d0777.png)

Sagebox can be used for traditional graphics programs with pure graphics and GUI-based controls — or pure Console-Mode applications. 

In Console Mode, you can use Sagebox functions to help with the program user-interface, such as simple sliders, buttons, or other controls. You can also bring up entry boxes, quick dialogs, before & after graphics windows, color selectors, or other widgets.

Because these are just simple function calls, you can put them into your existing code without changing your structure or interfering with the rest of your code.

Sagebox requires no program initialization, so you can just drop in any GUI control or other Sagebox function anyhwere and it will work.

Even if your end-product code doesn’t use any GUI-based graphic controls, Sagebox can still be useful during development, helping with user input and visualizing program flow while you’re developing and debugging.

<br />
<br />

# Fun with Graphics

![output-collage-graphics](https://user-images.githubusercontent.com/70604831/174466730-86c6f38a-e743-4f97-be99-8d84be64d39f.png)

Sagebox can also be used as a full graphical GUI when you want it — with graphics, controls, and built-in support for creating GUI-based applications.

You can place specific controls, create graphic buttons, and use a wide range of drawing and other graphics functions together.

Sagebox is designed to provide a full range of graphics and GUI controls when you want them, and stay out of the way when you don’t.

The image above shows various programs created with Sagebox, from simple visuals to full applications. For most of the above images, graphics were generated with just a few lines of code, with some coming from more complex, larger-scale applications.

<br />
<br />

# Standalone and 3rd-Party Widgets

![output-collage-widgets](https://user-images.githubusercontent.com/70604831/174466845-3b17fbe1-85bc-43f8-9f38-6dd1e248f8af.png)

Sagebox is designed to provide tools for developing and integrating 3rd-party plug-in controls and widgets — from dials and meters to real-world instruments like LCD panels and oscilloscopes, or any specialized GUI control you want to add to your program.

- Widgets can be launched from programs using Sagebox and can integrate into existing graphical windows.
- Widgets can also be completely standalone and used on their own inside of a console-mode program with just a one function call with no prior use of Sagebox functions.
- Sagebox will automatically create an environment to support the widget, if necessary.

The entire Sagebox library is available to help create and develop the Widget, without forcing the program using it itself. 

Widgets can be used in both procedural and event-driven applications, and do not need to follow the same programming model as the application that uses them.

Shown above: the Color Selector, Dial Widget, LCD Display Widget, and RGB Spline Widget.  

> See the [`plug_in_widgets`](https://github.com/Sagebox/Sagebox-rs/tree/main/examples) examples in the Github project.

### Embedding Widgets into Graphical Windows

![output-emulation](https://user-images.githubusercontent.com/70604831/174466885-1ac37379-5cb0-4538-83c5-1cefeab58dea.png)

Widgets can be embedded seamlessly into graphical windows to create larger GUI-based interfaces with minimal code.

The example above shows two widgets working together to emulate and control an Arduino or other hardware interface.

The LCD is drawn over a circuit board image, while the Dial Widget sits on a stucco background to simulate placement on an indoor wall.

When the dial is moved, the LCD reflects its value in real time, and the same value is printed to the lower debug window using color-coded text to highlight values.

The main interface window also uses a custom design with a rounded title bar and integrated graphic, for a more polished appearance than the usual standard OS-provided window and title bar.

<br />
<br />

# Fast Real-Time 3-D GPU Graphics <i>(short-term roadmap item)</i>

![output-collage-gpu](https://user-images.githubusercontent.com/70604831/174467047-dda08078-cf76-4d76-af24-7689271d5a56.png)

Sagebox's design includes a high-performance GPU graphics module for real-time 3-D visualization. The examples above demonstrate 60+ FPS GPU-based rendering of complex, high-resolution surfaces (often exceeding three million polygons per frame) with minimal CPU usage.

Planned for release in the the short-term roadmap, with additional tools for building GPU-accelerated applications released in the following months.

<br />
<br />

# High Performance Computing: Super-Fast AVX, Multi-Threading Functions <i>(short-term roadmap item)</i>

![output-collage-avx-both](https://user-images.githubusercontent.com/70604831/174681183-a4fd9c49-b98c-4247-8817-537682f5a5fa.png)

Sagebox includes a number of high-performance, multi-threaded AVX/SIMD functions used for real-time image processing, FFT functions, mathematical or data visualization, etc.

These components are built for maximum throughput and speed when using the traditonal CPU-based image processing functions.


The examples above include:

- A real-time Julia set rendered with AVX at 60fps in 4k,
- AVX-based Gaussian and Sinc blur filters
- CPU-rendered texture with over 1 million polygons
  - The entire image was construction in the CPU before being sent to the GPU
  - This was faster than sending the polyons to the GPU for rendering because of memory-transfer speed
  - The CPU-generated image is indisinguishable from the GPU-generated image, and has better phong-lighting model representation than the default OpenGL phong model.

Sagebox's internal image-processing core includes a set of high-performance, HPC-level, multi-threading functions.

These routines are not yet part of the public API, but many are already complete and designed for future release as general-purpose tools as completely independent functions with no GUI requirements.
The long-term roadmap is that once Sagebox’s initial release stabilizes, the timing will be based on developer feeback on which functions to release sooner than later.

<br />
<br />


# Event-Driven Architecture for Large-Scale Applications (in final integration)

While not inherently needed for most applications, Sagebox is built on a high-performance, event-driven architecture that includes a full procedural layer that gives direct access to its full capabilities.

This event-driven design means Sagebox supports fully event-driven programming by its own nature. The included procedural model is a feature that just about any application can use as a powerful feature stemming from Sagebox's core event-driven design, reducing need for an event-driven-GUI interface.

Full access to the event-driven framework is currently being integrated into the Rust interface, with emphasis on memory safety, Rust idiomatic usage, and Borrow Checker requirements.

---

# About This Release — Where We’re At and Where We’re Going

This marks Phase 1 of the Sagebox release: a Windows-based beta published early while Linux support and Rust integration continue progressing. The purpose of this release is to introduce Sagebox, gather meaningful feedback, and finalize design decisions before cross-platform code paths are fully merged.

### Why Windows First

While the original plan was for a simultaneous Linux and Windows launch, the decision was made to release Windows first in order to gather community feedback that can directly improve the Linux version.

### Your Feedback Matters

This early beta offers a chance to test features, GUI controls responsiveness, and general interface behavior in real-world use. And of course any bugs or other issues that may occur.

### What’s Next

Phase 2 will arrive in 3-4 weeks after this release (phase 1).  This release will bring more functionality and a full Windows version with many more real-world examples. 

The first native Linux beta will follow soon after (approximately 4–6 weeks), with much of the Linux-specific and architectural groundwork already complete or in active development.

# Sagebox Roadmap

Sagebox is being released in stages as part of a broader architecture, with many of its planned features already designed, or in active development. 

As described in [About This Release — Where We’re At and Where We’re Going](#about-this-release--where-were-at-and-where-were-going), Linux support is currently in progress, with a native release scheduled shortly after the Windows beta. The Windows-first release was intended to introduce Sagebox and demonstrate its capabilities as both a procedural and event-driven GUI system (with the Procedural elements emphasized in this document)

Feedback from the Rust community will help guide which features are prioritized, as well as ideas for features not listed here.

- **Linux Implementation**
  - Native Linux support is in progress, with a working prototype targeted for release 6–8 weeks after the Windows beta.
  - A functional Linux proof-of-concept is already complete, validating Sagebox’s core architecture and platform abstraction.
  - The Sagebox kernel was built from the start as a platform-agnostic, self-contained system, and has been validated through extensive real-world use.
  - Windows served as the initial integration environment for event handling and OS-level GUI behavior.
    - All functions were abstracted from the beginning to support clean multi-platform deployment, including Linux, macOS, and Android.
- **Powerful GPU Functions**
  - As shown above, GPU functions are already well underway, and will work with the same Sagebox philosophy of ease-of-use and scalability.
- **Designer Controls and Skins**
  - Sagebox includes a range of built-in controls (e.g., sliders, buttons, input boxes), and developers can create plug-in widgets.
  - Expanded custom-skin support and the ability to define fully custom controls are currently in progress.
- **GPU Graphic Controls**
  - Currently, controls are draw via the CPU and placed in a traditional window.
  - A GPU version will place the controls on the GPU window that can be used in the same window as your graphics.
    - The GPU control set will have the same flexibility and scalability as current controls.
    - This is essentially an "immediate mode" GUI for the GPU window. 
  - This has already been designed and implemention will hopefully start in the next year.
- **Other Platforms**
   - Sagebox is written as platform-agnostic kernel.  Adding Android, macOS, and other platforms is a directional goal. 
- **Fast, AVX image-processing functions**
  - Sagebox originated from the Sagelight Editor, which was heavily optimized with AVX-level code. The plan is to bring many of those fast image-processing routines into Sagebox as general-purpose functions, or possibly as a separate interfacing library that may be released as open source.
  - Several of these functions are already used internally in Sagebox, and others produce compelling graphical examples, making it practical and worthwhile to expose them as standalone tools developers can use in their own projects.
- **Educational**
  - While Sagebox already works well in educational contexts, the plan is to expand on this with ready-to-use "lab spaces" and other specific widgets and procedural frameworks to make implementation of GUI-based graphics and controls in a way where they don't become a significant part of the code just for a small project.

# Support Sagebox

Sagebox is actively developed and welcomes early support from developers and contributors.

> Sagebox was developed as a free, powerful and comprehensive GUI that is also very easy to use.<br>
> It is free to use in personal and commercial Rust projects.<br>

As Sagebox continues to grow, the developer community is invited to help shape its direction and contribute to making it even better.



If Sagebox feels like something worth supporting, consider contributing to its continued development:

- **[GitHub Sponsors](https://github.com/sponsors/YOUR_USERNAME)** — One-time or recurring donations.
- **[OpenCollective (Coming Soon)]** — For larger or institutional support with public transparency.

Your support helps add new features, documentation, and to continue to provide Sagebox free to the Rust community.

