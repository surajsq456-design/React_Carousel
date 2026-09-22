# Ex05 Image Carousel
## Date:23-09-2026

## AIM
To create a Image Carousel using React 

## ALGORITHM
### STEP 1 Initial Setup:
Input: A list of images to display in the carousel.

Output: A component displaying the images with navigation controls (e.g., next/previous buttons).

### Step 2 State Management:
Use a state variable (currentIndex) to track the index of the current image displayed.

The carousel starts with the first image, so initialize currentIndex to 0.

### Step 3 Navigation Controls:
Next Image: When the "Next" button is clicked, increment currentIndex.

If currentIndex is at the end of the image list (last image), loop back to the first image using modulo:
currentIndex = (currentIndex + 1) % images.length;

Previous Image: When the "Previous" button is clicked, decrement currentIndex.

If currentIndex is at the beginning (first image), loop back to the last image:
currentIndex = (currentIndex - 1 + images.length) % images.length;

### Step 4 Displaying the Image:
The currentIndex determines which image is displayed.

Using the currentIndex, display the corresponding image from the images list.

### Step 5 Auto-Rotation:
Set an interval to automatically change the image after a set amount of time (e.g., 3 seconds).

Use setInterval to call the nextImage() function at regular intervals.

Clean up the interval when the component unmounts using clearInterval to prevent memory leaks.

## PROGRAM

import { useState } from "react";
import "./App.css";

import image1 from "./assets/image1.jpg";
import image2 from "./assets/image2.jpg";
import image3 from "./assets/image3.jpg";

function App() {
  const images = [image1, image2, image3];

  const [currentIndex, setCurrentIndex] = useState(0);

  // Next image
  const nextImage = () => {
    setCurrentIndex((currentIndex + 1) % images.length);
  };

  // Previous image
  const previousImage = () => {
    setCurrentIndex(
      (currentIndex - 1 + images.length) % images.length
    );
  };

  return (
    <div className="container">
      <h1>Image Carousel</h1>

      <div className="carousel">

        <button className="prev" onClick={previousImage}>
          ❮
        </button>

        <img
          src={images[currentIndex]}
          alt={`Slide ${currentIndex + 1}`}
        />

        <button className="next" onClick={nextImage}>
          ❯
        </button>

      </div>

      <div className="dots">
        {images.map((_, index) => (
          <span
            key={index}
            className={index === currentIndex ? "dot active" : "dot"}
            onClick={() => setCurrentIndex(index)}
          ></span>
        ))}
      </div>

      <p>
        Image {currentIndex + 1} of {images.length}
      </p>
    </div>
  );
}

export default App;

* {
  box-sizing: border-box;
}

body {
  margin: 0;
  font-family: Arial, sans-serif;
  background: #f2f2f2;
}

.container {
  text-align: center;
  padding: 40px;
}

h1 {
  margin-bottom: 30px;
}

.carousel {
  position: relative;
  width: 700px;
  max-width: 90%;
  margin: auto;
  overflow: hidden;
}

.carousel img {
  width: 100%;
  height: 400px;
  object-fit: cover;
  border-radius: 10px;
}

button {
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
  border: none;
  background: rgba(0, 0, 0, 0.6);
  color: white;
  font-size: 30px;
  padding: 10px 18px;
  cursor: pointer;
  border-radius: 50%;
}

button:hover {
  background: rgba(0, 0, 0, 0.9);
}

.prev {
  left: 15px;
}

.next {
  right: 15px;
}

.dots {
  margin-top: 20px;
}

.dot {
  display: inline-block;
  width: 12px;
  height: 12px;
  margin: 5px;
  background: #bbb;
  border-radius: 50%;
  cursor: pointer;
}

.dot.active {
  background: #333;
}

p {
  font-size: 18px;
}


## OUTPUT

<img width="1042" height="587" alt="image" src="https://github.com/user-attachments/assets/2722d6a7-bc3c-4f19-9186-61841881f3aa" />

<img width="1045" height="592" alt="image" src="https://github.com/user-attachments/assets/91495292-0574-4836-b006-499acb2a5687" />


## RESULT
The program for creating Image Carousel using React is executed successfully.
