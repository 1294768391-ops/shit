# 1. Bibliographic Information

*   <strong>Title:</strong> Deep Residual Learning for Image Recognition
*   <strong>Authors:</strong> Kaiming He, Xiangyu Zhang, Shaoqing Ren, and Jian Sun.
*   <strong>Affiliations and Relevant Backgrounds:</strong> All authors were affiliated with Microsoft Research at the time of publication. This team was already well-known for their significant contributions to computer vision, including the PReLU activation and the associated "Delving Deep into Rectifiers" paper, which won the ILSVRC 2015 competition. Kaiming He is a leading figure in deep learning research, particularly in computer vision.
*   <strong>Journal/Conference:</strong> The paper was submitted to arXiv in December 2015 and later published at the <strong>Conference on Computer Vision and Pattern Recognition (CVPR) in 2016</strong>. CVPR is a premier, top-tier international conference in the field of computer vision, making it a highly prestigious venue.
*   <strong>Publication Year:</strong> 2015 (arXiv preprint), 2016 (CVPR publication).
*   <strong>Abstract:</strong> The paper introduces a <strong>residual learning framework</strong> to address the challenge of training extremely deep neural networks. Instead of learning direct mappings, the network layers are reformulated to learn <strong>residual functions</strong> with respect to the layer inputs. This is achieved through <strong>shortcut connections</strong> that perform identity mapping. The authors provide extensive empirical evidence showing that these <strong>Residual Networks (ResNets)</strong> are easier to optimize and gain accuracy from significantly increased depth. They present ResNets with up to 152 layers for the ImageNet dataset, achieving a 3.57% test error, which won first place in the ILSVRC 2015 classification task. The paper also demonstrates the framework's effectiveness on CIFAR-10 with up to 1000 layers and shows its strong generalization to other tasks like object detection on COCO, where it also won first place.
*   <strong>Original Source Link:</strong> https://arxiv.org/abs/1512.03385v1 (This is a link to the preprint version on arXiv).

    ---

# 2. Executive Summary

*   <strong>Background & Motivation (Why):</strong>
    *   <strong>Core Problem:</strong> Prior to this work, the deep learning community observed that simply stacking more layers onto a deep neural network did not always lead to better performance. After a certain depth, network accuracy would saturate and then rapidly degrade. This phenomenon, termed the <strong>"degradation problem,"</strong> was counterintuitive because a deeper model should, in theory, perform at least as well as a shallower one (a potential solution is for the extra layers to learn an identity mapping).
    *   <strong>Importance and Gaps:</strong> The degradation problem was a major obstacle preventing the community from harnessing the full potential of "very deep" models. It was not caused by standard issues like overfitting (as training error also increased) or vanishing/exploding gradients (which were largely addressed by techniques like Batch Normalization). This indicated a fundamental optimization difficulty: standard solvers struggled to approximate identity mappings with stacks of non-linear layers.
    *   <strong>Fresh Angle / Innovation:</strong> The paper proposes a brilliantly simple yet profound idea: instead of forcing layers to learn a complex underlying mapping H(x), let them learn a <strong>residual mapping</strong> F(x) = H(x) - x. The original mapping is then reconstructed as F(x) + x. The core hypothesis is that it is far easier for a network to learn to push a residual F(x) to zero (if an identity mapping is optimal) than to learn the identity mapping H(x) = x from scratch. This is implemented via "shortcut connections" that bypass layers and add the input x to the output of the block.

