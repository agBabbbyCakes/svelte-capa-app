<!-- src/Slideshow.svelte -->
<script>
    let currentSlideElement;
    let slides = [
      {
        path: 'path/to/image1.jpg',
        content: 'Sample content for slide 1',
        name: 'Slide 1'
      },
      {
        path: 'path/to/image2.jpg',
        content: 'Sample content for slide 2',
        name: 'Slide 2'
      },
      {
        path: 'path/to/image2.jpg',
        content: 'Sample content for slide 2',
        name: 'Slide 3'
      },
      {
        path: 'path/to/image2.jpg',
        content: 'Sample content for slide 2',
        name: 'Slide 4'
      },
      {
        path: 'path/to/image2.jpg',
        content: 'Sample content for slide 2',
        name: 'Slide 5'
      },
      {
        path: 'path/to/image2.jpg',
        content: 'Sample content for slide 2',
        name: 'Slide 6'
      },
      {
        path: 'path/to/image2.jpg',
        content: 'Sample content for slide 2',
        name: 'Slide 7'
      },
      {
        path: 'path/to/image2.jpg',
        content: 'Sample content for slide 2',
        name: 'Slide 8'
      },
      // ... Add all slides up to Slide 10 in this manner
    ];
  
    let currentSlide = 0;
  
    function nextSlide() {
      currentSlide = (currentSlide + 1) % slides.length;
    }
  
    function prevSlide() {
      currentSlide = currentSlide > 0 ? currentSlide - 1 : slides.length - 1;
    }
  
    function goToSlide(index) {
      currentSlide = index;
    }
  </script>
  
  <div class="slideshow-container">
    <div class="slide">
        <h2>{slides[currentSlide].name}</h2>
      <img src={slides[currentSlide].path} alt={`Image for ${slides[currentSlide].name}`} />
      <p>{slides[currentSlide].content}</p>
    </div>
    <button on:click={prevSlide}>Previous</button>
    <button on:click={nextSlide}>Next</button>
    <div class="slide-buttons">
      {#each slides as slide, index}
        <button on:click={() => goToSlide(index)}>{slide.name}</button>
      {/each}
    </div>
  </div>
  
  <style>
    .slideshow-container {
      width: 100%;
      max-width: 1200px;
      margin: 0 auto;
      text-align: center;
    }
  
    .slide {
      width: 100%;
      max-width: 1200px;
      height: auto;
      margin: 20px 0;
      box-shadow: 0px 0px 10px rgba(0,0,0,0.1);
    }
  
    img {
      width: 100%;
      height: auto;
      aspect-ratio: 16/9;
    }
  
    .slide-buttons {
      display: flex;
      flex-wrap: wrap;
      gap: 10px;
      justify-content: center;
    }
  </style>
  