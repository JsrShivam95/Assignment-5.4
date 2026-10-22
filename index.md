HTML

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Design Tokens & CSS Variables Showcase</title>
  <meta name="description" content="Demonstration of a modular design system using CSS custom properties in :root.">
  <link rel="icon" href="data:image/svg+xml,<svg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 100 100'><text y='.9em' font-size='90'>🎨</text></svg>">
  <link rel="stylesheet" href="tokens.css">
</head>
<body>

  <div class="container">
    <header>
      <h1>Modular Design Tokens</h1>
      <p class="subtitle">All colors, typographic scales, and spatial gutters below are powered by <code>:root</code> CSS variables.</p>
    </header>

    <main class="card-grid">

      <!-- Card 1: Primary Brand Card -->
      <article class="card">
        <div>
          <span class="card-badge">Module 01</span>
          <h2>Design Scalability</h2>
          <p>By declaring global values for primary actions and standard margins, component styling remains coherent across hundreds of pages.</p>
        </div>
        <div class="btn-group">
          <button class="btn btn-primary">Primary Action</button>
          <button class="btn btn-outline">Details</button>
        </div>
      </article>

      <!-- Card 2: Secondary Accent Card -->
      <article class="card">
        <div>
          <span class="card-badge">Module 02</span>
          <h2>Consistent Spacing</h2>
          <p>Standard small (8px), medium (16px), and large (32px) increments eliminate arbitrary pixel values and enforce layout rhythm.</p>
        </div>
        <div class="btn-group">
          <button class="btn btn-secondary">Secondary Action</button>
          <button class="btn btn-outline">Learn More</button>
        </div>
      </article>

      <!-- Card 3: Token Interoperability Card -->
      <article class="card">
        <div>
          <span class="card-badge">Module 03</span>
          <h2>Instant Theming</h2>
          <p>Changing a single CSS token inside the <code>:root</code> selector dynamically cascades updates across buttons, headings, and cards simultaneously.</p>
        </div>
        <div class="btn-group">
          <button class="btn btn-primary">Get Started</button>
        </div>
      </article>

    </main>
  </div>

</body>
</html>

CSS
/* ==========================================================================
   Step 1: CSS Variables defined in :root (Design Tokens)
   ========================================================================== */
:root {
  /* Step 2: Color Palette */
  --color-primary: #2563eb;         /* Main brand action color */
  --color-primary-hover: #1d4ed8;   /* Darker shade for interactions */
  --color-secondary: #0d9488;       /* Accent / secondary brand color */
  --color-secondary-hover: #0f766e; 
  --color-bg: #f8fafc;              /* Application background */
  --color-surface: #ffffff;         /* Card / container surface */
  --color-surface-muted: #f1f5f9;   /* Subtle background fill */
  --color-border: #e2e8f0;          /* Divider and outline border */
  --color-text: #1e293b;            /* Primary heading & body text */
  --color-text-muted: #64748b;      /* Secondary descriptive text */
  --color-white: #ffffff;

  /* Step 3: Spacing Tokens */
  --space-sm: 8px;                  /* Tight gaps, small padding */
  --space-md: 16px;                 /* Standard element padding & gutters */
  --space-lg: 32px;                 /* Section gutters & card padding */
  --space-xl: 48px;                 /* Container separation */

  /* Step 4: Font-Size Tokens */
  --font-size-sm: 0.875rem;         /* 14px - Badges, subheads */
  --font-size-md: 1rem;             /* 16px - Base paragraph body */
  --font-size-lg: 1.25rem;          /* 20px - Subtitles, card titles */
  --font-size-xl: 2.25rem;          /* 36px - Main page hero heading */

  /* Additional Design Tokens */
  --radius-sm: 6px;
  --radius-md: 10px;
  --shadow-card: 0 4px 12px rgba(0, 0, 0, 0.06);
  --transition-fast: 0.2s ease;
}

/* ==========================================================================
   Global Reset & Layout
   ========================================================================== */
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  background-color: var(--color-bg);
  color: var(--color-text);
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
  font-size: var(--font-size-md);
  line-height: 1.6;
  padding: var(--space-xl) var(--space-md);
}

.container {
  max-width: 960px;
  margin: 0 auto;
}

/* ==========================================================================
   Step 5: Headings Styled with Tokens
   ========================================================================== */
header {
  text-align: center;
  margin-bottom: var(--space-xl);
}

h1 {
  font-size: var(--font-size-xl);
  color: var(--color-primary);
  margin-bottom: var(--space-sm);
  letter-spacing: -0.02em;
}

h2 {
  font-size: var(--font-size-lg);
  color: var(--color-text);
  margin-bottom: var(--space-sm);
}

p.subtitle {
  font-size: var(--font-size-md);
  color: var(--color-text-muted);
}

/* ==========================================================================
   Step 5: Cards Styled with Tokens
   ========================================================================== */
.card-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
  gap: var(--space-lg);
  margin-bottom: var(--space-xl);
}

.card {
  background-color: var(--color-surface);
  border: 1px solid var(--color-border);
  border-radius: var(--radius-md);
  padding: var(--space-lg);
  box-shadow: var(--shadow-card);
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}

.card-badge {
  align-self: flex-start;
  font-size: var(--font-size-sm);
  font-weight: 600;
  text-transform: uppercase;
  color: var(--color-secondary);
  background-color: var(--color-surface-muted);
  padding: var(--space-sm) var(--space-md);
  border-radius: var(--radius-sm);
  margin-bottom: var(--space-md);
}

.card p {
  color: var(--color-text-muted);
  margin-bottom: var(--space-lg);
}

/* ==========================================================================
   Step 5: Buttons Styled with Tokens
   ========================================================================== */
.btn-group {
  display: flex;
  gap: var(--space-md);
}

.btn {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  font-size: var(--font-size-md);
  font-weight: 600;
  padding: var(--space-sm) var(--space-md);
  border-radius: var(--radius-sm);
  border: 1px solid transparent;
  cursor: pointer;
  text-decoration: none;
  transition: background-color var(--transition-fast), border-color var(--transition-fast);
}

.btn-primary {
  background-color: var(--color-primary);
  color: var(--color-white);
}

.btn-primary:hover {
  background-color: var(--color-primary-hover);
}

.btn-secondary {
  background-color: var(--color-secondary);
  color: var(--color-white);
}

.btn-secondary:hover {
  background-color: var(--color-secondary-hover);
}

.btn-outline {
  background-color: transparent;
  border-color: var(--color-border);
  color: var(--color-text);
}

.btn-outline:hover {
  background-color: var(--color-surface-muted);
}