*   <strong>Main Contributions / Findings (What):</strong>
    1.  <strong>Identification and Solution to the Degradation Problem:</strong> The paper clearly identifies and provides empirical evidence for the degradation problem in very deep "plain" networks and proposes the <strong>Deep Residual Learning framework</strong> as an effective solution.
    2.  <strong>Introduction of the Residual Network (ResNet) Architecture:</strong> The paper introduces a new family of extremely deep yet efficient network architectures built from <strong>residual blocks</strong>. These blocks use parameter-free identity shortcut connections, allowing for the training of networks substantially deeper than previously possible (e.g., 152 layers) without adding significant complexity.
    3.  <strong>State-of-the-Art Performance:</strong> ResNets achieved groundbreaking results, winning 1st place in multiple ILSVRC & COCO 2015 competitions, including:
        *   ImageNet Classification (3.57% top-5 error).
        *   ImageNet Detection.
        *   ImageNet Localization.
        *   COCO Detection.
        *   COCO Segmentation.
    4.  <strong>Extensive Empirical Validation:</strong> The authors demonstrate that ResNets are easier to optimize, converge faster, and benefit from increased depth on multiple datasets (ImageNet, CIFAR-10), including successful training of a 1000+ layer network.

        ---

# 3. Prerequisite Knowledge & Related Work

*   <strong>Foundational Concepts:</strong>
    *   <strong>Convolutional Neural Network (CNN):</strong> A class of neural networks specialized for processing grid-like data, such as images. CNNs use convolutional layers to automatically learn hierarchical features (from simple edges to complex objects).
    *   <strong>Vanishing/Exploding Gradients:</strong> A problem in training deep networks where gradients (error signals used for updating weights) either shrink exponentially to zero (vanish) or grow uncontrollably (explode) as they are propagated backward through many layers. This makes it difficult for the network to learn.
    *   <strong>Stochastic Gradient Descent (SGD):</strong> An iterative optimization algorithm used to train neural networks. It updates the network's weights by calculating the gradient of the loss function with respect to a small "mini-batch" of training data.
    *   <strong>Batch Normalization (BN):</strong> A technique that normalizes the inputs to each layer for each mini-batch. This stabilizes training, allows for higher learning rates, and acts as a regularizer, significantly mitigating the vanishing gradient problem.
    *   <strong>ReLU (Rectified Linear Unit):</strong> An activation function defined as f(x) = max(0, x). It introduces non-linearity into the network, allowing it to learn more complex functions.
    *   <strong>Degradation Problem:</strong> The core problem this paper addresses. As network depth increases, accuracy saturates and then degrades. Crucially, the <strong>training error</strong> also increases, meaning the model is not just overfitting but is fundamentally harder to optimize.

*   <strong>Previous Works:</strong>
    *   <strong>VGGNets ([41]):</strong> Architectures from the University of Oxford that demonstrated the benefits of depth by stacking many `3x3` convolutional layers. They reached up to 19 layers, but were very computationally expensive and began to show signs of saturation.
    *   <strong>GoogLeNet ([44]):</strong> The ILSVRC 2014 winner, which introduced the `Inception` module, a "network-in-network" approach that created wider, multi-path structures. It also used auxiliary classifiers in intermediate layers to combat vanishing gradients in its 22-layer deep network.
    *   <strong>Highway Networks ([42]):</strong> A concurrent work that also introduced shortcut connections. However, their connections were controlled by learnable <strong>gating mechanisms</strong>. In contrast, ResNet's identity shortcuts are parameter-free and always open, ensuring information flow. The paper notes that Highway Networks had not demonstrated accuracy gains with extreme depth (over 100 layers).

*   <strong>Technological Evolution:</strong>
    The field of deep learning for vision progressed from relatively shallow networks (like AlexNet, 8 layers) to "very deep" networks (VGG, 19 layers; GoogLeNet, 22 layers). The consensus was that depth was crucial for learning rich feature hierarchies. However, this pursuit of depth hit a wall: the degradation problem. The community had tools like normalized initialization and Batch Normalization to get training started, but optimization remained a challenge for truly deep models. ResNet shattered this barrier, showing that with the right architecture, depth could be pushed to unprecedented levels (152 layers and beyond) with corresponding gains in accuracy.

