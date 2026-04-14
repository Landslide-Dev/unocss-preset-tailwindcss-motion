# 😍 unocss-preset-tailwindcss-motion 😍 

![Motion Animation Preview](https://github.com/whatnickcodes/unocss-preset-tailwindcss-motion/blob/HEAD/cover.png?raw=true)

Port of the most beautiful animation Tailwind library [tailwindcss-motion](https://github.com/romboHQ/tailwindcss-motion) by @romboHQ.

## Get Started

This is for UnoCSS folks but should be really easy if you are familiar. Simply add the preset to your UnoCSS config via our [NPM package](https://www.npmjs.com/package/unocss-preset-tailwindcss-motion).

```bash
npm i -D unocss-preset-tailwindcss-motion
```

```js
import { presetTailwindMotion } from 'unocss-preset-tailwindcss-motion'


export default defineConfig({
    presets: [
        presetUno(),
        presetTailwindMotion()
    ],
})
```

## Changelog

It is now updated to match `v4` of the Tailwind plugin.

**Latest internal additions:**
- New `xs` size tier on every size-aware preset (slide, fade, focus, blur, pulse, wobble, seesaw, oscillate, stretch, float)
- Arbitrary value JIT support: `motion-preset-slide-up-[10px]`, `motion-preset-fade-[1200ms]`, `motion-preset-pulse-[1.05]`, etc.
- `wait`, `still`, `motion-paused`, `motion-running`, `pause`, `play` now apply `!important` so they reliably override animation state
- `still` now zeroes durations to `0ms` (was `0.01ms`)
- Bug fixes: corner slides (`motion-preset-slide-up-right` etc.) now actually animate diagonally; theme defaults wired to the correct UnoCSS keys; rule selectors interpolate `${selector}` so all UnoCSS variants (`hover:`, `focus:`, `md:`, `dark:`, `group-hover:` …) work everywhere
- Removed dead autocomplete entries (`motion-preset-slide` bare, `motion-preset-flomoji-[...]` literal)


## Demo

[Giant Test Page](https://animations.tips.io)


## Why?

I needed a solid animation library for my side project that is heavily UnoCSS dependent. UnoCSS is truly a work of art and so is this library. Now you can have both. More on side project soon.

## Features

Please reference the [official plugin docs](https://github.com/romboHQ/tailwindcss-motion) for a better explanation. Basically it comes down to:

```html
<!--
PRESETS
These are easy perfectly built out-of-the-box animations.
-->
<div class="motion-preset-slide-up"></div>
<div class="motion-preset-bounce"></div>
<div class="motion-preset-confetti"></div>
Etc...


<!--
BASE ANIMATIONS
These are specific one-offs.
-->
<div class="motion-translate-y">Default</div>
<div class="motion-translate-y-75">Custom</div>
<div class="motion-translate-y-[25px]">JIT</div>

<div class="motion-rotate-in">Default</div>
<div class="motion-rotate-in-45">Custom</div>
<div class="motion-rotate-in-[69deg]">JIT support</div>
Etc...


<!--
COMBINING ANIMATIONS
The real power comes in combining these
-->
<div class="motion-translate-y-in motion-rotate-in-45"></div>


<!-- 
MODIFIERS
Adjust duration, spring, delay and loop modifiers
-->
<div class="motion-translate-y-in">Normal</div>
<div class="motion-translate-y-in motion-duration-2000">2000ms speed</div>
<div class="motion-translate-y-in motion-ease-spring-bouncy">Bouncy</div>
<div class="motion-translate-y-in motion-delay-300">300ms delay</div>
<div class="motion-translate-y-loop-75 motion-loop-twice">Loop 2x</div>
<div class="motion-translate-y-in motion-duration-2000 motion-ease-spring-bouncy">2000ms speed, bouncy</div>

```

Making sense? Easy, great! Check out the million options below:

## Full Docs & Reference


### Base Animations

#### Scale
```
motion-scale-<in|out|loop>
motion-scale-<in|out|loop>-[0|50|75|90|95|100|105|110|125|150]
motion-scale-<in|out|loop>-[value]

motion-scale-in
motion-scale-out
motion-scale-loop
motion-scale-in-75
motion-scale-out-150
motion-scale-loop-[1.337]
motion-scale-in-[0.5]
motion-scale-loop-75/mirror
motion-scale-loop-[1.5]/reset
```

#### Scale X/Y
``` 
motion-scale-<x|y>-<in|out|loop>
motion-scale-<x|y>-<in|out|loop>-[0|50|75|90|95|100|105|110|125|150]
motion-scale-<x|y>-<in|out|loop>-[value]

motion-scale-x-in
motion-scale-y-out
motion-scale-x-loop
motion-scale-x-in-75
motion-scale-y-out-150
motion-scale-x-loop-[0.82]
motion-scale-y-in-[1.25]
motion-scale-x-loop-75/mirror
motion-scale-y-loop-[1.5]/reset
```

#### Translate
```
motion-translate-<x|y>-<in|out|loop>
motion-translate-<x|y>-<in|out|loop>-(0|25|50|75|100|150)
motion-translate-<x|y>-<in|out|loop>-[value]

motion-translate-x-in
motion-translate-y-out
motion-translate-x-loop
motion-translate-x-in-75
motion-translate-y-out-150
motion-translate-x-loop-[42px]
motion-translate-y-in-[-15rem]
motion-translate-x-loop-25/mirror
motion-translate-y-loop-[88vh]/reset
```

#### Rotate
```
motion-rotate-<in|out|loop>
motion-rotate-<in|out|loop>-(0|1|2|3|6|12|45|90|180)
motion-rotate-<in|out|loop>-[value]

motion-rotate-in
motion-rotate-out-45
motion-rotate-loop
motion-rotate-in-[42deg]
motion-rotate-out-[-15deg]
motion-rotate-loop-90/mirror
motion-rotate-loop-[180deg]/reset
```

#### Opacity
```
motion-opacity-<in|out|loop>
motion-opacity-<in|out|loop>-(0|25|50|75|100)
motion-opacity-<in|out|loop>-[value]

motion-opacity-in
motion-opacity-out-50
motion-opacity-loop
motion-opacity-in-[0.42]
motion-opacity-out-[33%]
motion-opacity-loop-75/mirror
motion-opacity-loop-[0.875]/reset
```

#### Blur
```
motion-blur-<in|out|loop>
motion-blur-<in|out|loop>-(sm|md|lg|xl|2xl|3xl)
motion-blur-<in|out|loop>-[value]

motion-blur-in
motion-blur-out-lg
motion-blur-loop
motion-blur-in-[5px]
motion-blur-out-[10px]
motion-blur-loop-xl/mirror
motion-blur-loop-[15px]/reset
```

#### Text Color
```
motion-text-<in|out|loop>
motion-text-<in|out|loop>-{color}
motion-text-<in|out|loop>-[value]

motion-text-in
motion-text-out-red-500
motion-text-loop-blue-500
motion-text-in-[#ff0000]
motion-text-out-purple-500
motion-text-loop-blue-500/mirror
motion-text-loop-[#0000ff]/reset
```

#### Background Color
```
motion-bg-<in|out|loop>
motion-bg-<in|out|loop>-{color}
motion-bg-<in|out|loop>-[value]

motion-bg-in
motion-bg-out-red-500
motion-bg-loop-blue-500
motion-bg-in-[#ff0000]
motion-bg-out-purple-500
motion-bg-loop-blue-500/mirror
motion-bg-loop-[#0000ff]/reset
```

#### Grayscale
```
motion-grayscale-<in|out|loop>
motion-grayscale-<in|out|loop>-(0|25|50|75|100)
motion-grayscale-<in|out|loop>-[value]

motion-grayscale-in
motion-grayscale-out-50
motion-grayscale-loop
motion-grayscale-in-[0.42]
motion-grayscale-out-[33%]
motion-grayscale-loop-75/mirror
motion-grayscale-loop-[0.875]/reset
```

#### Preset Animations

##### Classics
```
motion-preset-fade
motion-preset-fade-(xs|sm|md|lg)
motion-preset-fade-[<duration>]      // e.g. motion-preset-fade-[1200ms]

motion-preset-slide-<right|left|up|down>
motion-preset-slide-<right|left|up|down>-(xs|sm|md|lg)
motion-preset-slide-<right|left|up|down>-[<value>]    // motion-preset-slide-up-[10px], -[3rem], -[2%]

motion-preset-slide-<up-right|up-left|down-left|down-right>
motion-preset-slide-<up-right|up-left|down-left|down-right>-(xs|sm|md|lg)
motion-preset-slide-<up-right|up-left|down-left|down-right>-[<value>]

motion-preset-focus
motion-preset-focus-(xs|sm|md|lg)
motion-preset-focus-[<blur>]         // e.g. motion-preset-focus-[2px]

motion-preset-blur-<right|left|up|down>
motion-preset-blur-<right|left|up|down>-(xs|sm|md|lg)
motion-preset-blur-<right|left|up|down>-[<blur>]      // e.g. motion-preset-blur-up-[3px]

motion-preset-rebound
motion-preset-rebound-(right|left|up|down)

motion-preset-bounce
motion-preset-expand
motion-preset-shrink
motion-preset-pop
motion-preset-compress
motion-preset-shake
motion-preset-wiggle
```

##### Loops

```
motion-preset-pulse
motion-preset-pulse-(xs|sm|md|lg)
motion-preset-pulse-[<scale>]        // e.g. motion-preset-pulse-[1.05]

motion-preset-wobble
motion-preset-wobble-(xs|sm|md|lg)
motion-preset-wobble-[<value>]       // e.g. motion-preset-wobble-[20%]

motion-preset-seesaw
motion-preset-seesaw-(xs|sm|md|lg)
motion-preset-seesaw-[<deg>]         // e.g. motion-preset-seesaw-[2deg]

motion-preset-oscillate
motion-preset-oscillate-(xs|sm|md|lg)
motion-preset-oscillate-[<value>]    // e.g. motion-preset-oscillate-[20%]

motion-preset-stretch
motion-preset-stretch-(xs|sm|md|lg)

motion-preset-float
motion-preset-float-(xs|sm|md|lg)
motion-preset-float-[<value>]        // e.g. motion-preset-float-[200%]

motion-preset-spin

motion-preset-blink
```

##### Fun
```
motion-preset-typewriter-[<number of letters>]

motion-preset-confetti

motion-preset-flomoji-👉
motion-preset-flomoji-🚀
motion-preset-flomoji-👀
motion-preset-flomoji-👍
motion-preset-flomoji-[🎉]
motion-preset-flomoji-[🌟]
motion-preset-flomoji-[🎸]
motion-preset-flomoji-[Woah!]
```

### Modifiers

#### Duration
```
motion-duration
motion-duration-(75|100|150|200|300|500|700|1000|1500|2000)
motion-duration-(75|100|150|200|300|500|700|1000|1500|2000)/(scale|translate|rotate|blur|grayscale|opacity|background|text)
```

#### Delay
```
motion-delay
motion-delay-(75|100|150|200|300|500|700|1000)
motion-delay-(75|100|150|200|300|500|700|1000)/(scale|translate|rotate|blur|grayscale|opacity|background|text)
```

#### Easing
```
// Basic easings
motion-ease-(linear|in|out|in-out)

// Spring & bounce easings
motion-ease-(spring-smooth|spring-snappy|spring-bouncy|spring-bouncier|spring-bounciest|bounce)

// Additional cubic-bezier easings
motion-ease-(in-quad|in-cubic|in-quart|in-back)
motion-ease-(out-quad|out-cubic|out-quart|out-back)
motion-ease-(in-out-quad|in-out-cubic|in-out-quart|in-out-back)

// Per-property targeting
motion-ease-{any-of-above}/(scale|translate|rotate|blur|grayscale|opacity|background|text)
```

#### Loop
```
motion-loop
motion-loop-infinite
motion-loop-[number]
motion-loop-(infinite|number)/(scale|translate|rotate|blur|grayscale|opacity|background|text)
```

#### Mirror and Reset
- **Mirror**: Reverses the animation direction after completion.
  - Example: `motion-scale-loop-50/mirror`
- **Reset**: Resets the animation to its initial state after completion.
  - Example: `motion-scale-loop-50/reset`

### Combining Animations
```
motion-scale-in-75 motion-translate-y-in-100 motion-rotate-in-90 motion-blur-in-md motion-opacity-in-0
motion-opacity-in-0 motion-translate-y-in-100 motion-scale-in-150 motion-rotate-in-180 motion-grayscale-in-75
motion-scale-in-75 motion-rotate-in-180 motion-translate-x-in-100 motion-blur-in-lg motion-bg-in-blue-500
motion-translate-x-in-100 motion-translate-y-in-50 motion-scale-in-125 motion-rotate-in-45 motion-text-in-purple-500
motion-preset-pop motion-preset-slide-up motion-preset-focus motion-delay-100
motion-preset-shake motion-preset-blur-right motion-preset-stretch motion-delay-200
motion-preset-wiggle motion-preset-slide-down motion-preset-blink motion-delay-150
motion-preset-pop motion-translate-y-loop-50 motion-scale-in-150 motion-rotate-in-360 motion-blur-in-xl
motion-preset-compress motion-translate-x-loop-75 motion-scale-loop-125 motion-rotate-loop-180 motion-delay-100
motion-preset-stretch motion-scale-in-[250%] motion-rotate-in-[720deg] motion-blur-in-[15px] motion-grayscale-in-100
motion-preset-oscillate motion-translate-x-in-[150%] motion-translate-y-in-[150%] motion-scale-in-[175%] motion-rotate-in-[1080deg]
motion-preset-slide-up motion-preset-blur-up motion-scale-in-[300%] motion-rotate-loop-[360deg] motion-delay-150
```



#### Animation State
```
motion-paused
motion-running
```

### Smart Extras

These are not part of the original library, see "What's Different" below for more info. All apply with `!important` so they reliably override animation state regardless of source-order or specificity.

```css
/* Short-hand pause (animation-play-state: paused) */
.pause

/* Short-hand play (animation-play-state: running) */
.play

/* Same as pause, but better name — designed to be removed via JS or
   IntersectionObserver when you want the animation to start. Cascades to
   children + ::before/::after so the whole subtree freezes. */
.wait

/* Motion = 0, completes (or kills) animations forcefully — different from pause.
   Sets every duration and delay to 0ms !important and cascades to children. */
.still
```


## What's different?

Not much. This should be near identical for 99% of purposes.



### prefers-reduced-motion

Currently, tailwindcss-motion manually applies the `@media screen and (prefers-reduced-motion: no-preference)` on [various keyframes](https://github.com/romboHQ/tailwindcss-motion/blob/main/src/keyframes.js) that have basically big translates. It's also applied on some of [their custom one-off](https://github.com/romboHQ/tailwindcss-motion/blob/main/src/presets.js) more fun animations (Flomoji, Typewriter).

Rather than doing that, this library will automatically add the following for simplicity to your CSS:

```css
 @media (prefers-reduced-motion: reduce) {
    *, ::before, ::after {
        --motion-duration: 0.01ms !important;
        --motion-delay: 0ms !important;
        animation-duration: 0.01ms !important;
        animation-delay: 0ms !important;
        transition-duration: 0.01ms !important;
        transition-delay: 0ms !important;
    }
}
```

### ::backdrop

Tailwind compiles `:root {}` and `::backdrop {}` separately for variables since browsers treat them as distinct contexts. Unfortunately, you can't even do something like this `:root, ::backdrop {}` as that does not work.

That's a lot of bytes to do twice... So we skip `::backdrop`. It's rarely used anyway by people.

### typewriter effect supports custom fonts

Unlike the original library, this version doesn't set `font-family: monospace;` for the typewriter effect. This allows for greater flexibility in font choices and the animation, however it may require minor adjustments if spacing issues occur with various custom fonts. You can just do this instead:

```
motion-preset-typewriter-[29] font-mono
```

### confetti doesn't set margin and block

The preset `motion-preset-confetti` normally applies `display: block` and `margin: 0;`. This makes a ton of sense but also can be annoying because it can mess the layout when applying these animations (which goal wise we ideally don't want layout to ever shift when applying an animation). You can instead do this if you want it back perfectly to original:

```
motion-preset-confetti block m-0
```

### Flomoji is back and our version supports JIT

For maximum port, I decided to add Flomoji back and with JIT support:

```
motion-preset-flomoji-👉
motion-preset-flomoji-🚀
motion-preset-flomoji-👀
motion-preset-flomoji-👍
motion-preset-flomoji-[🎉]
motion-preset-flomoji-[🌟]
motion-preset-flomoji-[🎸]
motion-preset-flomoji-[Woah!]
```

### Smart Classes

These are extra short-hands. Note that still and pause (or motion-paused) are different. Every utility below uses `!important` so it always wins.

```css
.pause { animation-play-state: paused !important; }
.play  { animation-play-state: running !important; }

/* You'll need to manually remove "wait" with JS when you want the animation to start.
   This is excellent for triggering when in viewport.
   Note: wait also applies to ::before, ::after, and all descendants. */
.wait, .wait::before, .wait::after,
.wait *, .wait *::before, .wait *::after {
    animation-play-state: paused !important;
}

/* Note: still also applies to ::before, ::after, and all descendants. */
.still, .still::before, .still::after,
.still *, .still *::before, .still *::after {
    --motion-duration: 0ms !important;
    --motion-delay: 0ms !important;
    animation-duration: 0ms !important;
    animation-delay: 0ms !important;
    transition-duration: 0ms !important;
    transition-delay: 0ms !important;
}
```

### Variants (`hover:`, `focus:`, `md:`, `dark:`, `group-hover:` …)

You don't need to do anything special — every UnoCSS variant from `presetUno` / `presetWind4` works on every motion utility automatically. Examples:

```html
<!-- pseudo-classes -->
<button class="hover:motion-preset-pulse-md">hover to pulse</button>
<input class="focus:motion-preset-pulse-sm" />

<!-- breakpoints -->
<div class="md:motion-preset-fade-lg">only fades at ≥ md</div>

<!-- dark mode -->
<div class="dark:motion-preset-blur-up-md">animates in dark mode</div>

<!-- group / peer -->
<div class="group">
  <span class="group-hover:motion-preset-slide-right-md">child slides when parent is hovered</span>
</div>

<!-- stacked -->
<div class="md:hover:motion-preset-shake">≥md AND hovered</div>

<!-- helpers also support variants now -->
<div class="motion-preset-pulse-md hover:wait">freezes mid-loop on hover</div>
```

## Contributing

- The folder tailwind is for the tailwind styles, `tailwindcss-motion-reference` is detached just for easy file comparison and is not used.
- To dev it up here... just run `npm run dev`
- To see the test file, just run `npm run serve`
- To build it all, just run `npm run build`
- For more, reference `package.json`. This may get more sophisticated later but does have a 1 vs the other mode.

## License

In honor of original library this is MIT.

## More

[Via x.com/@whatnicktweets](https://x.com/@whatnicktweets)

https://www.npmjs.com/package/unocss-preset-tailwindcss-motion
