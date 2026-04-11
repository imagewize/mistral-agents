Here’s a production-ready **Hero block for Elayne** (FSE-compliant, split layout, light/modern aesthetic). The design uses CSS Grid for the split, a rendered browser mockup with a mini UI in the visual column, and follows WordPress FSE conventions for spacing, colors, and block composability.

---

### **Full HTML + CSS (Self-contained)**
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Elayne Hero Block</title>
    <style>
        :root {
            --wp--preset--color--primary: #017cb6;
            --wp--preset--color--accent: #f97316;
            --wp--preset--color--background: #ffffff;
            --wp--preset--color--foreground: #1e293b;
            --wp--preset--color--light-gray: #f8fafc;
            --wp--preset--color--border: #e2e8f0;
            --wp--preset--spacing--40: 2.5rem;
            --wp--preset--spacing--50: 3.125rem;
            --wp--preset--spacing--60: 3.75rem;
            --wp--preset--spacing--80: 5rem;
            --wp--preset--font-size--large: 2.25rem;
            --wp--preset--font-size--x-large: 3rem;
            --wp--preset--font-size--medium: 1.25rem;
            --wp--preset--font-size--small: 1rem;
            --wp--preset--border-radius--small: 0.25rem;
            --wp--preset--border-radius--large: 0.5rem;
        }

        body {
            font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
            line-height: 1.6;
            color: var(--wp--preset--color--foreground);
        }

        .wp-block-elayne-hero {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: var(--wp--preset--spacing-60);
            align-items: center;
            padding: var(--wp--preset--spacing-80) var(--wp--preset--spacing-40);
            max-width: 1200px;
            margin: 0 auto;
        }

        .wp-block-elayne-hero__content {
            padding-right: var(--wp--preset--spacing-40);
        }

        .wp-block-elayne-hero__content h1 {
            font-size: var(--wp--preset--font-size--x-large);
            font-weight: 700;
            margin-bottom: var(--wp--preset--spacing-40);
            color: var(--wp--preset--color--foreground);
            line-height: 1.2;
        }

        .wp-block-elayne-hero__content p {
            font-size: var(--wp--preset--font-size--medium);
            color: #475569;
            margin-bottom: var(--wp--preset--spacing-50);
        }

        .wp-block-elayne-hero__actions {
            display: flex;
            gap: var(--wp--preset--spacing-40);
            align-items: center;
        }

        .wp-block-button__link {
            padding: 0.75rem 1.5rem;
            border-radius: var(--wp--preset--border-radius--small);
            font-weight: 600;
            text-decoration: none;
            transition: all 0.2s ease;
        }

        .wp-block-button__link.is-style-primary {
            background-color: var(--wp--preset--color--primary);
            color: white;
            border: 2px solid var(--wp--preset--color--primary);
        }

        .wp-block-button__link.is-style-ghost {
            background-color: transparent;
            color: var(--wp--preset--color--primary);
            border: 2px solid var(--wp--preset--color--primary);
        }

        .wp-block-elayne-hero__visual {
            background-color: var(--wp--preset--color--light-gray);
            border-radius: var(--wp--preset--border-radius--large);
            padding: var(--wp--preset--spacing-50);
            border: 1px solid var(--wp--preset--color--border);
        }

        .browser-mockup {
            background-color: white;
            border-radius: var(--wp--preset--border-radius--small);
            overflow: hidden;
            box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1);
        }

        .browser-mockup__header {
            background-color: #f1f5f9;
            padding: 0.75rem 1rem;
            display: flex;
            align-items: center;
            gap: 0.5rem;
            border-bottom: 1px solid var(--wp--preset--color--border);
        }

        .browser-mockup__dots {
            display: flex;
            gap: 0.25rem;
        }

        .browser-mockup__dot {
            width: 0.5rem;
            height: 0.5rem;
            border-radius: 50%;
            background-color: #9ca3af;
        }

        .browser-mockup__screen {
            padding: var(--wp--preset--spacing-40);
            min-height: 300px;
            background-color: white;
        }

        .mock-nav {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: var(--wp--preset--spacing-50);
            padding-bottom: var(--wp--preset--spacing-40);
            border-bottom: 1px solid var(--wp--preset--color--border);
        }

        .mock-nav__logo {
            width: 40px;
            height: 40px;
            background-color: var(--wp--preset--color--primary);
            border-radius: var(--wp--preset--border-radius--small);
        }

        .mock-nav__menu {
            display: flex;
            gap: 1rem;
        }

        .mock-nav__menu-item {
            color: var(--wp--preset--color--foreground);
            font-size: var(--wp--preset--font-size--small);
            text-decoration: none;
        }

        .mock-content {
            display: flex;
            flex-direction: column;
            gap: var(--wp--preset--spacing-40);
        }

        .mock-image {
            width: 100%;
            height: 120px;
            background-color: var(--wp--preset--color--border);
            border-radius: var(--wp--preset--border-radius--small);
            margin-bottom: var(--wp--preset--spacing-40);
        }

        .mock-text {
            font-size: var(--wp--preset--font-size--small);
            color: var(--wp--preset--color--foreground);
            line-height: 1.5;
        }

        .mock-button {
            align-self: flex-start;
            padding: 0.5rem 1rem;
            background-color: var(--wp--preset--color--accent);
            color: white;
            border: none;
            border-radius: var(--wp--preset--border-radius--small);
            font-size: var(--wp--preset--font-size--small);
            font-weight: 600;
        }

        @media (max-width: 768px) {
            .wp-block-elayne-hero {
                grid-template-columns: 1fr;
                text-align: center;
            }

            .wp-block-elayne-hero__content {
                padding-right: 0;
                margin-bottom: var(--wp--preset--spacing-60);
            }

            .wp-block-elayne-hero__actions {
                justify-content: center;
            }
        }
    </style>