*   <strong>Differentiation:</strong>
    *   <strong>vs. Plain Networks:</strong> Plain networks are simple stacks of layers. ResNet differs by adding <strong>shortcut connections</strong> that bypass one or more layers, performing an element-wise addition of the input to the output of the stack.
    *   <strong>vs. Highway Networks:</strong> Highway Networks use <strong>gated shortcuts</strong> with learnable parameters. These gates can "close," making the layer behave like a plain, non-residual function. ResNet's shortcuts are <strong>identity mappings</strong> that are always active and parameter-free, forcing the layers to always learn residual functions. This design choice is simpler, more efficient, and proved more effective at extreme depths.
    *   <strong>vs. GoogLeNet:</strong> GoogLeNet focused on making the network "wider" with its multi-branch Inception module. ResNet's philosophy is simpler: make the network "deeper" by resolving the optimization bottleneck.

        ---

# 4. Methodology (Core Technology & Implementation)

*   <strong>Principles:</strong>
    The core idea is <strong>residual learning</strong>. Instead of trying to make a stack of layers learn a desired mapping H(x), the framework reformulates the problem. The layers are tasked with learning a <strong>residual function</strong> F(x).
    *   Desired Mapping: H(x)
    *   Residual Function: F(x) := H(x) - x
    *   Reconstructed Mapping: H(x) = F(x) + x

        The intuition is that optimizing the residual F(x) is easier than optimizing the original mapping H(x). In the extreme case where the optimal mapping is simply an identity function (H(x) = x), the solver can easily learn to set the weights of the layers to zero, making F(x) = 0. This is hypothesized to be much easier than fitting an identity mapping using a stack of non-linear layers. This reformulation acts as a form of <strong>preconditioning</strong>, biasing the learning towards solutions where layers make small adjustments to an identity mapping.

*   <strong>Steps & Procedures:</strong>
    The residual learning principle is implemented using a <strong>building block</strong> (or "residual block") as shown in Figure 2.

    ![caption](images/2.jpg)
    *Image 2: This diagram shows the structure of a residual block. The input x is passed through a series of "weight layers" (e.g., convolutional layers with ReLU activations) to produce a residual mapping F(x). Simultaneously, the input x bypasses these layers via an "identity" shortcut connection. The output of the block is the element-wise sum F(x) + x, which is then passed through a final activation function (ReLU).*

    The pipeline for a single block is:
    1.  An input x is fed into the main path, which consists of a few (typically two or three) convolutional layers.
    2.  The same input x is also fed into a "shortcut connection" that skips the convolutional layers.
    3.  The output of the convolutional path, F(x), is added element-wise to the input from the shortcut connection, x.
    4.  The result, F(x) + x, is passed through a final activation function (e.g., ReLU).

