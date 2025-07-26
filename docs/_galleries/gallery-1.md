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
    - /gallery2025/1.JPEG
    - /gallery2025/2.JPEG
    - /gallery2025/3.JPEG
    - /gallery2025/4.JPEG
    - /gallery2025/5.JPEG
    - /gallery2025/6.JPEG
    - /gallery2025/7.JPEG
    - /gallery2025/8.jpg
    - /gallery2025/9.jpg
    - /gallery2025/10.jpg
    - /gallery2025/11.jpg
    - /gallery2025/12.JPEG
    - /gallery2025/13.PNG
    - /gallery2025/14.JPEG
    - /gallery2025/15.JPEG
    - /gallery2025/16.JPEG
    - /gallery2025/17.JPEG
    - /gallery2025/18.JPEG
    - /gallery2025/19.JPEG
    - /gallery2025/20.JPEG
    - /gallery2025/21.JPEG
    - /gallery2025/22.JPEG
    - /gallery2025/23.JPEG
    - /gallery2025/24.JPEG
    - /gallery2025/25.JPEG
    - /gallery2025/26.JPEG
    - /gallery2025/27.JPEG
    - /gallery2025/28.JPEG
    - /gallery2025/29.JPEG
    - /gallery2025/30.JPEG
    - /gallery2025/31.JPEG
    - /gallery2025/32.JPEG
    - /gallery2025/33.jpg
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










