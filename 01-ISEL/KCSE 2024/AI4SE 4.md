### Paper 1
Model hubs example: Hugging Face, PyTorch

Problem: fine-tuning & applying new data sets are difficult
* this is due to user-centric design of the open model hubs
	* standardization

**Compose** PTMs to fit the requirements?
* why compose?
	* user-specific models are difficult to find + exact match may not exist

This paper has very practical motivations
* users need exact matching models for their use
	* but this is difficult to do because of the lack of documentation (user-centric design)

Case study (using. an (artificial?) example to repeatedly show their motivation):
step1: detection
step2: because no desired label, move on to classification
step3: upscaling model

questions:
can this problem be solved by requiring users of the model hubs to specify their model specifications?
* not the only probem
	* description standard
	* searching is difficult
	* user-env
	* measurements
* the problem that the exact match may not exist remains
	* which seems to be the more important one
		* but the other problem is more highlighted
What are the advantages compared to fine-tuning models to fit our use?
* used fine-tuning to highlight the motivation
* but clearly possible to integrate both approaches together
Are there online resources to create a composition?
* this is a new idea
	* HuggingGPT may be an interesting read

### Paper 3
graph convolution network

crawling vs scraping
* iteratively searching for web pages: crawling
* extraction of the data from the web pages: scraping

problem: adapting to diverse web services

original approaches: OCR, DOM based
* this intro paints the big picture to the audience

why graphs?
... no answer
using graphs, can adapt to different structures
* text, image, etc.

### Paper 4
intro: **realistic** testing is important -> **natural**
variational autoencoders provide latent space
* compressed dimensions of the input (in this case images)
* this provides efficiency
* used this to their advantage
because redundant information is compressed, high entropy, crucial semantics are the targets of mutation -> generates test datasets

one of the results: confusion of human perception
* what is the significance of this?
	* "This is to verify that SINVAD encodes a realistic space and is not simply memorizing images"
	* "show that images made by SINVAD are realistic and semantically confusing to people, indicating that the space SINVAD searches is close to the realistic image space"