*   <strong>Mathematical Formulas & Key Details:</strong>
    The core operation of a residual block is defined by:
    $$
    \mathbf { y } = \mathcal { F } ( \mathbf { x } , \{ W _ { i } \} ) + \mathbf { x }
    $$
    *   <strong>Symbol Explanation:</strong>
        *   x: The input vector (or feature map) to the residual block.
        *   y: The output vector (or feature map) of the block.
        *   F(x, {W_i}): The residual mapping to be learned by the layers within the block. {W_i} represents the weights of these layers.
        *   `+`: Element-wise addition.

            In the common case where F has two layers, F = W_2 * σ(W_1 * x), where σ denotes the ReLU activation.

    <strong>Handling Dimension Changes:</strong>
    When the dimensions of the input x and the output of F do not match (e.g., when downsampling or increasing the number of channels), the identity shortcut x cannot be used directly. The paper proposes a linear projection W_s to match the dimensions:
    $$
    \mathbf { y } = \mathcal { F } ( \mathbf { x } , \{ W _ { i } \} ) + W _ { s } \mathbf { x }
    $$
    *   <strong>Symbol Explanation:</strong>
        *   W_s: A projection matrix (implemented as a `1x1` convolution) used to match the dimensions of x to the dimensions of F(x).

            The paper empirically finds that parameter-free identity shortcuts work well and W_s is only necessary for matching dimensions, making the models more efficient.

    <strong>Network Architectures:</strong>
    The paper designs several networks based on the VGG philosophy (mostly using `3x3` filters).

    ![caption](images/3.jpg)
    *Image 3: This figure compares three network architectures. Left: The VGG-19 model. Middle: A 34-layer "plain" network, which is a simple stack of convolutional layers. Right: A 34-layer "residual" network, which is identical to the plain network but with shortcut connections (solid and dotted curved lines) added to form residual blocks. Dotted shortcuts indicate a change in dimension.*

    <table>

      <caption>Note: This table is a transcription of the original data from Table 1, not the original image. It describes the architectures for ImageNet. Building blocks are shown in brackets, with the number of blocks stacked. Downsampling is performed by conv3_1, conv4_1, and conv5_1 with a stride of 2.</caption>
      <tr>
        <td>layer name</td>
        <td>output size</td>
        <td colspan="2">18-layer</td>
        <td colspan="2">34-layer</td>
        <td colspan="2">50-layer</td>
        <td colspan="2">101-layer</td>
        <td colspan="2">152-layer</td>
      </tr>
      <tr>
        <td>conv1</td>
        <td>112×112</td>
        <td colspan="10">7×7, 64, stride 2</td>
      </tr>
      <tr>
        <td>conv2_x</td>
        <td>56×56</td>
        <td colspan="10">3×3 max pool, stride 2</td>
      </tr>
      <tr>
        <td></td>
        <td></td>
        <td>[3×3, 64<br>3×3, 64] × 2</td>
        <td></td>
        <td>[3×3, 64<br>3×3, 64] × 3</td>
        <td></td>
        <td>[1×1, 64<br>3×3, 64<br>1×1, 256] × 3</td>
        <td></td>
        <td>[1×1, 64<br>3×3, 64<br>1×1, 256] × 3</td>
        <td></td>
        <td>[1×1, 64<br>3×3, 64<br>1×1, 256] × 3</td>
      </tr>
      <tr>
        <td>conv3_x</td>
        <td>28×28</td>
        <td>[3×3, 128<br>3×3, 128] × 2</td>
        <td></td>
        <td>[3×3, 128<br>3×3, 128] × 4</td>
        <td></td>
        <td>[1×1, 128<br>3×3, 128<br>1×1, 512] × 4</td>
        <td></td>
        <td>[1×1, 128<br>3×3, 128<br>1×1, 512] × 4</td>
        <td></td>
        <td>[1×1, 128<br>3×3, 128<br>1×1, 512] × 8</td>
      </tr>
      <tr>
        <td>conv4_x</td>
        <td>14×14</td>
        <td>[3×3, 256<br>3×3, 256] × 2</td>
        <td></td>
        <td>[3×3, 256<br>3×3, 256] × 6</td>
        <td></td>
        <td>[1×1, 256<br>3×3, 256<br>1×1, 1024] × 6</td>
        <td></td>
        <td>[1×1, 256<br>3×3, 256<br>1×1, 1024] × 23</td>
        <td></td>
        <td>[1×1, 256<br>3×3, 256<br>1×1, 1024] × 36</td>
      </tr>
      <tr>
        <td>conv5_x</td>
        <td>7×7</td>
        <td>[3×3, 512<br>3×3, 512] × 2</td>
        <td></td>
        <td>[3×3, 512<br>3×3, 512] × 3</td>
        <td></td>
        <td>[1×1, 512<br>3×3, 512<br>1×1, 2048] × 3</td>
        <td></td>
        <td>[1×1, 512<br>3×3, 512<br>1×1, 2048] × 3</td>
        <td></td>
        <td>[1×1, 512<br>3×3, 512<br>1×1, 2048] × 3</td>
      </tr>
      <tr>
        <td></td>
        <td>1×1</td>
        <td colspan="10">average pool, 1000-d fc, softmax</td>
      </tr>
      <tr>
        <td colspan="2">FLOPs</td>
        <td colspan="2">1.8×10⁹</td>
        <td colspan="2">3.6×10⁹</td>
        <td colspan="2">3.8×10⁹</td>
        <td colspan="2">7.6×10⁹</td>
        <td colspan="2">11.3×10⁹</td>
      </tr>
    </table>

    <strong>Deeper Bottleneck Architecture:</strong> For deeper networks (50+ layers), a more efficient "bottleneck" block is introduced to manage computational cost.

    ![caption](images/5.jpg)
    *Image 5: This figure illustrates two types of residual blocks. Left: The basic block used in ResNet-34, with two `3x3` convolutional layers. Right: The "bottleneck" block used in ResNet-50/101/152. It uses a sequence of `1x1`, `3x3`, and `1x1` convolutions. The first `1x1` layer reduces the channel dimension, the `3x3` layer operates on this smaller dimension (the "bottleneck"), and the final `1x1` layer restores the original channel dimension. This design has similar time complexity to the basic block but enables much deeper networks.*

