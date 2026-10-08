# Rumi mascot: sprite pack + generator

Everything here was exported straight from `Rumi.psd` at **full resolution** (2138 x 3746 px canvas),
as **lossless PNGs**, with **no resizing and no edits**. Every sprite is cropped to its visible pixels and
its exact position on the PSD canvas is saved in `manifest.json`.

## Folders
```
index.html            the generator (mix looks, save OCs, export PNG/WebP/JPG or a ZIP of all expressions)
manifest.json         every sprite + its x/y/width/height, all in PSD pixels
example-embed.html    ~40 lines showing how to rebuild a look on your own site
poses/
  standing-normal/ standing-holding-something/ laying-on-belly/ sitting-hands-tucked/ extras-typing/
    default/ pastel/ dark/ cyberglass/
      body.png                  (Typing's laptop is part of body.png)
      thumb.png                 small preview, only used by the generator UI
      expressions/neutral.png happy.png excited.png confused.png sad.png angry.png
                  unbothered.png uwu.png dead.png love.png we-deadass-bro.png
aromas/
  thoughts.png sparkles.png surprise.png loading.png anger.png lovely.png confusion.png
```
Each body has **its own** expression files (they are drawn in different colors per body), so always pair an
expression with the body folder it lives in.

## Putting a look together
Stack the layers in this order, each placed at its own `x`, `y` (top-left corner, in PSD pixels):

1. `body`
2. `expression` (from the same body folder)
3. `aroma` (optional): also add the pose's `aromaOffset` `[dx, dy]` to its x/y.

The aromas were drawn around the Standing pose. `aromaOffset` moves them so they sit next to the head
in the other poses (it is the head's position difference from Standing/Normal). `[0, 0]` for Standing/Normal.
You can ignore it and place aromas yourself if you prefer.

`example-embed.html` does exactly this with plain `<img>` tags positioned in percentages, so it scales to any size.

## manifest.json
```
canvas: { width, height }
poses[]:   { id, group, name, aromaOffset: [dx, dy],
             bodies[]: { id, name, thumb,
                         body: { file, x, y, w, h },
                         expressions[]: { id, name, file, x, y, w, h } } }
aromas[]:  { id, name, file, x, y, w, h }
```

## Running the generator
Serve the folder over http (browsers block image export from a double-clicked file):
```
python -m http.server 8000     # then open http://localhost:8000
```
On a real host (GitHub Pages, Netlify, etc.) it just works. Keep `index.html` next to `manifest.json`,
`poses/` and `aromas/`.
