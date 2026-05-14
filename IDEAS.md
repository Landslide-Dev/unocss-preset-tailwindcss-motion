# Ideas (parking lot)

Loose notes. Nothing shipped yet.

---

## `step-N:` variant for declarative sequencing

### The pitch

Sequence multiple animation presets on a **single element** by wrapping any existing utility with a `step-N:` variant. Reuses the entire current vocabulary — every preset, every per-property slash modifier, every duration / ease / delay utility works inside a step. Nothing new to learn; the variant just scopes existing utilities to a position in a timeline.

### Shape

```html
<div class="
  step-1:motion-preset-fade-up
  step-1:motion-duration-400
  step-1:motion-ease-out

  step-2:motion-preset-pop
  step-2:motion-duration-600
  step-2:motion-ease-spring-bouncy

  step-3:motion-preset-spin
  step-3:motion-duration-300/rotate
  step-3:motion-delay-200/opacity

  step-4:motion-preset-shake
  step-4:motion-duration-500

  step-5:motion-preset-fade-down
  step-5:motion-duration-200
">
```

Each step is a slot in a comma-list animation shorthand. Steps run in order; each step's delay = cumulative sum of prior step durations. Per-property slash modifiers (`/rotate`, `/opacity`, etc.) still work inside a step.

### CSS mechanics (pure CSS, no JS, no transformer)

Preflight pre-computes the delay cascade and pre-allocates N slots:

```css
* {
  --motion-1-delay: 0ms;
  --motion-2-delay: var(--motion-1-duration, 750ms);
  --motion-3-delay: calc(var(--motion-1-duration, 750ms) + var(--motion-2-duration, 750ms));
  --motion-4-delay: calc(/* sum of 1..3 */);
  /* …up to step-8 */
}
```

Every motion element's `animation:` shorthand is a fixed N-entry comma list:

```css
animation:
  var(--motion-1-all-animations, none),
  var(--motion-2-all-animations, none),
  /* …through step-N, each defaults to none */;
```

Unused steps = `none` = no-op. Empty steps still contribute their default 750ms duration to the cascade (unless we want to special-case empty = 0ms).

### Why it beats a `/then` slash-suffix approach

- Reuses the whole preset. No new `then` / `with` / `at` / `before` vocabulary.
- Per-step, per-property control — `step-2:motion-duration-500/rotate` stacks cleanly.
- Reorderable by renumbering. Gaps are implicit no-ops.
- Variant prefixes are already a Tailwind-native idiom; no grammar invention.

### Open questions

- **Implementation route.** UnoCSS variants transform selectors, not CSS variable names — `step-N:` can't *automatically* rewrite `--motion-duration` → `--motion-N-duration`. Two paths:
  - **Code-gen duplicate rules** — stamp the existing rule set out N times with namespaced vars. Rock solid, larger CSS.
  - **Body-transform variant** — use UnoCSS's variant `body` hook to rewrite declarations on the fly. Elegant, more fragile.
- **How many steps to pre-allocate.** 8? 16? Class-explosion risk past ~8.
- **Empty-step semantics.** Does an unfilled step still consume its default duration in the cascade, or collapse to 0ms? Probably collapse — but needs thinking about how unused `--motion-N-duration` falls back.
- **Interaction with existing unscoped utilities.** `motion-preset-fade-up step-2:motion-preset-pop` — does the unscoped fade-up run as step 0? Or is step-less behavior completely independent of the sequence system? Leaning toward: step-less = current behavior, independent channel, runs alongside the sequence.
- **Naming.** `step-1:` vs `s1:` vs `[1]:` vs `1:`. `step-N:` reads clearest, costs most characters.

### Alt syntax worth remembering

`/then` slash-suffix as a lighter-weight alternative for simple linear chains:

```html
<div class="motion-preset-fade-up motion-preset-pop/then motion-preset-spin/then">
```

`/then` = "after prev ends." Plus `/then+200`, `/then-100`, `/with`, `/with+150` for overlap / gap / concurrency. Needs a transformer to compute cumulative delays (CSS alone can't resolve "previous class's duration"). Could ship alongside `step-N:` — terse form for quick chains, step form for anything complex.

### Backwards compat

Net-new additions. Zero existing rules change. Elements without `step-N:` utilities render byte-identical to today.