*   <strong>Implementation Details:</strong>
    *   <strong>Training:</strong> Models were trained from scratch using SGD with a mini-batch size of 256.
    *   <strong>Learning Rate:</strong> Started at 0.1 and was divided by 10 when validation error plateaued.
    *   <strong>Regularization:</strong> Weight decay of 0.0001 and momentum of 0.9. Dropout was not used.
    *   <strong>Normalization:</strong> Batch Normalization (BN) was applied after each convolution and before the activation.
    *   <strong>Data Augmentation:</strong> For ImageNet, images were resized with the shorter side sampled from [256, 480]. A `224x224` crop was randomly sampled from the image or its horizontal flip. Standard color augmentation was also used.

        ---

# 5. Experimental Setup

*   <strong>Datasets:</strong>
    *   <strong>ImageNet 2012:</strong> A large-scale image classification dataset with ~1.28 million training images, 50k validation images, and 100k test images across 1000 object categories. This was the primary benchmark for demonstrating the method's power.
    *   <strong>CIFAR-10:</strong> A smaller dataset with 50k training and 10k testing `32x32` color images across 10 classes. Used for analyzing the behavior of extremely deep networks (up to 1202 layers).
    *   <strong>PASCAL VOC 2007 & 2012:</strong> Standard object detection benchmarks used to evaluate the generalization of ResNet features.
    *   <strong>MS COCO:</strong> A more challenging large-scale object detection, segmentation, and captioning dataset with 80 object categories.

*   <strong>Evaluation Metrics:</strong>
    *   <strong>Top-k Error Rate:</strong> Used for image classification.
        1.  <strong>Conceptual Definition:</strong> A prediction is considered incorrect only if the true class label is not among the k classes with the highest predicted probabilities. `top-1` error is the standard misclassification rate, while `top-5` error is more lenient and commonly used for ImageNet. It measures if the model can get the right answer "in its top few guesses."
        2.  <strong>Mathematical Formula:</strong>
            $$
            \text{Top-k Error} = \frac{1}{N} \sum_{i=1}^{N} I(\text{true\_label}_i \notin \{\text{top k predicted labels for sample}_i\})
            $$
        3.  <strong>Symbol Explanation:</strong>
            *   N: Total number of samples in the evaluation set.
            *   `I(·)`: An indicator function that is 1 if the condition inside is true, and 0 otherwise.
            *   true_label_i: The ground-truth class for the i-th sample.
            *   `{top k predicted labels}`: The set of k class labels to which the model assigned the highest probabilities.

    *   <strong>Mean Average Precision (mAP):</strong> Used for object detection.
        1.  <strong>Conceptual Definition:</strong> mAP is the standard metric for evaluating object detection performance. It summarizes the precision-recall curve into a single number, representing the average precision over all object classes. For a given class, <strong>Average Precision (AP)</strong> computes the average precision value across all recall levels. <strong>mAP</strong> is simply the mean of the APs calculated for each class. Some variants, like `mAP@[.5, .95]`, average the mAP over multiple Intersection over Union (IoU) thresholds, providing a more comprehensive evaluation of localization accuracy.
        2.  <strong>Mathematical Formula:</strong> The AP for a single class is the area under the precision-recall curve:
            $\mathrm{AP} = \sum_{k=1}^{K} (r_{k} - r_{k-1}) p_{k}$
            where $p_k$ and $r_k$ are the precision and recall at the k-th threshold. mAP is then:
            $\mathrm{mAP} = \frac{1}{C} \sum_{c=1}^{C} \mathrm{AP}_c$
        3.  <strong>Symbol Explanation:</strong>
            *   C: The total number of object classes.
            *   AP_c: The Average Precision for class c.
            *   K: The number of thresholds/points on the precision-recall curve.
            *   r_k, p_k: The recall and precision at the k-th point.

