---
output:
  pdf_document:
    latex_engine: lualatex
header-includes: |
  \usepackage{graphicx}
  \usepackage{fancyhdr}
  \pagestyle{fancy}
  \fancyhead{}
  \fancyhead[LO,LE]{\textsc{Edge AI Publishing Portfolio 2025}}
  \fancyhead[RO,RE]{\textsc{Steven Hoenisch}}
  \fancyfoot[RO,RE]{\href{https://github.com/open-edge-platform}{\textsc{Open Edge Platform on GitHub}}}
  \renewcommand{\footrulewidth}{0.3pt}
  \fancyfoot[LO,LE]{\href{https://criticism.com/tech/publishing-portfolio.pdf}{\textsc{Technology Portfolio Briefing}}}
  \usepackage{xcolor}
  \usepackage[dvipsnames]{xcolor}
  \definecolor{IntelBlue}{RGB}{0, 114, 206}
  \usepackage{titlesec}
  \usepackage{sectsty}
  \sectionfont{\color{IntelBlue}}
  \subsectionfont{\color{IntelBlue}} 
  \subsubsectionfont{\color{IntelBlue}}
  \usepackage[stamp=false, firstpageonly, angle=35, scale=.4, hpos=0.18\paperwidth, vpos=0.88\paperheight, color={[gray]{0.8}}, text=DRAFT]{draftwatermark}
  \usepackage{caption}
  \captionsetup[figure]{labelformat=empty}
---

<!-- 
pandoc --pdf-engine=lualatex -V geometry:margin=1in -V urlcolor=NavyBlue -V fontsize=10pt edge-ai-blogs-papers-2025.md -o edge-ai-blogs-papers-2025.pdf
-->

## Blog Posts and Papers on Edge AI

Here's a quick summary of some of the blog posts and papers I've published during the latter half of 2025, typically as part of highlighting the capababilities, use cases, and benefits of [Open Edge Platform](https://github.com/open-edge-platform) from Intel. 

The platform delivers a modular, composable stack of open-source software optimized to rapidly deploy, secure, and scale AI solutions at distributed edge sites. Open Edge Platform comprises [Edge Microvisor Toolkit](https://github.com/open-edge-platform/edge-microvisor-toolkit), [Edge Manageability Framework](https://github.com/open-edge-platform/edge-manageability-framework), [Edge AI Libraries](https://github.com/open-edge-platform/edge-ai-libraries), and [Edge AI Suites](https://github.com/open-edge-platform/edge-ai-suites). 

In addition, the [OS Image Composer](https://github.com/open-edge-platform/os-image-composer) tool lets you rapidly create and easily manage custom Linux images to meet your organizations' exacting requirements for edge AI workloads. The tool gives you a standardized, extensible framework for composing operating system images from pre-built artifacts of any Linux distribution that supports Debian or RPM packages. See my recent blog post on Medium: [Composing Custom Linux Images with the Inaugural Release of OS Image Composer](https://medium.com/@steveski170/composing-custom-linux-images-with-the-inaugural-release-of-os-image-composer-1810fc83a8d6). 

Here are links to my recent blog posts and papers: 

* A [Medium Blog Post](https://medium.com/open-edge-platform/evaluating-security-capabilities-for-edge-ai-workloads-on-intel-platforms-with-edge-microvisor-4977eb686ffc) on evaluating security capabilities for edge AI.

* A GitHub Discussions blog post titled [Validating the Performance of Edge AI Workloads on Intel Processors with Edge Microvisor Toolkit](https://github.com/open-edge-platform/edge-microvisor-toolkit/discussions/497) on running easy-to-benchmark sample applications for smart traffic intersections and wind turbine predictive maintenance on Edge Microvisor Toolkit to showcase the power and performance of running edge AI workloads on Intel processors. 

* A short [blog post](https://github.com/open-edge-platform/edge-microvisor-toolkit/discussions/616) on where to download the various versions of Edge Microvisor Toolkit.

* Deploying Edge Microvisor Toolkit with Edge Manageability Framework to Evaluate Intel Processors for AI Workloads, a GitHub Discussions [blog post](https://github.com/open-edge-platform/edge-manageability-framework/discussions/1039) on using the different versions of the toolkit to evaluate the latest Intel processor optimizations.

* The [Robotics AI Suite goes gold](https://github.com/open-edge-platform/edge-ai-suites/discussions/1481) with release 2025.2 of Edge AI Suites.  

* [Ringing in release 2025.2 of Edge AI Libraries](https://github.com/open-edge-platform/edge-ai-libraries/discussions/1601).

* [Ringing in Release 2025.2 of Edge Manageability Framework](https://github.com/open-edge-platform/edge-manageability-framework/discussions/1301).

* A [blog post](https://github.com/open-edge-platform/edge-microvisor-toolkit/discussions/644) to highlight the latest release of Edge Microvisor Toolkit.

* A [blog post](https://github.com/open-edge-platform/edge-microvisor-toolkit/discussions/591) on the public availability of OS Image Composer.

* A [blog post](https://github.com/open-edge-platform/edge-microvisor-toolkit/discussions/585) on using the real-time version of Edge Microvisor Toolkit.  

* A [blog post](https://github.com/open-edge-platform/edge-microvisor-toolkit/discussions/521) on selecting a version of Edge Microvisor Toolkit for demonstrating the capabilities of Intel platforms.

* A [blog post](https://github.com/open-edge-platform/edge-microvisor-toolkit/discussions/624) on evaluating security capabilities for edge AI.

* An [FAQ](https://github.com/open-edge-platform/edge-microvisor-toolkit/discussions/545) on the Purpose and Uses of Edge Microvisor Toolkit. 

* A description of the [purpose and capabilities](https://docs.openedgeplatform.intel.com/dev/edge-microvisor-toolkit/index.html) of Edge Microvisor Toolkit and an [explanation](https://github.com/open-edge-platform/edge-microvisor-toolkit/blob/3.0/RELEASE_POLICY.md) of the toolkit's open source release policy model.

* An evolving [list of resources](https://github.com/open-edge-platform/edge-ai-resources/blob/main/README.md) for participating in or [contributing to Open Edge Platform](https://github.com/open-edge-platform/edge-ai-resources/blob/main/oep-participate-contribute.md). 

* A GitHub Discussions [blog post](https://github.com/open-edge-platform/os-image-composer/discussions/229) that includes a concise section on how to download, install, and try out the OS Image Composer tool. 

* A [white paper](https://github.com/user-attachments/files/22503833/os-image-composer-wp.pdf) titled Composing and Managing Custom OS Images for Performance, Scalability, and Security at the Edge that describes the vision, capabilities, and business benefits of the OS Image Composer tool.

* An end-of-the-year [LinkedIn post](https://www.linkedin.com/pulse/recent-blog-posts-papers-open-edge-platform-ai-steve-hoenisch-co90c) on various recent publications.

* Blog post on Medium: [Composing Custom Linux Images with the Inaugural Release of OS Image Composer](https://medium.com/@steveski170/composing-custom-linux-images-with-the-inaugural-release-of-os-image-composer-1810fc83a8d6). | [More edge AI blog posts on Medium](https://medium.com/@steveski170/list/blog-posts-on-edge-ai-68cafc64db42).







