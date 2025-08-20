let currentImgIndex = 0;
let galleryImages = [];

function openLightbox(img) {
  const images = Array.from(document.querySelectorAll('.gallery-img')).filter(el => el.style.display !== 'none');
  galleryImages = images;
  currentImgIndex = images.indexOf(img);

  document.getElementById('lightbox').style.display = 'block';
  document.getElementById('lightbox-img').src = img.src;
}

function closeLightbox() {
  document.getElementById('lightbox').style.display = 'none';
}

function showImage(index) {
  if (galleryImages.length === 0) return;
  currentImgIndex = (index + galleryImages.length) % galleryImages.length;
  document.getElementById('lightbox-img').src = galleryImages[currentImgIndex].src;
}

function nextImage() {
  showImage(currentImgIndex + 1);
}

function prevImage() {
  showImage(currentImgIndex - 1);
}

function filterImages(category) {
  const allImages = document.querySelectorAll('.gallery-img');
  allImages.forEach(img => {
    if (category === 'all' || img.classList.contains(category)) {
      img.style.display = '';
    } else {
      img.style.display = 'none';
    }
  });
}