*   <strong>Baselines:</strong>
    *   <strong>Plain Networks:</strong> The authors' own implementations of deep networks without shortcut connections, designed to have the same depth, width, and computational cost as their ResNet counterparts. These are crucial for isolating the effect of residual learning.
    *   <strong>VGG-16 ([41]):</strong> A well-established deep architecture, serving as a strong and widely recognized baseline.
    *   <strong>GoogLeNet ([44]), PReLU-net ([13]), BN-Inception ([16]):</strong> Other state-of-the-art models at the time, used for comparison in the final results tables.

        ---

# 6. Results & Analysis

## <strong>The Degradation Problem</strong>

![caption](images/1.jpg)
*Image 1: Training error (left) and test error (right) on CIFAR-10 for 20-layer and 56-layer "plain" networks. The deeper 56-layer network shows higher training and test error than the shallower 20-layer network, clearly illustrating the degradation problem.*

This figure provides initial motivation. A deeper model should have the capacity to perform better, but it actually performs worse, even on the training data. This suggests an optimization failure, not overfitting.

## <strong>ImageNet Classification (Section 4.1)</strong>

*   <strong>Plain vs. Residual Networks:</strong>

    ![caption](images/4.jpg)
    *Image 4: Training/validation error on ImageNet. Left: For plain networks, the deeper 34-layer model has higher error than the 18-layer model. Right: For ResNets, the situation is reversed. The deeper 34-layer ResNet achieves significantly lower error than the 18-layer ResNet, demonstrating that residual learning solves the degradation problem.*

    <table>

      <caption>Note: This table is a transcription of Table 2. It shows Top-1 error on ImageNet validation.</caption>
      <thead>
        <tr>
          <th></th>
          <th>plain</th>
          <th>ResNet</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <td>18 layers</td>
          <td>27.94</td>
          <td>27.88</td>
        </tr>
        <tr>
          <td>34 layers</td>
          <td>28.54</td>
          <td>25.03</td>
        </tr>
      </tbody>
    </table>

    <strong>Key Findings:</strong>
    1.  The 34-layer plain net performs worse than the 18-layer plain net (28.54% vs 27.94% error), confirming the degradation problem on ImageNet.
    2.  The 34-layer ResNet is substantially better than the 18-layer ResNet (25.03% vs 27.88% error), showing that ResNets gain accuracy from increased depth.
    3.  The 34-layer ResNet dramatically outperforms its plain counterpart (25.03% vs 28.54% error), proving the effectiveness of the residual learning framework.

