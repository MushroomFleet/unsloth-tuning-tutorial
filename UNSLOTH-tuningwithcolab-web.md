# Unsloth + Colab in VS Code — Interactive Educational Tutorial Site

## Description

A multi-page, interactive educational tutorial website built with **Vite + React + TypeScript** that teaches users how to fine-tune Large Language Models (LLMs) using the open-source [Unsloth](https://github.com/unslothai/unsloth) library and Google Colab GPU runtimes — all from within the Visual Studio Code IDE.

The site transforms the official Unsloth VS Code + Colab guide into a rich, navigable web experience with step-by-step instructions, annotated screenshots, interactive checklists, syntax-highlighted code blocks with copy buttons, a progress tracker, expandable troubleshooting panels, and a polished visual design inspired by Unsloth's brand identity (greens, dark backgrounds, modern typography).

The target audience is developers and ML practitioners who are new to LLM fine-tuning and want a guided, visual walkthrough rather than a flat markdown document. The site must be fully self-contained (no backend), deployable as a static site, and responsive across desktop and tablet viewports.

---

## Functionality

### Site-Wide Features

1. **Multi-Page Navigation** — A persistent top navigation bar with links to each page. The current page is visually highlighted. Navigation uses client-side routing (React Router) with no full-page reloads.

2. **Progress Tracker** — A sidebar or top-bar progress indicator that shows the user which tutorial steps they have completed. Progress is persisted to `localStorage` so it survives page reloads and revisits. Each step page has a "Mark as Complete" button that advances the tracker.

3. **Dark/Light Theme Toggle** — A toggle button in the navigation bar that switches between a dark theme (default) and a light theme. Theme preference is saved to `localStorage`. The dark theme uses deep charcoal backgrounds (`#0f1117`) with green accent colors (`#4ade80`, `#22c55e`). The light theme uses white/off-white backgrounds with the same green accents.

4. **Responsive Layout** — The site must render correctly at desktop (1200px+), tablet (768px–1199px), and mobile (320px–767px) widths. On mobile, the navigation collapses into a hamburger menu. The sidebar progress tracker moves to a horizontal strip below the nav on smaller screens.

5. **Scroll-to-Top Button** — A floating button appears in the bottom-right corner when the user scrolls down more than 300px. Clicking it smoothly scrolls to the top of the page.

### Page Structure

The site has **7 pages** organized as follows:

---

#### Page 1: Home / Landing (`/`)

**Purpose:** Welcome the user and introduce the tutorial.

**Content:**
- A hero section with the title: **"Fine-Tune LLMs in VS Code with Unsloth & Colab GPUs"**
- A subtitle: *"A step-by-step guide to training large language models using free GPU resources — directly from your favorite code editor."*
- Three feature cards in a horizontal row:
  - **Card 1:** Icon of a code editor. Title: "VS Code Native". Description: "Work in the IDE you already know and love."
  - **Card 2:** Icon of a GPU/chip. Title: "Free GPU Access". Description: "Leverage Google Colab's free T4 GPUs for training."
  - **Card 3:** Icon of a lightning bolt. Title: "Unsloth Speed". Description: "2x faster fine-tuning with 70% less memory."
- A prominent "Get Started" CTA button that navigates to Page 2 (`/prerequisites`).
- A brief "What You'll Learn" section listing the tutorial outcomes as a bulleted list:
  - Install the Google Colab extension in VS Code
  - Connect to a free Colab GPU runtime
  - Clone and open Unsloth fine-tuning notebooks
  - Run a complete fine-tuning workflow (Qwen3-4B RL example)
  - Troubleshoot common issues

---

#### Page 2: Prerequisites (`/prerequisites`)

**Purpose:** Ensure the user has everything needed before starting.

**Content:**
- Page title: **"Prerequisites"**
- An interactive checklist (checkboxes that toggle and persist to `localStorage`) with these items:
  1. **VS Code Installed** — Link to [https://code.visualstudio.com/](https://code.visualstudio.com/). Description: "Download and install Visual Studio Code if you haven't already."
  2. **Git Installed** — Description: "Git is typically pre-installed with VS Code. Verify by running `git --version` in your terminal." Include an inline code block for the command.
  3. **Google Account** — Description: "You'll need a Google account to authenticate with Colab and access free GPU runtimes."
  4. **Jupyter Extension (Recommended)** — Description: "Most VS Code installations include the Jupyter extension. Check under Extensions (`Ctrl+Shift+X`) and search for 'Jupyter'."
- A "Continue" button at the bottom that navigates to Page 3 (`/step/1`). The button should display a subtle warning tooltip if not all checklist items are checked: "Some prerequisites are unchecked — proceed anyway?"

---

#### Page 3: Step 1 — Install the Colab Extension (`/step/1`)

**Purpose:** Walk the user through installing the Google Colab extension.

**Content:**
- Step indicator: **"Step 1 of 5"**
- Page title: **"Install the Colab Extension in VS Code"**
- Numbered instructions:
  1. Open the **Extensions** panel in VS Code using the keyboard shortcut `Ctrl+Shift+X` (Windows/Linux) or `Cmd+Shift+X` (macOS). Display this as a styled keyboard shortcut badge component.
  2. In the search bar, type **"Colab"**.
  3. Find the **"Google Colab"** extension in the results and click **Install**.
- A screenshot placeholder image area with the caption: *"The Google Colab extension in the VS Code marketplace."* Use the image URL from the source document: `https://3215535692-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FxhOjnexMCB3dmuQFQ2Zq%2Fuploads%2FJ1f5BS4EK0ok5QLy6vz5%2Fcolab_img_1.png?alt=media&token=1faa7aac-c016-4c31-90ba-ccad655244e1`
- A styled info callout box: *"Tip: If the extension doesn't appear in search results, ensure your VS Code is updated to the latest version."*
- Navigation: "Previous" button (to `/prerequisites`) and "Next: Clone the Notebooks" button (to `/step/2`).
- "Mark Step Complete" checkbox at the bottom.

---

#### Page 4: Step 2 — Clone & Open an Unsloth Notebook (`/step/2`)

**Purpose:** Guide the user to clone the notebook repository and open a notebook file.

**Content:**
- Step indicator: **"Step 2 of 5"**
- Page title: **"Clone & Open an Unsloth Notebook"**
- Instruction sub-section **"Clone the Repository"**:
  1. Open a terminal in VS Code (`` Ctrl+` `` or **Terminal → New Terminal**).
  2. Run the following commands:

  ```bash
  git clone https://github.com/unslothai/notebooks
  cd notebooks
  ```

  This code block must have a **"Copy" button** in its top-right corner. Clicking the button copies the code to the clipboard and briefly displays a "Copied!" confirmation.

- A screenshot placeholder with caption: *"Cloning the Unsloth notebooks repository in the VS Code terminal."* Use image URL: `https://3215535692-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FxhOjnexMCB3dmuQFQ2Zq%2Fuploads%2FwRL8pvgtLRpz5rcmS6vy%2FScreenshot%202026-02-18%20at%206.29.16%E2%80%AFPM.png?alt=media&token=7a72c2ec-6f94-4015-8355-27e76ba9b974`

- Instruction sub-section **"Open a Notebook"**:
  1. In the VS Code Explorer sidebar, navigate into the `notebooks/nb/` folder.
  2. Open the notebook you want to use. Unsloth supports many model types including text, embedding, and TTS fine-tuning.
  3. For this tutorial, we'll use the **Qwen3-4B RL (GRPO)** notebook: `nb/Qwen3_(4B)-GRPO.ipynb`

- A screenshot placeholder with caption: *"Opening the Qwen3-4B GRPO notebook."* Use image URL: `https://3215535692-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FxhOjnexMCB3dmuQFQ2Zq%2Fuploads%2FleZtIzyflSgi1o1QcZDU%2Fcolab_img_2.png?alt=media&token=805ebe8b-cb50-49a4-83d4-0daf96ad21c1`

- An expandable "Available Notebooks" panel (collapsed by default) listing other notable notebooks with brief descriptions:
  - Embedding fine-tuning notebooks
  - Text-to-Speech (TTS) fine-tuning notebooks
  - Links to [Unsloth notebook docs](https://unsloth.ai/docs/get-started/unsloth-notebooks)

- Navigation: "Previous" / "Next: Connect to Colab" buttons.
- "Mark Step Complete" checkbox.

---

#### Page 5: Step 3 — Connect to a Colab GPU Runtime (`/step/3`)

**Purpose:** Show how to select the Colab kernel, authenticate, and configure the GPU.

**Content:**
- Step indicator: **"Step 3 of 5"**
- Page title: **"Connect to a Colab GPU Runtime"**

- **Sub-section: Select the Colab Kernel**
  1. In the notebook toolbar at the top-right, click **"Select Kernel"**.
  2. From the dropdown, choose **"Colab"**.

  Screenshot placeholder with caption: *"Selecting the Colab kernel from the notebook toolbar."* Image URL: `https://3215535692-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FxhOjnexMCB3dmuQFQ2Zq%2Fuploads%2FleGtAKSVehrlspPGvDy2%2Fcolab_img_3.png?alt=media&token=ba3d8f1d-9cbb-44ed-8e52-8d0e52280607`

- **Sub-section: Add a New Colab Server**
  1. After selecting Colab, a dropdown with server options appears.
  2. Click **"+ Add New Colab Server"**.
  3. A browser window will open for Google authentication. Log in with your Google account, grant the requested permissions, then return to VS Code.

  Screenshot placeholder with caption: *"Adding a new Colab server."* Image URL: `https://3215535692-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FxhOjnexMCB3dmuQFQ2Zq%2Fuploads%2FZcDsB2i0aUStIKEeFTvF%2Fcolab_img_4.png?alt=media&token=a7c3642f-db35-4215-933f-99c17ebc92a2`

- **Sub-section: Configure GPU & Name the Server**
  1. Set **Hardware accelerator** to **GPU**.
  2. Choose a GPU type — **T4** is the most commonly available free-tier option.
  3. Give the server any name you like (e.g., "unsloth-training").

  Screenshot placeholder with caption: *"Choosing GPU hardware and naming the server."* Image URL: `https://3215535692-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FxhOjnexMCB3dmuQFQ2Zq%2Fuploads%2FLuK8oheihdCNn9MAZSlk%2Fcolab_img_5.png?alt=media&token=e5ed396f-afe2-4c09-b1b8-120c7301793c`

  A styled warning callout: *"GPU availability depends on your Colab plan and current capacity. If you don't see GPU options, refer to the Troubleshooting page."*

- **Sub-section: Select the Python Kernel**
  1. Once the Colab server is connected, a Python kernel will appear.
  2. Select the **Python 3** kernel for that runtime.

  Screenshot placeholder with caption: *"Selecting the Python kernel on the connected Colab runtime."* Image URL: `https://3215535692-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FxhOjnexMCB3dmuQFQ2Zq%2Fuploads%2FBexUiXJ7LRFBXs95tX2S%2Fcolab_img_6.png?alt=media&token=391e343d-d2fa-4a77-8e3f-ef244adfcb4c`

- Navigation: "Previous" / "Next: Run the Notebook" buttons.
- "Mark Step Complete" checkbox.

---

#### Page 6: Step 4 — Run the Notebook (`/step/4`)

**Purpose:** Instruct the user to execute the fine-tuning workflow.

**Content:**
- Step indicator: **"Step 4 of 5"**
- Page title: **"Run the Fine-Tuning Notebook"**
- Instructions:
  1. Click **"Run All"** in the notebook toolbar (or run cells individually from top to bottom).
  2. The first cells will install Unsloth and its dependencies on the Colab runtime. This may take 1–3 minutes.
  3. Subsequent cells will load the model, prepare the dataset, configure training parameters, and begin fine-tuning.
  4. Watch the cell outputs for training progress (loss values, steps completed).
- A styled info callout: *"For detailed guidance on what each cell does, see the official Unsloth documentation:"*
  - Link: [Fine-Tuning Guide](https://unsloth.ai/docs/get-started/fine-tuning-llms-guide)
  - Link: [Reinforcement Learning (RL) Guide](https://unsloth.ai/docs/get-started/reinforcement-learning-rl-guide)
- An embedded or linked video section: **"Video Walkthrough"** — Display an embedded YouTube player (or a styled link-card if embedding is impractical) for the video at `https://youtu.be/5NNggTrEWNQ`. Use a responsive 16:9 aspect ratio container.
- Navigation: "Previous" / "Next: Troubleshooting" buttons.
- "Mark Step Complete" checkbox.

---

#### Page 7: Step 5 — Troubleshooting & Next Steps (`/step/5`)

**Purpose:** Address common problems and provide further resources.

**Content:**
- Step indicator: **"Step 5 of 5"**
- Page title: **"Troubleshooting & Next Steps"**

- **Troubleshooting section** — rendered as expandable accordion panels (collapsed by default). Each panel has a title (the problem) and expandable body (the solution):

  **Panel 1:** *"Notebook won't run after Colab server disconnects"*
  - **Cause:** If the notebook stays open while the Colab server disconnects, VS Code can get stuck in a bad kernel/runtime state after reconnecting.
  - **Fix:** Close the notebook tab completely and re-open the notebook file. Related [GitHub issue](https://github.com/googlecolab/colab-vscode/issues/200).

  **Panel 2:** *"Can't select a GPU — only CPU shows up"*
  - **Possible causes:**
    - **Colab free-tier capacity:** GPUs may be temporarily unavailable. Try again later.
    - **Not connected to a Colab runtime:** Re-check **Select Kernel → Colab** and ensure a server is active.
    - **Account or region restrictions:** You may have reached your usage limit. Wait, try a different Google account, or upgrade your Colab plan.

  **Panel 3:** *"Packages are 'gone' after reconnecting"*
  - **Cause:** Colab runtimes are **ephemeral**. When a server restarts, all installed packages are lost.
  - **Fix:** Re-run the setup/install cells (typically the first few cells in the notebook) after reconnecting.

- **Next Steps section** — A styled card grid:
  - **Card:** "Explore More Notebooks" — Link to [Unsloth Notebooks](https://unsloth.ai/docs/get-started/unsloth-notebooks)
  - **Card:** "Unsloth GitHub" — Link to [github.com/unslothai/unsloth](https://github.com/unslothai/unsloth)
  - **Card:** "Fine-Tuning Guide" — Link to [unsloth.ai/docs/get-started/fine-tuning-llms-guide](https://unsloth.ai/docs/get-started/fine-tuning-llms-guide)
  - **Card:** "RL Training Guide" — Link to [unsloth.ai/docs/get-started/reinforcement-learning-rl-guide](https://unsloth.ai/docs/get-started/reinforcement-learning-rl-guide)

- A completion message: *"Congratulations! You've learned how to fine-tune LLMs using Unsloth and Google Colab directly from VS Code."* Styled prominently with a green checkmark icon.

- "Mark Step Complete" checkbox.
- "Back to Home" button.

---

## Technical Implementation

### Stack

| Layer | Technology |
|---|---|
| Build Tool | Vite 6.x |
| Framework | React 19.x |
| Language | TypeScript 5.x |
| Routing | React Router v7 (react-router-dom) |
| Styling | CSS Modules (one `.module.css` per component) |
| Icons | Lucide React |
| Syntax Highlighting | Prism.js (via `prism-react-renderer`) |
| State Persistence | localStorage (no external state library) |

No additional UI framework (no Tailwind, no MUI, no Chakra). All styling is hand-written CSS Modules for full control and minimal bundle size.

### Project Structure

```
unsloth-tutorial/
├── index.html
├── package.json
├── tsconfig.json
├── tsconfig.app.json
├── tsconfig.node.json
├── vite.config.ts
├── public/
│   └── favicon.svg              # Unsloth-style green lightning bolt SVG
└── src/
    ├── main.tsx                  # React root mount
    ├── App.tsx                   # Router setup, theme provider, layout shell
    ├── App.module.css
    ├── index.css                 # CSS reset, custom properties (theme tokens), global typography
    │
    ├── context/
    │   ├── ThemeContext.tsx       # Dark/light theme context + localStorage persistence
    │   └── ProgressContext.tsx    # Tutorial step completion context + localStorage persistence
    │
    ├── hooks/
    │   ├── useLocalStorage.ts    # Generic localStorage hook with JSON serialization
    │   └── useScrollTop.ts       # Hook that returns boolean: user has scrolled > 300px
    │
    ├── components/
    │   ├── Navbar/
    │   │   ├── Navbar.tsx
    │   │   └── Navbar.module.css
    │   ├── ProgressBar/
    │   │   ├── ProgressBar.tsx        # Shows step completion (e.g., "3 / 5 steps complete")
    │   │   └── ProgressBar.module.css
    │   ├── StepNavigation/
    │   │   ├── StepNavigation.tsx      # Previous / Next buttons + "Mark Complete" checkbox
    │   │   └── StepNavigation.module.css
    │   ├── CodeBlock/
    │   │   ├── CodeBlock.tsx           # Syntax-highlighted code with copy button
    │   │   └── CodeBlock.module.css
    │   ├── Callout/
    │   │   ├── Callout.tsx             # Info / Warning / Tip callout box
    │   │   └── Callout.module.css
    │   ├── Accordion/
    │   │   ├── Accordion.tsx           # Expandable panel for troubleshooting
    │   │   └── Accordion.module.css
    │   ├── Checklist/
    │   │   ├── Checklist.tsx           # Interactive checkbox list with persistence
    │   │   └── Checklist.module.css
    │   ├── FeatureCard/
    │   │   ├── FeatureCard.tsx         # Icon + title + description card
    │   │   └── FeatureCard.module.css
    │   ├── Screenshot/
    │   │   ├── Screenshot.tsx          # Image with caption, loading state, and error fallback
    │   │   └── Screenshot.module.css
    │   ├── VideoEmbed/
    │   │   ├── VideoEmbed.tsx          # Responsive YouTube embed (16:9 container)
    │   │   └── VideoEmbed.module.css
    │   ├── KeyboardShortcut/
    │   │   ├── KeyboardShortcut.tsx    # Renders styled <kbd> badge(s)
    │   │   └── KeyboardShortcut.module.css
    │   ├── ScrollToTop/
    │   │   ├── ScrollToTop.tsx         # Floating scroll-to-top FAB
    │   │   └── ScrollToTop.module.css
    │   └── Footer/
    │       ├── Footer.tsx
    │       └── Footer.module.css
    │
    ├── pages/
    │   ├── Home/
    │   │   ├── Home.tsx
    │   │   └── Home.module.css
    │   ├── Prerequisites/
    │   │   ├── Prerequisites.tsx
    │   │   └── Prerequisites.module.css
    │   ├── Step1_InstallExtension/
    │   │   ├── Step1.tsx
    │   │   └── Step1.module.css
    │   ├── Step2_CloneNotebook/
    │   │   ├── Step2.tsx
    │   │   └── Step2.module.css
    │   ├── Step3_ConnectColab/
    │   │   ├── Step3.tsx
    │   │   └── Step3.module.css
    │   ├── Step4_RunNotebook/
    │   │   ├── Step4.tsx
    │   │   └── Step4.module.css
    │   └── Step5_Troubleshooting/
    │       ├── Step5.tsx
    │       └── Step5.module.css
    │
    └── data/
        └── tutorialSteps.ts      # Step metadata array (title, path, description)
```

### Data Models

#### `TutorialStep` (in `src/data/tutorialSteps.ts`)

```typescript
export interface TutorialStep {
  id: number;          // 1-5
  title: string;       // e.g., "Install the Colab Extension"
  path: string;        // e.g., "/step/1"
  shortTitle: string;  // e.g., "Install Extension" (for progress bar)
  description: string; // One-line summary
}

export const TUTORIAL_STEPS: TutorialStep[] = [
  {
    id: 1,
    title: "Install the Colab Extension in VS Code",
    path: "/step/1",
    shortTitle: "Install Extension",
    description: "Install the Google Colab extension from the VS Code marketplace."
  },
  {
    id: 2,
    title: "Clone & Open an Unsloth Notebook",
    path: "/step/2",
    shortTitle: "Clone Notebook",
    description: "Clone the Unsloth notebooks repository and open a fine-tuning notebook."
  },
  {
    id: 3,
    title: "Connect to a Colab GPU Runtime",
    path: "/step/3",
    shortTitle: "Connect GPU",
    description: "Select the Colab kernel, authenticate, and configure a GPU server."
  },
  {
    id: 4,
    title: "Run the Fine-Tuning Notebook",
    path: "/step/4",
    shortTitle: "Run Notebook",
    description: "Execute the notebook cells to fine-tune your model."
  },
  {
    id: 5,
    title: "Troubleshooting & Next Steps",
    path: "/step/5",
    shortTitle: "Troubleshooting",
    description: "Fix common issues and explore further resources."
  }
];
```

#### `ProgressState` (managed by `ProgressContext`)

```typescript
interface ProgressState {
  completedSteps: number[];          // Array of completed step IDs, e.g., [1, 2]
  prerequisitesChecked: string[];    // Array of checked prerequisite item IDs
}
```

Stored in `localStorage` under the key `"unsloth-tutorial-progress"`.

#### `ThemeState` (managed by `ThemeContext`)

```typescript
type Theme = "dark" | "light";
```

Stored in `localStorage` under the key `"unsloth-tutorial-theme"`. Default: `"dark"`.

### Component Specifications

#### `Navbar`
- Fixed to the top of the viewport (`position: sticky; top: 0; z-index: 100`).
- Contains: site logo/title on the left ("Unsloth Tutorial"), navigation links in the center, theme toggle button on the right.
- Navigation links: Home, Prerequisites, Steps 1–5 (shown as "Step 1", "Step 2", etc.), with the current page link visually highlighted (green underline or background).
- At viewport widths below 768px, the nav links collapse behind a hamburger icon button. Clicking the hamburger opens a full-height slide-in menu from the left.
- Background color matches theme: dark theme `#0f1117`, light theme `#ffffff`. A subtle bottom border or shadow separates it from page content.

#### `ProgressBar`
- Displayed below the Navbar on all step pages (`/step/*`).
- Shows a horizontal segmented bar with 5 segments (one per step). Completed segments are filled green (`#22c55e`), the current step segment pulses subtly, incomplete segments are gray.
- Text below the bar: "Step X of 5 — [Step Title]".

#### `CodeBlock`
- Props: `code: string`, `language: string` (default `"bash"`), `filename?: string`.
- Renders syntax-highlighted code using `prism-react-renderer` with a dark theme (VS Code Dark+ or similar).
- A "Copy" button in the top-right corner. On click, copies `code` to clipboard via `navigator.clipboard.writeText()`. Button text changes to "Copied!" with a green checkmark for 2 seconds, then reverts.
- If `filename` is provided, displays it as a tab-like header above the code.
- Horizontal scroll for long lines; no line wrapping.

#### `Callout`
- Props: `type: "info" | "warning" | "tip"`, `children: ReactNode`.
- Renders a bordered box with left accent stripe.
  - `info`: blue accent (`#3b82f6`), info-circle icon.
  - `warning`: amber accent (`#f59e0b`), alert-triangle icon.
  - `tip`: green accent (`#22c55e`), lightbulb icon.
- Background is a subtle tinted version of the accent color at 10% opacity.

#### `Accordion`
- Props: `items: { title: string; content: ReactNode }[]`.
- Each item is a clickable header with a chevron icon that rotates 180° when expanded.
- Only one item can be open at a time (single-expand mode).
- Smooth height transition on expand/collapse (CSS `max-height` transition or `grid-template-rows` trick).

#### `Checklist`
- Props: `items: { id: string; label: string; description?: string; link?: string }[]`, `storageKey: string`.
- Each item renders as a styled checkbox with label. Checked state is stored in `ProgressContext` (which persists to localStorage).
- If `link` is provided, the label is a clickable external link (opens in new tab).

#### `Screenshot`
- Props: `src: string`, `alt: string`, `caption: string`.
- Renders the image inside a styled container with rounded corners, a subtle border, and a drop shadow.
- Below the image, a centered caption in smaller, muted text.
- While loading, shows a gray placeholder skeleton with a subtle shimmer animation.
- On error (image fails to load), shows a placeholder box with text: "Screenshot unavailable" and the alt text.
- Max width: 600px, centered within the content column.

#### `VideoEmbed`
- Props: `youtubeId: string`, `title?: string`.
- Renders a responsive 16:9 container with an iframe pointing to `https://www.youtube.com/embed/{youtubeId}`.
- Iframe attributes: `allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"`, `allowFullScreen`, `loading="lazy"`.
- Title is displayed as a heading above the embed.

#### `KeyboardShortcut`
- Props: `keys: string[]` (e.g., `["Ctrl", "Shift", "X"]`).
- Renders each key as a styled `<kbd>` element with a subtle border, rounded corners, and slight inset shadow to mimic a physical key. Keys are separated by a `+` character.

#### `StepNavigation`
- Props: `currentStep: number` (1–5).
- Renders at the bottom of each step page.
- "Previous" button (links to the prior step or `/prerequisites` if step 1).
- "Next" button (links to the next step; hidden on step 5, replaced with "Back to Home").
- "Mark as Complete" toggle checkbox — calls `ProgressContext.toggleStep(currentStep)`.

#### `ScrollToTop`
- Uses `useScrollTop` hook. Appears only when scrolled > 300px.
- Renders a circular FAB in the bottom-right corner with an up-arrow icon.
- Smooth fade-in/out transition on show/hide.
- On click: `window.scrollTo({ top: 0, behavior: 'smooth' })`.

#### `Footer`
- Displayed on every page at the bottom.
- Contains: "Built with React & Vite" on the left, external links to Unsloth GitHub and Unsloth Docs on the right.
- Muted text color, smaller font size.

### Routing Configuration (`App.tsx`)

```typescript
<Routes>
  <Route path="/" element={<Home />} />
  <Route path="/prerequisites" element={<Prerequisites />} />
  <Route path="/step/1" element={<Step1 />} />
  <Route path="/step/2" element={<Step2 />} />
  <Route path="/step/3" element={<Step3 />} />
  <Route path="/step/4" element={<Step4 />} />
  <Route path="/step/5" element={<Step5 />} />
  <Route path="*" element={<Navigate to="/" replace />} />
</Routes>
```

### Context Providers

`App.tsx` wraps the app in:

```tsx
<BrowserRouter>
  <ThemeProvider>
    <ProgressProvider>
      <Layout>    {/* Contains Navbar, ProgressBar, main content area, Footer, ScrollToTop */}
        <Routes>...</Routes>
      </Layout>
    </ProgressProvider>
  </ThemeProvider>
</BrowserRouter>
```

### Theme System

CSS custom properties defined in `src/index.css`:

```css
:root {
  /* Dark theme (default) */
  --color-bg-primary: #0f1117;
  --color-bg-secondary: #1a1d27;
  --color-bg-card: #21242f;
  --color-text-primary: #e4e4e7;
  --color-text-secondary: #a1a1aa;
  --color-text-muted: #71717a;
  --color-accent: #22c55e;
  --color-accent-light: #4ade80;
  --color-accent-bg: rgba(34, 197, 94, 0.1);
  --color-border: #2e3140;
  --color-info: #3b82f6;
  --color-warning: #f59e0b;
  --color-code-bg: #1e1e2e;
  --font-sans: 'Inter', system-ui, -apple-system, sans-serif;
  --font-mono: 'JetBrains Mono', 'Fira Code', 'Consolas', monospace;
  --max-content-width: 800px;
  --nav-height: 64px;
}

[data-theme="light"] {
  --color-bg-primary: #ffffff;
  --color-bg-secondary: #f4f4f5;
  --color-bg-card: #ffffff;
  --color-text-primary: #18181b;
  --color-text-secondary: #3f3f46;
  --color-text-muted: #71717a;
  --color-border: #e4e4e7;
  --color-code-bg: #f4f4f5;
}
```

The `ThemeContext` sets a `data-theme` attribute on the `<html>` element. All CSS references use `var(--color-*)` tokens, so theme switching is instant and CSS-only.

Import Google Fonts (`Inter` and `JetBrains Mono`) via a `<link>` in `index.html`.

---

## Style Guide

### Typography
- **Headings (H1):** 2.25rem, font-weight 700, color `var(--color-text-primary)`.
- **Headings (H2):** 1.75rem, font-weight 600.
- **Headings (H3):** 1.25rem, font-weight 600.
- **Body text:** 1rem (16px), line-height 1.7, color `var(--color-text-secondary)`.
- **Code inline:** `var(--font-mono)`, background `var(--color-code-bg)`, padding 2px 6px, border-radius 4px.
- **Font stack:** `Inter` for prose, `JetBrains Mono` for code.

### Spacing
- Section vertical spacing: 3rem.
- Paragraph spacing: 1.25rem.
- Card padding: 1.5rem.
- Page content max-width: 800px, centered with auto margins.
- Page horizontal padding: 1.5rem (shrinks to 1rem on mobile).

### Colors
- Primary accent: `#22c55e` (green).
- Light accent for hover states: `#4ade80`.
- Link color: `var(--color-accent)`. Underline on hover.
- Button primary: green background `#22c55e`, white text, rounded 8px, padding 12px 24px. Hover: brightness increase.
- Button secondary: transparent background, green border, green text. Hover: green background at 10% opacity.

### Animations
- Page transitions: none (keep it snappy).
- Accordion expand/collapse: 250ms ease.
- Scroll-to-top fade: 200ms ease.
- Button hover: 150ms color/background transition.
- Copied-to-clipboard confirmation: 2-second display duration.
- Screenshot skeleton shimmer: continuous subtle left-to-right gradient sweep.

### Iconography
- Use Lucide React icons consistently. Specific icons:
  - Navigation hamburger: `Menu` / `X`
  - Theme toggle: `Sun` / `Moon`
  - Scroll to top: `ArrowUp`
  - Copy button: `Copy` / `Check`
  - Accordion chevron: `ChevronDown`
  - Callout info: `Info`
  - Callout warning: `AlertTriangle`
  - Callout tip: `Lightbulb`
  - Feature card icons: `Monitor` (VS Code), `Cpu` (GPU), `Zap` (Speed)
  - External link: `ExternalLink`
  - Checkbox checked: `CheckSquare` / unchecked: `Square`
  - Completion checkmark: `CircleCheckBig`

---

## Accessibility Requirements

- All images have meaningful `alt` text.
- All interactive elements are keyboard-focusable with visible focus indicators (green outline ring).
- Accordion panels are toggled with `Enter` or `Space` keys. Use `aria-expanded` and `aria-controls` attributes.
- The hamburger menu is accessible: button has `aria-label="Toggle navigation"`, the menu has `role="navigation"`.
- Code blocks have `role="code"` for screen readers.
- Color contrast ratios meet WCAG AA (4.5:1 for normal text, 3:1 for large text) in both themes.
- Skip-to-content link as the first focusable element on the page.
- YouTube embeds have a descriptive `title` attribute.

---

## Performance Goals

- **Lighthouse score:** 90+ on Performance, Accessibility, Best Practices, SEO.
- **First Contentful Paint:** Under 1.5 seconds on a 3G connection.
- **Bundle size:** Under 200KB gzipped for the initial JS bundle (code-split per page if needed via React Router lazy loading).
- Images are loaded lazily (`loading="lazy"`) and have explicit `width`/`height` to prevent layout shift.
- Fonts are preloaded in `index.html` with `<link rel="preload">`.

---

## Setup & Run Instructions

```bash
# Create the project
npm create vite@latest unsloth-tutorial -- --template react-ts
cd unsloth-tutorial

# Install dependencies
npm install react-router-dom lucide-react prism-react-renderer

# Start development server
npm run dev
```

---

## Testing Scenarios

1. **Theme toggle:** Click the theme button — verify all pages render correctly in both dark and light themes. Refresh the page — verify the selected theme persists.
2. **Progress persistence:** Mark steps 1 and 3 as complete. Refresh the page. Navigate to a step page — verify the progress bar still shows steps 1 and 3 as complete.
3. **Prerequisite checklist:** Check all 4 items. Refresh. Verify all are still checked. Uncheck one — verify the "Continue" button shows the warning tooltip.
4. **Code copy:** Click the "Copy" button on any code block. Paste into a text editor — verify the correct code was copied. Verify the button shows "Copied!" for ~2 seconds.
5. **Accordion:** Click a troubleshooting panel title — verify it expands. Click another — verify the first collapses and the second opens. Click the open one again — verify it collapses.
6. **Responsive layout:** Resize the browser to below 768px. Verify the nav collapses to a hamburger menu, the progress bar becomes horizontal below the nav, and all content remains readable and properly spaced.
7. **Navigation flow:** Start at Home, click "Get Started", proceed through each step using "Next" buttons. Verify correct page order and that "Previous" buttons navigate back correctly.
8. **Scroll to top:** On any page with long content, scroll down past 300px. Verify the scroll-to-top button appears. Click it — verify smooth scroll to top and button disappears.
9. **404 handling:** Navigate to `/nonexistent` — verify redirect to Home page.
10. **Screenshot fallback:** Temporarily break a screenshot `src` URL — verify the error placeholder renders with alt text instead of a broken image icon.
