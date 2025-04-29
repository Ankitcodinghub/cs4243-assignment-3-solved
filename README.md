# cs4243-assignment-3-solved
**TO GET THIS SOLUTION VISIT:** [CS4243 Assignment 3 Solved](https://www.ankitcodinghub.com/product/cs4243-instructions-solved-3/)


---

📩 **If you need this solution or have special requests:** **Email:** ankitcoding@gmail.com  
📱 **WhatsApp:** +1 419 877 7882  
📄 **Get a quote instantly using this form:** [Ask Homework Questions](https://www.ankitcodinghub.com/services/ask-homework-questions/)

*We deliver fast, professional, and affordable academic help.*

---

<h2>Description</h2>



<div class="kk-star-ratings kksr-auto kksr-align-center kksr-valign-top" data-payload="{&quot;align&quot;:&quot;center&quot;,&quot;id&quot;:&quot;113954&quot;,&quot;slug&quot;:&quot;default&quot;,&quot;valign&quot;:&quot;top&quot;,&quot;ignore&quot;:&quot;&quot;,&quot;reference&quot;:&quot;auto&quot;,&quot;class&quot;:&quot;&quot;,&quot;count&quot;:&quot;1&quot;,&quot;legendonly&quot;:&quot;&quot;,&quot;readonly&quot;:&quot;&quot;,&quot;score&quot;:&quot;5&quot;,&quot;starsonly&quot;:&quot;&quot;,&quot;best&quot;:&quot;5&quot;,&quot;gap&quot;:&quot;4&quot;,&quot;greet&quot;:&quot;Rate this product&quot;,&quot;legend&quot;:&quot;5\/5 - (1 vote)&quot;,&quot;size&quot;:&quot;24&quot;,&quot;title&quot;:&quot;CS4243 Assignment 3 Solved&quot;,&quot;width&quot;:&quot;138&quot;,&quot;_legend&quot;:&quot;{score}\/{best} - ({count} {votes})&quot;,&quot;font_factor&quot;:&quot;1.25&quot;}">

<div class="kksr-stars">

<div class="kksr-stars-inactive">
            <div class="kksr-star" data-star="1" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="2" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="3" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="4" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="5" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
    </div>

<div class="kksr-stars-active" style="width: 138px;">
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
    </div>
</div>


<div class="kksr-legend" style="font-size: 19.2px;">
            5/5 - (1 vote)    </div>
    </div>
This lab has four parts. For each part, implement the outlined functions in lab3.py and run them in the notebook lab3.ipynb. Exploratory questions are embedded directly at the end of the sections; write your answers directly into the notebook. Expected outputs are supplied as reference, but your outputs do not need to match exactly.

Upload to LumiNUS your completed lab3.py and lab3.ipynb by zipping them into a file named AXXX1_AXXX2.zip, where AXXX is the student number of the group members. Submit one file per group. Missing files, incorrectly formatted code that does not run, etc. will be penalized.

Objective

This lab covers keypoint detection and feature descriptors. We will explore the Harris Corner Detector, a simplified version of the SIFT descriptor and two applications for keypoint matching: image stitching and symmetry detection.

Unfortunately, we need to change the coordinate convention (x- and y-axis are swapped compared to Lab 2, see Figure on the right) to stay consistent with the conventions of the OpenCV functions which are used in this lab.

Part 1: Keypoint Detection, Description, and Matching (35%)

This part covers foundations of keypoint descriptors and matching which will be used in later parts. We provide the wrapper describe_keypoints which calls either the naïve descriptor or the simplified version of SIFT.

● harris_corners() detects Harris corner keypoints. For each pixel in an imsage,

1. Compute image gradient 𝐼𝑥, 𝐼𝑦 and compose the second moment matrix H. Note that the elements A, B, and C of matrix H are obtained by summing the elements in some window W:

i. 𝐻 = [𝐴𝐵 𝐵𝐶 ] 𝐴 𝐵 𝑊 𝐼𝑥𝐼𝑦 𝐶

Consider an efficient implementation of the window-wise summation based on convolution (i.e., do not use for-loops). Weight the elements uniformly in the window for the summation. Hint: Consider using built-in functions skimage.filters.sobel_v, sobel_h and scipy.ndimage.filters.convolve.

2. Compute the corner response 𝑅 = 𝑑𝑒𝑡(𝐻)– 𝑘 (𝑡𝑟(𝐻))2 with 𝑘 = 0.04.

3. Find local maxima using the provided non-maximum suppression; the local maxima in the response map corresponds to the keypoints.

● naive_descriptor() computes a local descriptor based on the normalized pixel intensity,

𝐼 𝜇

i.e. 𝐹(𝑥, 𝑦) = . 𝐼(𝑥, 𝑦) is the intensity at a keypoint located at (𝑥, 𝑦) and 𝜇 and 𝜎 are the

𝜎

mean and standard deviation of the pixel intensities in a patch of 5×5 centered at (𝑥, 𝑦). The 0.0001 term in the numerator improves numerical stability.

● simple_sift() is a simplified version of the full SIFT descriptor which is not rotationally invariant. For each keypoint, take a 16 × 16 patch of pixels around the keypoint and compute the image gradient magnitude and orientation at each pixel. For efficiency, consider precomputing the image gradients for the entire image in advance. Divide the patch into a 4×4 grid of cells, where each cell has 4 × 4 = 16 pixels (see Figure 1a).

Figure 1. Schematic visualization of estimating our simplified SIFT descriptor.

For each cell, create a histogram of the gradient orientations with 8 bins of 45° each (e.g., 0° to 44° for bin 0, 45° to 89° for bin 1, etc.). Each pixel’s contribution to the histogram is weighted by the pixel’s gradient magnitude and the weight from a Gaussian kernel of 16 × 16 centered on the keypoint coordinate. Use the provided make_gaussian_kernel. Concatenate the histograms from each cell to form a 4×4×8=128-dimension vector (see Figure 1b). Normalize the vector to unit length by dividing by the vector’s magnitude [link].

● top_k_matches()finds the k top matches between two feature descriptor sets 𝐹1 =

{𝐹11,𝐹12 … 𝐹1𝑖 … 𝐹1𝑀} and 𝐹2 = {𝐹21,𝐹22 … 𝐹2𝑗 … 𝐹2𝑁}. For each descriptor in 𝐹1, find the 𝑘 descriptors in 𝐹2 with the smallest Euclidean distance. Give the output as a list of length-2 tuples. For each tuple, the first element is the descriptor index 𝑖 from 𝐹1 and the second element is a 𝑘long list of length-2 tuples, with indices 𝑗 in 𝐹2 and the Euclidean distance 𝐷(𝐹1𝑖, 𝐹2𝑗). Hint: consider using scipy.spatial.distance.cdist().

● ratio_test_match() checks for 𝐹1𝑖 the ratio between the top 2 matches 𝐹2𝑎 and 𝐹2𝑏. If

𝐷

&lt; 𝜏, then 𝐹1𝑖 and 𝐹2𝑎 are a match. The ratio threshold 𝜏 is given as an argument.

𝐷(𝐹1𝑖,𝐹2𝑏)

Part 2: Image Stitching (25%)

This part uses the matched descriptor pairs from Part 1 and solves the homography between the two images. The images are then warped and stitched together. For this part, use your SIFT descriptor implementation (simple_sift) to match the keypoints for image fp1.png and fp2.png.

If you need more details to help you with the implementation, refer to this StackOverflow post.

● For implementing the above two functions, use the provided transform_homography function that applies a given homography to a set of points.

Part 3: Mirror Symmetry Detection (25%)

For Parts 3 and 4, use the provided function compute_cv2_descriptor, which uses OpenCV’s SIFT implementation since we require rotation-invariant descriptors. Mirror symmetry is defined by a line of reflection or symmetry line (dashed red line in Fig. 3b). This part performs SIFT keypoint matching to solve for candidate points on the symmetry line. SIFT descriptors are rotationally invariant, but not mirror-invariant, so how can they be matched? We create a virtual set of “mirror” descriptors by re-assigning the cell indices and histogram bin indices.

● create_mirror_descriptors()using the provided compute_cv2_descriptor, detect keypoints and compute descriptors from the original image 𝐼𝑜 denoted as 𝐹𝑜 =

{𝐹𝑂1,𝐹𝑂2 … 𝐹𝑂𝑖 … 𝐹𝑂𝑀}.

● shift_sift_descriptor() creates a virtual set of mirror descriptors (see Fig. 3b). Treat the image as if it has been mirrored over a virtual vertical axis (see Figure 3a for conceptual visualization). Shift the cell indices and bin indices of each 8-dimensional vector accordingly. For each 8-dim. vector, as SIFT already shifts the indices to keep the dominant orientation first, the first index (0) will stay in the same position. Remaining bins are reversed, i.e. [0, 1, 2, ..7] remaps to [0, 7, 6, .., 2, 1]. See lab3.py for an example of a SIFT histogram vs. its mirrored version.

● match_mirror_descriptors()matches keypoints between 𝐹𝑜 and mirrored descriptors

𝐹𝑂′ = {𝐹𝑂′1,𝐹𝑂′2 … 𝐹𝑂′𝑖 … 𝐹𝑂′𝑀} (see Fig. 3c)

Figure 3. Symmetric feature matching.

● find_symmetry_lines()takes in pairs of matched descriptors and votes for a candidate symmetry line via the Hough transform. For a matched pair of points 𝑖 and 𝑘′ (see Fig 3d), form a line that intersects the two points; this line is perpendicular to the symmetry line. Solve for the midpoint 𝑚 = (𝑥𝑚, 𝑦𝑚) between 𝑖 and 𝑘′ on the intersecting line and compute the angle 𝜃𝑚 that the line makes with the x-axis.

● hough_vote_mirror() performs Hough voting with parameter space (𝜌,θ). Each intersecting point 𝑚 has one vote defined by 𝜃𝑚 and 𝜌𝑚 = 𝑥𝑚 × 𝑐𝑜𝑠 (𝜃𝑚) + 𝑦𝑚 × 𝑠𝑖𝑛 (𝜃𝑚) . The line(s) of symmetry in the image will be represented by local maxima in the Hough vote space. Use the function find_peak_params (from Lab 2); num_lines is a parameter which limits the number of local maxima that are returned.

Part 4: Rotation Symmetry Detection (15%)

Keypoint matching and Hough voting can also be used to detect rotational symmetry. For this part, we use the orientation and scale attributes for the cv2.Keypoint class named angle and size.

Figure 5. Rotational symmetry detection: a) A shape looks the same after rotations; b) A pair of matched keypoints (green) vote for one candidate center of rotation (red); c) Hough voting is used to select a maxima point from the candidate centers as the predicted center of rotation.