*   <strong>Identity vs. Projection Shortcuts:</strong>

    <table>

      <caption>Note: This table is a transcription of the top portion of Table 3, comparing different shortcut options on ImageNet validation.</caption>
      <thead>
        <tr>
          <th>model</th>
          <th>top-1 err.</th>
          <th>top-5 err.</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <td>VGG-16 [41]</td>
          <td>28.07</td>
          <td>9.33</td>
        </tr>
        <tr>
          <td>...</td>
          <td>...</td>
          <td>...</td>
        </tr>
        <tr>
          <td>plain-34</td>
          <td>28.54</td>
          <td>10.02</td>
        </tr>
        <tr>
          <td>ResNet-34 A</td>
          <td>25.03</td>
          <td>7.76</td>
        </tr>
        <tr>
          <td>ResNet-34 B</td>
          <td>24.52</td>
          <td>7.46</td>
        </tr>
        <tr>
          <td>ResNet-34 C</td>
          <td>24.19</td>
          <td>7.40</td>
        </tr>
      </tbody>
    </table>
    
    *   <strong>Option A:</strong> Zero-padding for increasing dimensions (parameter-free).
    *   <strong>Option B:</strong> Projection shortcuts (`1x1` conv) for increasing dimensions, identity otherwise.
    *   <strong>Option C:</strong> All shortcuts are projections.
    
        <strong>Analysis:</strong> Option B is slightly better than A, and C is slightly better than B. However, the differences are marginal. This indicates that projection shortcuts are not essential for solving the degradation problem. The authors chose to use the more efficient Option B for the deeper bottleneck models.

