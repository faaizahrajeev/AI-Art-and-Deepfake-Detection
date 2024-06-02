# Deepfake and AI-Generated Art Detection

Recent years have seen innovative advancements in Artificial Intelligence (AI) in the realms of image and video processing, speech and audio recognition, and pattern recognition, leading to the boom in AI art and deepfakes. The evolution of ChatGPT, Dalle-2, and Midjourney has sparked debate about whether AI art qualifies as true art and whether it will eventually displace human artists and creators. AI art generation models are trained on large datasets, often consisting of copyrighted art. Due to this, the resulting picture produced is frequently a manipulated version of the art piece, namely through various techniques - Cutmix, Adversarial Data Poisoning, Inpainting, and Style Transfer. This manipulation constitutes a violation of the rights held by the artists. On a similar note, deep fakes pose threats to privacy and security. We are entering a new age of misinformation and confusion, where we are victims of deepfake phishing scams, identity theft, and malicious political interference. These issues necessitate the development of state-of-the-art algorithms to detect real-life photos and videos, as well as painting and art manipulation. This repo dives deep into the topic of AI art and Deepfake detection, highlighting the most efficient machine learning classification techniques on the DeepfakeArt Challenge and Deepfake Detection Challenge dataset. It aims to highlight the best algorithm that provides reliable results and assists future research in this newly emerging area.                                                                                                                                                                            
<br>
# Deepfake detection - logic/technique

Several features of a video can be manipulated. To identify deepfakes, it is important to understand the different ways a video can be manipulated and give ways to identify them. The following are aspects that were looked into to identify fakes from genuine.

1.	Facial Feature Analysis – This involves analyzing inconsistent blinking patterns, facial feature analysis, which looks at the features’ synchronization, and analyzing the synchronization between the emotion conveyed during the speech (either depicted by content or tone), and the emotion portrayed by the subject’s features.
2.	Lip Syncing – This involves analysis of how well the speech matched the movement of the subject’s lips.
3.	Frame by Frame Consistency – Genuine videos often include consistent lighting and environments. When tampered with, such features can result in variations and glitches, especially around the mouth or digitally altered traits.
4.	Texture Analysis – Checking the texture consistencies around altered features often reveals manipulation, such as smooth spots, and inconsistent grainy ones.
<br>
For this study, speech manipulation, and speech-emotion consistency were not considered. The considered aspects were analyzed by multi-task learning, segmentation and localization, and temporal analysis. Since several aspects are considered, it is necessary to transfer acquired knowledge across the features, for which multitask learning (MTL) was utilized. It is a learning technique, where a single neural network is trained on multiple tasks simultaneously. Segmentation, and localization were also employed to look at the entire frame, the isolated face, and its features. Finally, temporal analysis allowed us to check for inconsistencies over time.
<br><br>

![image](https://github.com/faaizahrajeev/AI-Art-Detection/assets/37416458/8767a93d-a718-4062-b36c-38f3d873dafc)

Figure 1: Each frame is analyzed and given an output array. The first 3 elements are classified as REAL and the last frame as FAKE. The true label is REAL.
<br>
# AI Generated Art Detection - logic/technique

As the images have been manipulated with 4 main techniques (Inpainting /Adversarial/ Cutmix/ Style Transfer), each manipulation method has to be taken into account, and multitask learning has to be employed to accurately classify the image as human or AI-generated. 
<br>
	Cutmix involves cutting pieces of the image and blending another painting with the one in hand. The change in texture, colour, and style consistencies can be abrupt in Cutmix. The model looks for inconsistencies in these aspects.
 <br><br>
![image](https://github.com/faaizahrajeev/AI-Art-Detection/assets/37416458/f578dca5-74d9-4b67-86e9-771e7f0049e2)

 

Figure 2: Cutmix Painting Example. The bottom right corner consists of an image, that appears out of place to the human eye.
<br><br>
	Adversarial Data Poisoning is minutely performed on individual pixels, its changes appearing imperceptible to the human eye. To identify such attacks, the model was trained on Fast Gradient Sign Method (FGSM), Adversarial Proximal Gradient Descent (APGD), and Projected Gradient Descent (PGD). Through this, it identifies unnatural changes in pixel values that do not align with human artwork.
 <br><br>

<img width="568" alt="image" src="https://github.com/faaizahrajeev/AI-Art-Detection/assets/37416458/c73bf420-4c5d-4fa0-bc1c-00271136312e">


Figure 3: Original Painting (Far Left) followed by Adversarial Data Poisoned Images manipulated by APGD, FGSM, and PGD respectively.
<br><br>
	Inpainting involves adding strokes of paintings or filling in empty areas, for example, imagine Mona Lisa’s painting with a Starry Night background. Inpainting, like cutmix, looks for inconsistencies in brush strokes, textures, boundaries, and lighting, that defers from the artists’ usual style.
<br><br>
 ![image](https://github.com/faaizahrajeev/AI-Art-Detection/assets/37416458/b2b505f5-5596-4748-86b0-92740fe297e4)


Figure 4: Inpainting (Left) and the Original Painting (Right).
<br><br>
	The final method of manipulation, Style Transfer, involves resembling the painting styles of famous artists to the painting of another. For style-transferred images, the modified areas tend to show unusual patterns of activation (output values of neurons in network layers) compared to normal images because style-transfer techniques tend to modify textural details that can lead to distinctive feature activations in the network.
<br><br>
<img width="766" alt="image" src="https://github.com/faaizahrajeev/AI-Art-Detection/assets/37416458/32dbdc45-29ed-4299-981a-16662ee3f439">

        

Figure 5: Original Painting (Left), Style Transferred Painting (Center), and the Edges of the Original Painting on which Style Transfer was applied. (Right)
<br><br>



