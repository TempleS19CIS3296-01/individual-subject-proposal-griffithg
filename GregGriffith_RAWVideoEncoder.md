# RAW Video Encoder

## Project Abstract
_At least one paragraph description of the overall project. Include a UML use case diagram._ 
### Background
Modern digital video generates a huge data stream that must be stored in some fashion. In most applications this is handled through compression of an RGB image. Many algorithims have been devised over the years, most customized to a specific purpose.

Most color cameras available at this time utilize a single image sensor. In order to allow a single sensor to record all three colors, the sensor uses a color filter array (CFA) arranged in what is referred to as a "Bayer Pattern". In this configuration, each pixel in the sensor senses ony red, green, or blue. The other two values are determined by inerpolation within the camera. The parameters used in this process affect all aspects of the image.

Over the last decade the industry has aknowledged the creative benefits of preserving the bayer pattern encoded data as it comes off of the image sensor. By manipulating the data in this format the creator has greater control over the image, as well as allowing for more radical changes to the image before artifacts appear. The recording of a CFA pattern image has become know as recording a "RAW" image. 

Another benefit of recording this "RAW" image is an immediate reduction in data rate. Reducing the needed bandwidth for a 4K video from GBs/sec, to hundreds of MBs/sec. While this reduction is significant, it still requires a very fast storage medium. In many cases RAW video is needed, but the quality of uncompressed video is not. 

At this time there exist very few compression algorithims that can compress RAW video effectively. Most sutible compression methods employ higly tuned predictors to achieve the desired compression ratios. Since the RAW CFA data only records one of the primary colors at each location, the preditcors in the algorithims become ineffective. Several groups have released compressed RAW formats. Cineform RAW, and RED's REDCODE were two of the first. In the last few months Apple released PRORES RAW, and Blackmagic Design released their own format. None of these are open formats, in the case of REDCODE the output is in fact encrypted to prevent reverse engineering. Neither Apple or Blackmagic Design have provided information on decoding their format.

Cineform, now the most open of them all, was eventually acquired by GoPro and used in their cameras, eventually being standardized by the SMPTE as the VC5 codec. In late 2017 GoPro open sourced the SDK and codec, both of which are available in a public GitHub repo. Unfortunately there is a complete lack of documentation, and the VC5 standard is copyrighted and not distributable. 

### Project Purpose

In recent years there has been a push by the open source community to "hack" off the shelf cameras to improve quality and add features not supported by the manyfacture. In one case, a group is working to release a completly open camera design. Apertus has grown significantly over the years after a successful crowdfunding campaign. While their camera has been evolving, there has been very little effort put to a recording solution. For this project I would like contribute a piece to that solution. 



![Use Case Image](StellaOwl_PayStation.png)

## Project Relevance
_A one paragraph explanation of how the proposal is linked to the educational goals of this class and why this goal is important goal 

This project relates to several of the educational objectives of this course. It requires the cordination of team members to work on several diferent parts of the project. Issues will need to be reported, and tracked to a fix. It will require a solid overall object oriented design, with a well thought test plan. It requires the use of external libraries, and APIs. The use of multi-threading and potentially parallel computing to provide desired performance. In addition there will be a need for significant optimization and code profiling to identify and correct bottlenecks in the system. In the end if this is to be useful it will also need usable documentation. 

## Conceptual Design
_A one-paragraph description of your proposed contribution._
The core goal of this project will be to produce a module that can compress a 4K RAW video stream. This module would be targeted to perform realtime encoding using the NVIDIA Jetson platform. This is an embedded module providing a high performance ARM processor and NVIDIA GPU in a mobile platform.The project would read frames from the Jetsons camera, and use the OpenJPEG and gpu-jpeg2k libraries to process and compress the images before storing them to disk. There are several methods of preparing the RAW data for encoding proposed, in this case the simplest of the methods would be implemented. The code would designed to be modular and allow for change of the preprocessor.

## Background
_A URL reference to the project._
* APERTUS Project: https://apertus.org/
* CINEFORM SDK: https://github.com/gopro/cineform-sdk
* Open JPEG: http://www.openjpeg.org/
* gpu-JPEG: https://github.com/etalab/gpu-jpeg2k
* CUDA accelerated DWT: https://code.google.com/archive/p/gpudwt/
* GPU DWT implementation details: https://www.sitola.cz/papers/858064.pdf

## Required Resources
- Group members
- Hardware and software resource required