● Using compute_cv2_descriptor, detect keypoints and compute descriptors from a given image denoted as 𝐹 = {𝐹1,𝐹2 … 𝐹𝑖 … 𝐹𝑀}.

● Then implement the function match_with_self which uses top_k_matches, giving 𝐹 as both 𝐹1 and 𝐹2 since we are matching descriptors on an image to itself to find the best three matches. Eliminate the trivial match (a keypoint is matched with itself) and perform the ratio test on the other two matches. If no match is eliminated, pick the best two.

● find_rotation_centers()estimates, for a matched pair of keypoints 𝑝𝑖 = (𝑥𝑖, 𝑦𝑖) and 𝑝𝑗 = (𝑥𝑗, 𝑦𝑗), the coordinates for a candidate centre of rotation:

a. Remove “parallel” matches based on the keypoint orientation i.e. the angle. Wrap around the orientations 𝛷𝑖 and 𝛷𝑗 for 𝑝𝑖 and 𝑝𝑗 respectively to ensure they are within [0, 2𝜋). If 𝛷𝑖 and 𝛷𝑗 are within 1 degree of each other, discard 𝑝𝑖 and 𝑝𝑗. The similar orientations suggest “parallel” keypoints, i.e. there exists no centre of rotation about which 𝑝𝑖 can be rotated to coincide with 𝑝𝑗.

