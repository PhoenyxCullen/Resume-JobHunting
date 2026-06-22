# Solarized Color Reference

Source: https://ethanschoonover.com/solarized/
Author: Ethan Schoonover
License: MIT

Solarized is a sixteen color palette (eight monotones, eight accent colors) designed
for use with terminal and GUI applications. L*a*b values are canonical (White D65,
Reference D50). Other values are matched in sRGB space.

---

## Full Color Table

```
SOLARIZED HEX     16/8 TERMCOL   XTERM/HEX   L*A*B      RGB         HSB
--------- ------- ---- --------  ----------- ---------- ----------- -----------
base03    #002b36  8/4 brblack   234 #1c1c1c 15 -12 -12   0  43  54 193 100  21
base02    #073642  0/4 black     235 #262626 20 -12 -12   7  54  66 192  90  26
base01    #586e75 10/7 brgreen   240 #585858 45 -07 -07  88 110 117 194  25  46
base00    #657b83 11/7 bryellow  241 #626262 50 -07 -07 101 123 131 195  23  51
base0     #839496 12/6 brblue    244 #808080 60 -06 -03 131 148 150 186  13  59
base1     #93a1a1 14/4 brcyan    245 #8a8a8a 65 -05 -02 147 161 161 180   9  63
base2     #eee8d5  7/7 white     254 #e4e4e4 92 -00  10 238 232 213  44  11  93
base3     #fdf6e3 15/7 brwhite   230 #ffffd7 97  00  10 253 246 227  44  10  99
yellow    #b58900  3/3 yellow    136 #af8700 60  10  65 181 137   0  45 100  71
orange    #cb4b16  9/3 brred     166 #d75f00 50  50  55 203  75  22  18  89  80
red       #dc322f  1/1 red       160 #d70000 50  65  45 220  50  47   1  79  86
magenta   #d33682  5/5 magenta   125 #af005f 50  65 -05 211  54 130 331  74  83
violet    #6c71c4 13/5 brmagenta  61 #5f5faf 50  15 -45 108 113 196 237  45  77
blue      #268bd2  4/4 blue       33 #0087ff 55 -10 -45  38 139 210 205  82  82
cyan      #2aa198  6/6 cyan       37 #00afaf 60 -35 -05  42 161 152 175  74  63
green     #859900  2/2 green      64 #5f8700 60 -20  65 133 153   0  68 100  60
```

---

## Semantic Roles by Mode

The naming is a deliberate mirror. Dark mode uses two-digit suffixes (base0x) as
backgrounds and one-digit suffixes (base0, base1) as text. Light mode flips these.

### Dark Mode

| Color  | Role                                             |
|--------|--------------------------------------------------|
| base03 | Background (normal)                              |
| base02 | Background (highlights, selections)              |
| base01 | Comments / secondary content                     |
| base00 | Deemphasized — NOT body text (see note below)    |
| base0  | **Body text / primary content / default code**   |
| base1  | Optional emphasized content                      |
| base2  | Available for reversed/inverted elements         |
| base3  | Available for reversed/inverted elements         |

### Light Mode

| Color  | Role                                             |
|--------|--------------------------------------------------|
| base3  | Background (normal)                              |
| base2  | Background (highlights, selections)              |
| base1  | Comments / secondary content                     |
| base0  | Deemphasized — NOT body text (see note below)    |
| base00 | **Body text / primary content / default code**   |
| base01 | Optional emphasized content                      |
| base02 | Available for reversed/inverted elements         |
| base03 | Available for reversed/inverted elements         |

### IMPORTANT: The base00 trap

> "body text is not base00" — Ethan Schoonover (explicit callout on the project page)

