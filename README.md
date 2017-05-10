# Mosaix - An iOS Photo Mosaic App
### Nathan Eliason & Shelly Bensal
<em>Updated May 10th, 2017</em>

## Summary
______

We created an iOS application which uses the Metal framework to generate photo mosaics in parallel, on-demand. Using the photos already in the device's Photo Library, Mosaix reconstructs the reference photo by selecting photos which match in color, shape, and contrast and placing them in a grid pattern representing the original image. <!--- Insert sentence here directly comparing our abilities to apps in the App Store/our naive implementation. -->

<p align="center">
  <img width="350" src="https://hunt.blob.core.windows.net/web-images/parallel/dog.jpg">
  <img width="350" src="https://hunt.blob.core.windows.net/web-images/parallel/mosaic_dog.jpg"><br/>
  <em>A reference and composite comparison generated by our parallel algorithm, chosen to be of "low-quality" and "high grid size" .</em>
</p>

#### Demo
 - We can demonstrate the app live on an iPhone, by taking a picture live and having the application generate a composite mosaic of that image on the spot with both a naive and parallel implementation.

## Background 
______
Our application is a Swift mobile app with a fairly simple user interface; the user selects the desired image (referred to as the _reference photo_) and adjusts the grid size and quality. At this point, the application reassembles the selected image (into the _composite photo_) of the other images in the users' libraries, presenting the user with the _composite_ as a final result.

There were two main algorithms we parallelized - 1) generating a reasonable representation of photos within the Photo Library so that we can efficiently detect what the best match for a particular subsection of our reference photo is, and 2), breaking down the reference photo into sections and choosing a single "best" image to represent each section in the composite image.

<!---
TODO: Add more about our implementation here.  
-->

#### Platform Choice & Resources 

Mosaix made the most sense on a mobile device because that's the platform on which a majority of our everyday photos are taken and stored. Creating a mobile app made it easy for the end user to take a photo and see a live result, and made sharing the composite image much simpler. 

In particular, our choice of iOS 10 on iPhone 7 is driven mostly by the inclusion of the Metal framework, which gave us unprecendented low-level access to the GPU on the iPhone 7. Not only was the hardware specifically designed with photo processing in mind, but the software gave us complete control over multi-threading and image processing and a simple way of accessing a library of existing photos.

#### Major Challenges

<!---
TODO: Rewrite to better address what we tried.
-->

 - While each square section of the reference photo is in itself independent, communication between selections of adjacent squares are important for flow in the overall image -- it will be important to select photos that don't contrast highly along the seams between photos in order for the reference photo to be visible from the composite image.
 - Additionally, communication between selections of similar colors, shapes, and contrast patterns is incredibly important as we are choosing not to use the same source photo twice within the composite image. For example, a reference photo with a solid blue sky could very easily match the same photo across a major portion of the gridspace if there was no communication between selection in that region.

## Approach 
______
 
## Results
______

#### Features
 - Full graphic user interface with automatic photo library access and an in-app camera and photo selector.
 - Adjustable grid size and final quality -- letting the user select how large each source image is framed within the final composite photo and how picky the algorithm is in its selection.
 - Implemented naive and basic parallel photo selection algorithms.
 - Pre-processing of the device's Photo Library that reduces complexity and time of the generation of each individual mosaic.
 - Performance that improves upon existing solutions in the app store. While there are a few apps already that perform similar functions to Mosaix, they consume 30-40s per image to finish processing (depending on grid size and quality).

## References 
______
- Apple Developer Documentation 

## List of Work By Each Student 
______
