# 🌐 NetMark — AI-Ready Network Diagramming SPA

**NetMark** is a lightweight, zero-backend Single Page Application (SPA) designed for network engineers, system architects, and educators to visually design network topologies. 

Unlike traditional diagramming tools that lock your architecture inside proprietary binary formats or complex XML files, **NetMark serializes your entire network topology directly into structured, human-readable Markdown (`.md`)**. This makes your diagrams completely Git-friendly and immediately ready for Large Language Models (LLMs) to analyze, audit, and troubleshoot.

---

## ✨ Key Features

- **🤖 AI-Ready Markdown Storage:** Save and load complete network architectures (nodes, connections, annotations, and coordinates) using standard Markdown tables and YAML frontmatter. Easily feed the `.md` output into AI assistants for bottleneck analysis, subnet calculation, or security auditing.
- **🎨 Interactive Drag-and-Drop Canvas:** Smooth 3000×3000px workspace with intuitive device placement, real-time rubber-band link routing, and smart bounding-box auto-centering (`Center View`).
- **📦 Comprehensive Device Library:**
  - **Networking:** Router, Switch, Firewall, Access Point (AP)
  - **Compute / Endpoints:** Server, PC / Host, NAS, Mobile, Tablet, Embedded System / IoT
  - **Security / Surveillance:** IP Camera, NVR
  - **Cloud / Virtual:** Cloud / WAN, Virtual Machine (VM)
- **🏷️ Rich Metadata & Annotations:**
  - Assign device names, IP addresses, security zones/VLANs, and detailed comments to every node.
  - Label connection links (e.g., `Trunk 10G`, `Fiber Optic`, `Eth0 -> Gi0/1`) and attach link-specific notes.
  - Right-click anywhere on the canvas to drop customizable, color-coded **Text Labels** to demarcate zones or write architectural notes.
- **📸 Smart High-DPI Image Export:** Export your topology as a crisp `2x` resolution `.png` image. Automatically calculates the bounding box of your diagram to crop out empty canvas space and preserves your active color theme.
- **🌓 Dark & Light Theme:** Built-in theme switcher for comfortable viewing in any environment.
- **⚡ Zero Dependencies / No Build Step:** Runs 100% in the browser using pure HTML5, Tailwind CSS (CDN), Font Awesome, and Vanilla JavaScript.

---

## 🚀 Quick Start

Because NetMark is a pure client-side SPA, no installation or Node.js build pipeline is required.

1. Clone this repository:
   ```bash
   git clone [https://github.com/your-username/your-repo-name.git](https://github.com/your-username/your-repo-name.git)
   ```
2. Open `index.html` directly in any modern web browser (Chrome, Edge, Firefox, Safari).

---

## 🖱️ Controls & Shortcuts

| Action | Control |
| :--- | :--- |
| **Add Device** | Drag an icon from the left sidebar and drop it onto the canvas |
| **Move Device / Label** | Left-click and drag across the canvas |
| **Quick Connect (Link)** | **Right-click** the source node (a dashed orange line will follow your cursor), then **left/right-click** the target node |
| **Cancel Connection** | **Right-click** on any empty canvas space while drawing a link |
| **Add Text Label** | **Right-click** on any empty canvas space (when not drawing a link) |
| **Edit Properties** | Left-click any node, link line, or text label to open the right-hand Inspector Panel |
| **Center View** | Click the Crosshair/Arrows icon in the top toolbar to auto-center on all active nodes |

---

## 📄 How the Markdown Format Works

When you save a diagram, NetMark generates a clean `.md` file containing both logical architecture tables (for humans and AI) and an embedded JSON state comment (for lossless canvas reloading):

```markdown
---
diagram_name: "Campus Core Network"
version: "1.3"
updated: "2026-10-14"
description: "Main building topology with CCTV surveillance VLAN."
---

# Campus Core Network

## 1. Network Nodes (Devices)
| ID | Name | Type | IP Address | Zone / Subnet | Comment | Position (x,y) |
|---|---|---|---|---|---|---|
| n1 | Edge-Router | router | 10.0.0.1 | Core-WAN | Primary ISP Gateway | 600,300 |
| n2 | Core-Switch-01 | switch | 10.0.1.2 | Server-VLAN | 24-Port PoE+ | 600,480 |

## 2. Network Connections (Links)
| ID | Source | Target | Connection Name | Type | Port / Info | Comment |
|---|---|---|---|---|---|---|
| l1 | Edge-Router (n1) | Core-Switch-01 (n2) | Uplink-10G | Fiber Optic | Gi0/1 -> SFP1 | Redundant trunk |

## 3. Text Labels (Annotations)
| ID | Text | Size | Color | Position (x,y) |
|---|---|---|---|---|
| t1 | DMZ Zone | lg | red | 450,250 |
```

### 💡 Example AI Prompt Usage
Once you export your `.md` file, you can paste its contents into any LLM (ChatGPT, Claude, Gemini) with prompts like:
* *"Review this network diagram Markdown. Identify any single points of failure (SPOF) and recommend a high-availability upgrade."*
* *"Based on the nodes and zones in this Markdown file, generate Cisco IOS VLAN and ACL configuration scripts for the Core Switch and Edge Router."*

---

## 🛠️ Tech Stack

* **UI & Styling:** HTML5, [Tailwind CSS](https://tailwindcss.com/)
* **Icons:** [Font Awesome 6 Free](https://fontawesome.com/)
* **Rendering:** DOM + Dynamic SVG Overlay (for vector connections and rubber-banding)
* **Image Export:** [html2canvas](https://html2canvas.hertzen.com/)
* **Logic:** Pure Vanilla JavaScript (ES6 Classes)

---

## 📜 License

This project is open-source and available under the [MIT License](LICENSE).
