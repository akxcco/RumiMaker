# Rumi Mascot

A sprite pack and character generator for **Rumi**.

The sprites were exported directly from `Rumi.psd` at full resolution (**2138 × 3746 px**) as lossless PNGs. Nothing was resized or edited during export. Each sprite is cropped to its visible area, with its original position saved in `manifest.json`.

## What's inside

```text
index.html          Rumi's character generator
manifest.json       Sprite data and canvas positions

◆ Aromas
  ├─ Thoughts
  ├─ Sparkles
  ├─ Surprise
  ├─ Loading
  ├─ Anger
  ├─ Lovely
  └─ Confusion

◆ Poses
  ├─ Standing
  │  └─ Bodies
  │     ├─ Holding Something
  │     │  ├─ Cyberglass
  │     │  ├─ Dark
  │     │  ├─ Pastel
  │     │  └─ Default
  │     └─ Normal
  │        ├─ Cyberglass
  │        ├─ Dark
  │        ├─ Pastel
  │        └─ Default
  │
  ├─ Laying
  │  └─ Bodies
  │     └─ Laying on Belly
  │        ├─ Cyberglass
  │        ├─ Dark
  │        ├─ Pastel
  │        └─ Default
  │
  └─ Sitting
     └─ Bodies
        └─ Hands Tucked
           ├─ Cyberglass
           ├─ Dark
           ├─ Pastel
           └─ Default

◆ Extras
  └─ Bodies
     └─ Typing
        ├─ Cyberglass
        ├─ Dark
        ├─ Pastel
        └─ Default
```

Each body has its own set of expressions since the expressions are colored to match their body. Make sure to use the expressions from the same body folder.

## How the sprites work

A Rumi look is built from three layers:

1. **Body**
2. **Expression**
3. **Aroma** (optional)

The sprites use the original PSD canvas coordinates stored in `manifest.json`.

For aromas, the pose's `aromaOffset` can be added to the aroma's position so it lines up with the character's head in different poses. Standing/Normal uses `[0, 0]`.

You can also position the sprites yourself if you don't need the manifest coordinates.

## `manifest.json`

The manifest contains the canvas size, poses, bodies, expressions, and aromas along with their positions and dimensions.

```text
canvas: { width, height }

poses[]:
  id
  group
  name
  aromaOffset: [dx, dy]

  bodies[]:
    id
    name
    thumb

    body:
      file
      x, y, w, h

    expressions[]:
      id
      name
      file
      x, y, w, h

aromas[]:
  id
  name
  file
  x, y, w, h
```

## GitHub Pages

The generator is a static HTML project, so there's no backend or server setup needed.

Keep these in the same repository:

```text
index.html
manifest.json
poses/
aromas/
```

GitHub Pages can serve the project directly.

The generator loads the sprites and manifest from the repository, so the folder structure and file paths need to stay the same.

## License

Check the repository for the current usage and licensing information.