*   <strong>Deeper Bottleneck Architectures & SOTA Results:</strong>

    <table>

      <caption>Note: This table is a transcription of the bottom portion of Table 3 and data from Table 4, showing results of deep bottleneck ResNets.</caption>
      <thead>
        <tr>
          <th>model</th>
          <th>top-1 err.</th>
          <th>top-5 err.</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <td>ResNet-50</td>
          <td>22.85 (single-crop: 20.74)</td>
          <td>6.71 (single-crop: 5.25)</td>
        </tr>
        <tr>
          <td>ResNet-101</td>
          <td>21.75 (single-crop: 19.87)</td>
          <td>6.05 (single-crop: 4.60)</td>
        </tr>
        <tr>
          <td>ResNet-152</td>
          <td>21.43 (single-crop: 19.38)</td>
          <td>5.71 (single-crop: 4.49)</td>
        </tr>
      </tbody>
    </table>

    <strong>Analysis:</strong> Accuracy consistently improves as depth increases from 34 to 50, 101, and 152 layers, without any sign of degradation. The single-model 152-layer ResNet (4.49% top-5 error) outperformed all previous ensemble results.

    <table>

      <caption>Note: This table is a transcription of Table 5, showing ensemble results.</caption>
      <thead>
        <tr>
          <th>method</th>
          <th>top-5 err. (test)</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <td>VGG [41] (ILSVRC'14)</td>
          <td>7.32</td>
        </tr>
        <tr>
          <td>GoogLeNet [44] (ILSVRC'14)</td>
          <td>6.66</td>
        </tr>
        <tr>
          <td>PReLU-net [13]</td>
          <td>4.94</td>
        </tr>
        <tr>
          <td>BN-inception [16]</td>
          <td>4.82</td>
        </tr>
        <tr>
          <td><b>ResNet (ILSVRC'15)</b></td>
          <td><b>3.57</b></td>
        </tr>
      </tbody>
    </table>

    An ensemble of ResNets achieved a remarkable <strong>3.57% top-5 error</strong> on the ImageNet test set, winning the competition by a large margin.

## <strong>CIFAR-10 and Analysis (Section 4.2)</strong>

![caption](images/6.jpg)
*Image 6: Error rates on CIFAR-10. Left: Plain nets show clear degradation as depth increases (e.g., plain-56 has higher error than plain-20). Middle: ResNets show consistent improvement as depth increases from 20 to 56 and 110 layers. Right: Even an extremely deep 1202-layer ResNet can be trained and achieves low training error, though its test error is slightly worse than the 110-layer model, suggesting overfitting.*

<strong>Analysis of Layer Responses:</strong>

![caption](images/7.jpg)
*Image 7: Standard deviation of layer responses on CIFAR-10. The responses are outputs of `3x3` layers after BN but before ReLU/addition. Top: Layers in their original order. Bottom: Responses sorted by magnitude. ResNet layers (solid lines) generally have smaller responses (lower std) than plain network layers (dashed lines). Furthermore, as ResNets get deeper (ResNet-20 vs -56 vs -110), the response magnitudes tend to decrease.*

This provides empirical support for the paper's core hypothesis. The learned residual functions F(x) have small responses, suggesting they are making small corrections to the identity mapping, which is easier for the optimizer.

## <strong>Object Detection (Section 4.3)</strong>

<table>

  <caption>Note: This table is a transcription of Table 8, showing object detection results on COCO validation.</caption>
  <thead>
    <tr>
      <th></th>
      <th>mAP@.5</th>
      <th>mAP@[.5, .95]</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>VGG-16</td>
      <td>41.5</td>
      <td>21.2</td>
    </tr>
    <tr>
      <td>ResNet-101</td>
      <td>48.4</td>
      <td>27.2</td>
    </tr>
  </tbody>
</table>

Simply replacing VGG-16 with ResNet-101 as the backbone in the Faster R-CNN detection framework resulted in a massive <strong>28% relative improvement</strong> in the standard COCO metric (`mAP@[.5, .95]`). This demonstrates the powerful generalization capability of the features learned by ResNets.

---

# 7. Conclusion & Reflections

*   <strong>Conclusion Summary:</strong>
    The paper successfully identifies and solves the degradation problem that had stalled progress in building deeper neural networks. By introducing a simple and elegant residual learning framework, the authors enabled the training of networks far deeper than previously imagined. The resulting ResNet architectures are not only easier to optimize but also gain significant accuracy from increased depth. This led to a new state-of-the-art on ImageNet and demonstrated superior generalization on other vision tasks like object detection, marking a major milestone in deep learning.

*   <strong>Limitations & Future Work:</strong>
    *   The authors acknowledge that for extremely deep models on smaller datasets (like the 1202-layer ResNet on CIFAR-10), <strong>overfitting</strong> becomes a concern. The 1202-layer model had higher test error than the 110-layer model despite similar training error. They suggest that combining ResNets with stronger regularization techniques (like maxout or dropout) could improve results, a direction they leave for future work.
    *   The paper provides a strong empirical case but does not delve deeply into the theoretical reasons why optimizing residual mappings is easier. This opened up a new avenue for theoretical research.

*   <strong>Personal Insights & Critique:</strong>
    *   <strong>Impact and Legacy:</strong> It is difficult to overstate the impact of this paper. ResNet architectures, and the residual connection principle, became the de facto standard for a vast number of computer vision applications and research. The concept of shortcut connections has been a foundational element in subsequent influential architectures, including DenseNets, ResNeXt, and even the Transformer, whose architecture relies heavily on residual connections around its self-attention and feed-forward blocks.
    *   <strong>Simplicity is Genius:</strong> The beauty of the residual block lies in its simplicity. It introduced no new parameters (for identity shortcuts) and a negligible amount of computation (element-wise addition), yet it fundamentally changed what was possible in deep learning. This stands as a powerful lesson in research: sometimes the most effective solutions are the simplest.
    *   <strong>Shift in Perspective:</strong> The paper shifted the focus of network design. Instead of just thinking about what function a layer should compute, it encouraged thinking about *how* to make that computation easier for an optimizer to learn. The idea of learning a *delta* or *perturbation* relative to an identity has proven to be a powerful and generalizable principle.
    *   <strong>Open Questions:</strong> While the paper solved the optimization problem, it raised questions about the intrinsic properties of these deep representations. What exactly are these thousands of layers learning? How redundant are they? This has inspired research into network pruning, efficiency, and understanding the "effective depth" of ResNets.