</head>
<body>
    <div class="wp-block-elayne-hero">
        <div class="wp-block-elayne-hero__content">
            <h1>Build beautiful sites with Elayne</h1>
            <p>Elayne is a modern WordPress block theme designed for the Site Editor. Create stunning layouts without writing a single line of code.</p>
            <div class="wp-block-elayne-hero__actions">
                <a href="#" class="wp-block-button__link is-style-primary">Get Started</a>
                <a href="#" class="wp-block-button__link is-style-ghost">Learn More</a>
            </div>
        </div>
        <div class="wp-block-elayne-hero__visual">
            <div class="browser-mockup">
                <div class="browser-mockup__header">
                    <div class="browser-mockup__dots">
                        <div class="browser-mockup__dot"></div>
                        <div class="browser-mockup__dot"></div>
                        <div class="browser-mockup__dot"></div>
                    </div>
                </div>
                <div class="browser-mockup__screen">
                    <div class="mock-nav">
                        <div class="mock-nav__logo"></div>
                        <div class="mock-nav__menu">
                            <a href="#" class="mock-nav__menu-item">Home</a>
                            <a href="#" class="mock-nav__menu-item">Features</a>
                            <a href="#" class="mock-nav__menu-item">Pricing</a>
                        </div>
                    </div>
                    <div class="mock-content">
                        <div class="mock-image"></div>
                        <div class="mock-text">
                            <p>Discover the power of Full Site Editing with Elayne. Customize every part of your site with ease.</p>
                            <p>From headers to footers, Elayne gives you full control over your site's design.</p>
                        </div>
                        <button class="mock-button">Try Now</button>
                    </div>
                </div>
            </div>
        </div>
    </div>
</body>
</html>
```

---

### **Developer Handoff Notes**

#### **Project:** Elayne (FSE Block Theme)
#### **Component:** Hero Block (Split Layout)
#### **WordPress Mapping:**
- **Structure:** Group block containing:
  - **Columns block** (50/50 split)
    - **Left column:** Group block with Heading, Paragraph, Buttons block (2 buttons)
    - **Right column:** Group block with a custom "Browser Mockup" inner block (see notes)
- **Styles:** All colors, spacing, and typography use `theme.json` presets (e.g., `--wp--preset--color--primary`).
- **Buttons:** Use the core Buttons block with "Primary" and "Outline" style variations.
- **Browser Mockup:** Should be implemented as a **custom block** (e.g., `elayne/browser-mockup`) for reusability. The mockup’s content (nav, image placeholder, text, button) is static and styled via CSS.

#### **Responsive Notes:**
- Stacks to 1 column on mobile.
- Buttons center-align on mobile.

#### **Implementation Steps:**
1. Register a custom `elayne/browser-mockup` block for the visual column.
2. Add the Hero layout as a **pattern** in the Site Editor.
3. Ensure all spacing and colors reference `theme.json` presets.

---
**Next Steps:**
- Should I extract the browser mockup as a standalone component for reuse?
- Do you want to adjust the typography scale or button styles?