In dark mode, body text is **base0** (#839496), not base00.
In light mode, body text is **base00** (#657b83), not base0.

base00 and base0 are adjacent on the scale but their roles swap entirely between modes.
This is the single most common mistake when implementing Solarized.

### The Mirror Rule

- Dark backgrounds: base03, base02 → Light backgrounds: base3, base2
- Dark body text:   base0           → Light body text:   base00
- Dark emphasized:  base1           → Light emphasized:  base01
- Dark comments:    base01          → Light comments:    base1

---

## Key Pairs

These two pairs have **identical L\* contrast by design**:

| Pair              | Use                                  |
|-------------------|--------------------------------------|
| base03 : base0    | Normal background : body text        |
| base02 : base1    | Highlighted background : text on it  |

Because the lightness difference is identical, text is equally readable on both
normal and highlighted backgrounds. Example: Vim folded text uses base02 bg + base1 fg.

---

## Accent Color Conventions

Accent colors are **foreground (text) only** — never used as backgrounds.
Background must always be a base monotone (base02/base03 dark, base2/base3 light).
All accent colors share a similar L* (~50–65) so no single hue dominates visually —
meaning comes from hue, not brightness.

| Color   | Hex     | Human meaning / typical use              |
|---------|---------|------------------------------------------|
| green   | #859900 | Strings, success, go                     |
| yellow  | #b58900 | Warnings, attention, active selection    |
| orange  | #cb4b16 | Constants, deprecated, important notices |
| red     | #dc322f | Errors, danger, stop                     |
| magenta | #d33682 | Structural/categorical (tags, decorators)|
| violet  | #6c71c4 | Keywords, reserved words                 |
| blue    | #268bd2 | Links, trusted/calm, types               |
| cyan    | #2aa198 | Special values, built-ins, visited links |

---

## Terminal Color Slot Mapping (ncurses / 16-color)

Solarized remaps the 16 terminal color slots from their standard values.
This is why ncurses color names behave unexpectedly in Solarized terminals.

| Slot | ncurses name  | Solarized color | Hex     |
|------|--------------|-----------------|---------|
|  0   | black        | base02          | #073642 |
|  1   | red          | red             | #dc322f |
|  2   | green        | green           | #859900 |
|  3   | yellow/brown | yellow          | #b58900 |
|  4   | blue         | blue            | #268bd2 |
|  5   | magenta      | magenta         | #d33682 |
|  6   | cyan         | cyan            | #2aa198 |
|  7   | white        | base2           | #eee8d5 |
|  8   | brightblack  | base03          | #002b36 |
|  9   | brightred    | orange          | #cb4b16 |
| 10   | brightgreen  | base01          | #586e75 |
| 11   | brightyellow | base00          | #657b83 |
| 12   | brightblue   | base0           | #839496 |
| 13   | brightmagenta| violet          | #6c71c4 |
| 14   | brightcyan   | base1           | #93a1a1 |
| 15   | brightwhite  | base3           | #fdf6e3 |

Notable consequence: "brightblue" in ncurses renders as #839496 (gray) in a Solarized
terminal, and "brightblack" is not a valid ncurses name in most lss/config contexts —
use "default" to reference the terminal's background instead.

---

## 16/5 Palette Modes

Solarized was designed to scale down from 16 colors to **4 base monotones + 1 accent color**
for simpler design contexts (web design, print, single-accent UI themes). In every reduced
palette it retains a strong personality without overwhelming.

The five-color palettes each pick four of the eight monotones appropriate to the mode
(dark or light) plus one accent color. Example reduced palettes:

| Monotones (4)                    | Accent   | Feel              |
|----------------------------------|----------|-------------------|
| base03, base02, base0, base1     | red      | urgent/alert      |
| base03, base02, base0, base1     | yellow   | warm/caution      |
| base03, base02, base0, base1     | blue     | calm/professional |
| base03, base02, base0, base1     | orange   | energetic         |
| base03, base0, base1, base2      | magenta  | creative/distinct |

---

## Precision and Symmetry — L\* Contrast Pairs

The monotone scale has symmetric CIELAB lightness (L*) differences by design.
The two primary content pairs have **identical L\* contrast**:

| Dark mode pair   | L* values  | L* difference | Role                          |
|------------------|-----------|---------------|-------------------------------|
| base03 : base0   | 15 : 60   | 45            | Normal bg : body text         |
| base02 : base1   | 20 : 65   | 45            | Highlight bg : text on it     |

| Light mode pair  | L* values  | L* difference | Role                          |
|------------------|-----------|---------------|-------------------------------|
| base3  : base00  | 97 : 50   | 47            | Normal bg : body text         |
| base2  : base01  | 92 : 45   | 47            | Highlight bg : text on it     |

Result: text is **equally readable** on both normal and highlighted backgrounds in either
mode. This is why Vim folded text (base02 bg + base1 fg) looks just as readable as normal
text (base03 bg + base0 fg) — the contrast is mathematically identical.

Dark↔light inversion preserves all contrast relationships because the monotone scale
was built with symmetric L* steps, not arbitrary color picks.

---

## SCSS Inversion Reference

From the project page — shows how dark/light inversion works by reordering the base
monotones. The accent colors stay fixed; only the base scale flips direction.

```scss
$base03: #002b36;  $base02: #073642;  $base01: #586e75;  $base00: #657b83;
$base0:  #839496;  $base1:  #93a1a1;  $base2:  #eee8d5;  $base3:  #fdf6e3;

@mixin rebase($rebase03,$rebase02,$rebase01,$rebase00,$rebase0,$rebase1,$rebase2,$rebase3) {
    background-color: $rebase03;
    color: $rebase0;
    h1,h2,h3,h4,h5,h6 { color: $rebase1; border-color: $rebase0; }
    a, a:active, a:visited { color: $rebase1; }
}

/* light is default — pass bases in normal order */
html, .light { @include rebase($base3,$base2,$base1,$base0,$base00,$base01,$base02,$base03) }
/* dark — pass bases in reverse order */
.dark         { @include rebase($base03,$base02,$base01,$base00,$base0,$base1,$base2,$base3) }
```
