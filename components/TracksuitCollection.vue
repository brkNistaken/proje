<template>
    <div class="tracksuit-collection">
      <div class="image-container">
        <h1 class="collection-title">TRACKSUIT COLLECTION</h1>
        <img src="https://cdn.myikas.com/images/theme-images/1d7a8aad-94ed-4a89-a870-a7ec7610199e/image_1296.webp" alt="Tracksuit Collection" />
      </div>
    </div>
  </template>
  
  <script>
  export default {};
  </script>
  
  <style scoped>
  .tracksuit-collection {
    display: flex;
    justify-content: center;
    align-items: center;
    padding: 0;
    background-color: #f5f5f5;
  }
  
  .image-container {
    position: relative;
    display: inline-block;
    text-align: center; /* Yazıyı yatayda ortala */
  }
  
  .image-container img {
    display: block;
    width: 100%;
    max-width: 1000px; /* Görüntü genişliği sınırı */
    height: auto;
  }
  
  .collection-title {
    position: absolute;
    top: 10px; /* Yazıyı resmin tam üstüne yerleştir (resme yakın olacak şekilde) */
    left: 50%;
    transform: translate(-50%, 0); /* Yatayda ortala */
    font-size: 1.5rem; /* Yazı boyutu */
    font-weight: bold;
    color: #000; /* Siyah yazı */
    text-shadow: 2px 2px 4px rgba(255, 255, 255, 0.8); /* Yazının görünürlüğü için gölge */
    text-transform: uppercase; /* Tamamen büyük harf */
    margin: 0;
  }
  </style>
  