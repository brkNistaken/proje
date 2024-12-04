<template>
    <div class="category-slider">
      <div class="category-slide">
        <a href="/Mont">
          <img
            src="https://cdn.myikas.com/images/theme-images/1cbb3273-469a-45aa-9eb1-fa82e21690e3/image_720.webp"
            alt="Mont"
          />
          <div class="text">
            <h2>MONT</h2>
            <p>& CEKET</p>
            <button>TÜMÜNÜ GÖR</button>
          </div>
        </a>
      </div>
      <div class="category-slide">
        <a href="/eşofman">
          <img
            src="https://cdn.myikas.com/images/theme-images/12bd6259-2a52-4503-a058-87dd7dd81b4f/image_720.webp"
            alt="Eşofman"
          />
          <div class="text">
            <h2>EŞOFMAN</h2>
            <p>BAGGY & RELAXED IT</p>
            <button>TÜMÜNÜ GÖR</button>
          </div>
        </a>
      </div>
      <div class="category-slide">
        <a href="/bere">
          <img
            src="https://cdn.myikas.com/images/theme-images/f250d12b-699d-471e-86e4-fef264d0646a/image_720.webp"
            alt="Bere"
          />
          <div class="text">
            <h2>AKSESUARLAR</h2>
            <p>BERE,ÇORAP VE DAHASI</p>
            <button>TÜMÜNÜ GÖR</button>
          </div>
        </a>
      </div>
    </div>
  </template>
  
  <script>
  
  </script>
  
  <style>
  .category-slider {
    display: flex;
    justify-content: center;
    gap: 20px;
    padding: 20px;
    background-color: #fff;
  }
  .category-slide {
    width: 100%;
    height: auto;
    position: relative;
    overflow: hidden;
    border: 1px solid #ddd;
    border-radius: 0px;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
    object-fit: cover;
  }
  .category-slide img {
    width: 100%;
    height: 100%;
    object-fit: cover;
    transition: all 0.3s ease;
  }
  .text {
    position: absolute;
    top: 25%;
    left: 0%;
    width: 100%;
    height: 100%;
    color: white;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    text-align: center;
    font-family: "Oswald", -apple-system, system-ui, BlinkMacSystemFont,
      "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif;
  }
  .category-slide:hover img {
    width: 100%;
    height: 105%;
    object-fit: cover;
  }
  .text h2 {
    font-size: 2rem;
    margin: 0px;
    padding: 0px;
    box-sizing: border-box;
    text-transform: uppercase;
    font-weight: 600;
  }
  .text p {
    font-size: 1rem;
    font-weight: 700;
    margin: 0px;
    padding: 0px;
    box-sizing: border-box;
  }
  .text button {
    background-color: white;
    color: black;
    width: 35%;
    border: none;
    padding: 14px;
    cursor: pointer;
    font-size: 14px;
    border-radius: 0px;
    text-transform: uppercase;
    transition: background-color 0.3s;
    font-weight: bold;
    transition: all .3s;
    box-sizing: border-box;
  }
  
  .text button:hover {
    background-color: black;
    color: white;
  }
  </style>