b. Form a line of intersection (see red line in Fig. 4) between 𝑝𝑖 and 𝑝𝑗 and solve for this line the length 𝑑 and the angle 𝛾 that it forms with the x-axis.

c. A center of rotation 𝑐𝑖𝑗 = (𝑥𝑐, 𝑦𝑐) between

𝑝𝑖 and 𝑝𝑗 can be defined by angle

𝛽 = and radius 𝑟 with coordinates

𝑥𝑐 = 𝑥𝑖 + 𝑟 × 𝑐𝑜𝑠(𝛽 + 𝛾) and 𝑦𝑐 = 𝑦𝑖 + 𝑟 × 𝑠𝑖𝑛(𝛽 + 𝛾). Discard if the center is out of image bounds.

● hough_vote_rotation()does Hough voting on the rotation coordinates with

parameter space (𝑥, 𝑦). Matched keypoints 𝑝𝑖 and 𝑝𝑗 vote for the associated center location (𝑥𝑐, 𝑦𝑐) with the vote weighted by the keypoint scales 𝑠𝑖 and 𝑠𝑗 respectively. The vote weight is defined as 𝑤 = (𝑒𝑞)2 where 𝑞 = − |𝑠𝑖−𝑠𝑗|. The global maxima should

(𝑠𝑖+𝑠𝑗)

correspond to the center of rotation.

● Note: pay attention to our coordinate choice because to get the point (𝑥𝑖, 𝑦𝑖) you will need to call I[yi][xi] in your code.
