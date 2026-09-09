# Adding a note

Notes live in `index.html`, inside `<div class="board">`. Each is one block.
They stack into two masonry columns automatically — order in the file is order on screen.

## Text note

```html
<article class="note">
  <div class="nhead">
    <span class="mark" style="background:linear-gradient(150deg,#8E8E94,#5A5A5E)">R</span>
    <b>Research</b><time>Sep 2026</time>
  </div>
  <div class="nbody">
    <h5>Headline</h5>
    <p>Two or three sentences.</p>
  </div>
</article>
```

## Note with an image

Add this line between `</div>` (the nhead) and `<div class="nbody">`:

```html
<img class="nimg" src="images/PROJECT/FILE.jpg" alt="">
```

## Clickable note

Add `data-url` to the article and it becomes clickable, with a "Read →" line
appended automatically:

```html
<article class="note" data-url="https://lydiaamadi.substack.com/p/POST">
```

## Quote note

Use `<p class="quote">` for the line and `<p class="src">` for the attribution
instead of `<h5>` and `<p>`.

## The mark

The little square is a letter on a gradient. Any two hex colours work.
Keep one colour per source so notes from the same project read as a set.
