---
layout: gallery
title: MACFE 2025
thumbnail: /gallery2025/1.PNG
images:
    - /gallery2025/1.PNG
    - /gallery2025/2.PNG
    - /gallery2025/3.PNG
    - /gallery2025/4.PNG
    - /gallery2025/5.PNG
    - /gallery2025/6.PNG
---

<head>
    <link href="/lightboxCSS/lightbox.css" rel="stylesheet" />
</head>

<script src="/lightboxJS/lightbox-plus-jquery.js"></script>

<script> src="/lightboxJS/lightbox.js"</script>

<script>
    lightbox.option({
        'fadeDuration': 200,
        'imageFadeDuration': 200,
        'resizeDuration': 200,
        'alwaysShowNavOnTouchDevices': true,
        'showImageNumberLabel': false,
        'fitImagesInViewport': true
    })
</script>

<style>
.masonry-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
  grid-auto-rows: 1px;
  gap: 10px;
}
.masonry-item {
  break-inside: avoid;
}
.masonry-item img {
  width: 100%;
  height: auto;
  display: block;
  border-radius: 6px;
}
.masonry-item a img:hover {
  transform: scale(1.05);
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.2);
}
</style>

<script>
function resizeAllMasonryGrids() {
  document.querySelectorAll(".masonry-grid").forEach(grid => {
    const rowHeight = 1;
    const rowGap = parseInt(getComputedStyle(grid).getPropertyValue("gap"));

    grid.querySelectorAll(".masonry-item").forEach(item => {
      const img = item.querySelector("img");
      if (!img.complete) {
        img.addEventListener("load", () => resizeItem(item, grid, rowHeight, rowGap));
      } else {
        resizeItem(item, grid, rowHeight, rowGap);
      }
    });
  });
}
function resizeItem(item, grid, rowHeight, rowGap) {
  const content = item.querySelector("img");
  const height = content.getBoundingClientRect().height;
  const span = Math.ceil((height + rowGap) / (rowHeight + rowGap));
  item.style.gridRowEnd = `span ${span}`;
}

window.addEventListener("load", resizeAllMasonryGrids);
window.addEventListener("resize", resizeAllMasonryGrids);
</script>










