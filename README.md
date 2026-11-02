<div align="center">

# 🚀 Rohit Bhalerao — Portfolio

**AI Engineer exploring intelligent, useful technology.** A personal portfolio built with an interactive 3D keyboard, animated project showcases, and a space-inspired visual design.

[![License: MIT](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)
[![Next.js 16](https://img.shields.io/badge/Next.js-16-black?logo=next.js)](https://nextjs.org)

![Portfolio preview](public/assets/seo/og-image.svg)

</div>

Personal portfolio for Rohit Bhalerao, an AI Engineer based in Jalandhar. Project, skills, and résumé sections are placeholders until personal details are added.

## ✨ Features

- **Interactive 3D Keyboard** — Programmatically generated Chibi keyboard where each keycap represents a skill, revealing titles and descriptions on hover/press. Try colors, logos, and layouts in the [Chibi keycap customizer](https://chibi.nareshkhatri.dev/demo/keycaps).
- **Live Multiplayer** — See other visitors' cursors in realtime, who's online, and chat with them ([details](#-realtime-features-optional))
- **Buttery Animations** — GSAP + Framer Motion powered scroll, hover, and reveal animations
- **Space Theme** — Floating particles on a dark canvas for a cosmic vibe
- **Easter Eggs** — Open DevTools and follow the clues 🐱
- **Light & Dark Mode** — Full theme support with cheeky disclaimer toasts
- **Responsive** — Works across all screen sizes
- **Contact Form** — Email delivery via Resend
- **Analytics** _(optional)_ — Umami analytics integration

## 🛠️ Tech Stack

| Layer | Technologies |
|---|---|
| **Framework** | Next.js 16.2.2, React 19.2.4, TypeScript |
| **Styling** | Tailwind CSS, Shadcn UI, Aceternity UI |
| **Animation** | GSAP, Framer Motion |
| **3D** | @chibi3d/runtime, Three.js, React Three Fiber |
| **Email** | Resend |
| **Misc** | Lenis (smooth scroll), Zod, next-themes |

---

## 🚀 Getting Started

### Prerequisites

- Node.js 20.9+ for Next.js 16; use a current LTS release with pnpm 11
- pnpm 11.20.0

### Installation

1. **Clone the repository:**

    ```bash
    git clone https://github.com/YOUR-USERNAME/my-portfolio.git
    cd my-portfolio
    ```

2. **Install dependencies:**

    ```bash
    pnpm install
    ```

3. **Set up environment variables:**

    Copy `.env.example` to `.env.local` and fill in the values:

    ```bash
    cp .env.example .env.local
    ```

    | Variable | Required | Description |
    |---|---|---|
    | `RESEND_API_KEY` | Yes | API key from [Resend](https://resend.com) for the contact form |
    | `NEXT_PUBLIC_SITE_URL` | No | Your public site URL for canonical metadata and sitemap generation |
    | `NEXT_PUBLIC_WS_URL` | No | WebSocket server URL for realtime features (cursors, chat, presence) |
    | `UMAMI_DOMAIN` | No | Script URL for your own Umami instance |
    | `UMAMI_SITE_ID` | No | Website ID for your Umami instance |

4. **Run the development server:**

    ```bash
    pnpm dev
    ```

5. Open [http://localhost:3000](http://localhost:3000) and see the magic ✨

---

## Code checks

Run these before opening a pull request:

```bash
pnpm lint
pnpm typecheck
```

Next.js 16 no longer runs lint during builds. The ESLint CLI uses `eslint.config.mjs`. New React Compiler diagnostics for refs, immutability, effect state updates, and manual memoization report warnings while existing animation and realtime components are migrated. Hook ordering violations remain errors.

Blog frontmatter requires a title, summary, and `publishedAt` date in `YYYY-MM-DD` format. Optional fields are `image`, `author`, and a list of `tags`. Invalid frontmatter raises a content error; unknown blog slugs return a 404.

Files under `public/assets` can be replaced at the same URL and cache for one hour before revalidation. Next.js content-hashed static assets retain immutable caching.

---

## 🎨 Make It Your Own

All personal info is centralized in [`src/data/config.ts`](src/data/config.ts). Edit this single file to rebrand the portfolio:

```ts
const config = {
  title: "Your Name | Your Title",
  description: {
    long: "Your long description for SEO...",
    short: "Your short description...",
  },
  keywords: ["your", "keywords"],
  author: "Your Name",
  email: "you@example.com",
  site: "https://yoursite.com",

  // GitHub stars button in the header
  githubUsername: "your-github-username",
  githubRepo: "your-repo-name",

  social: {
    twitter: "https://x.com/you",
    linkedin: "https://linkedin.com/in/you",
    instagram: "https://instagram.com/you",
    facebook: "https://facebook.com/you",
    github: "https://github.com/you",
  },
};
```

Other files you'll want to customize:

| File | What to change |
|---|---|
| `src/data/projects.tsx` | Your projects, screenshots, descriptions, and tech stacks |
| `src/data/constants.ts` | Skills list (name, description, icon) and work experience |
| `public/assets/` | Your images, OG image, and project screenshots |

---

## ⌨️ Customize the 3D keyboard

Try colors, logos, and layouts in the [Chibi keycap customizer](https://chibi.nareshkhatri.dev/demo/keycaps), then apply your choices to `SKILLS` in [`src/data/constants.ts`](src/data/constants.ts):

- `keyboardColor`: keycap color, such as `"#ff9408"`.
- `keyboardIcon`: copy an SVG URL from [thesvg.org](https://thesvg.org) and paste it here. You can also use a local file under `public/assets/keyboard/logos/`.
- `label` and `shortDescription`: text shown when interacting with a key.
- `shortcut`: optional physical key code, such as `"KeyQ"`. Keep shortcuts unique; defaults follow QWERTY letter order.

The demo accepts logo names too, but `keyboardIcon` needs an image URL or local asset path. Without keyboard overrides, keys use the skill's `color` and `icon`.

Keys follow the order of `SKILLS`. To change the default six columns, pass a second argument to `createKeyboardScene` in [`keyboard-scene.tsx`](src/components/keyboard/keyboard-scene.tsx). Rows adjust automatically to the skill count.

---

## 🔌 Realtime Features (Optional)

The portfolio supports optional realtime features powered by a **separate backend API**:

- 🖱️ **Live cursors** — See other visitors' cursors in realtime
- 👥 **Online presence** — Shows who's currently on the site
- 💬 **Chat** — Live chat between visitors
- **Zombie Survival** with multiplayer and leaderboards on the live site.

These features activate automatically when the `NEXT_PUBLIC_WS_URL` environment variable is set. Without it, the portfolio works perfectly fine as a static site — no realtime features, no backend dependency.

> [!NOTE]
> The backend API is **not open source**. This is intentional! Too many people have cloned the portfolio and claimed they built it from scratch. The realtime server stays private to keep the live experience unique and make it stand out.


---

## 🚀 Deployment

To deploy the portfolio:

1. Push your code to a GitHub repository
2. Connect the repository to [Vercel](https://vercel.com)
3. Add your environment variables in the Vercel dashboard
4. Vercel handles the rest — automatic deployments on every push

---

## 🤝 Contributing

If you'd like to contribute or suggest improvements, feel free to open an issue or submit a pull request. All contributions are welcome!

---

## 📄 License

This project is open source and available under the [MIT License](LICENSE).

This project is adapted from the [original 3D Portfolio](https://github.com/Naresh-Khatri/3d-portfolio) and remains under its MIT license.
