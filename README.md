# 🛰️ Satellite-Based Land Use Compliance Screening

CNN-based classification of Sentinel-2 satellite imagery to detect 
mismatches between declared and actual land use — simulating a 
screening tool for agricultural subsidy compliance (EU CAP-style).

## Problem
Under the European Union's Common Agricultural Policy, farmers receive a yearly subsidy based on how they declare their land is being used, for example as cropland. In reality, some of that land quietly changes into something else over time: an abandoned lot, a small industrial site, or new housing, while it keeps being reported (and paid for) as farmland. Catching this today mostly relies on government inspectors physically visiting parcels one by one, which is slow, expensive, and impossible to repeat for every farm every year. This project explores a simpler question: could a computer look at a satellite photo of a parcel and work out on its own what the land actually looks like, so inspectors know exactly where to check first?

## Approach
The project uses a Convolutional Neural Network, a type of AI model that is especially good at recognizing patterns in images (the same basic idea that lets your phone automatically sort your photos by what is in them). The model is trained on EuroSAT, a public dataset of thousands of real photos taken by Sentinel 2, a European satellite that images the entire planet every few days. Each photo in the dataset already comes labeled with its true land type, such as forest, cropland, industrial, or residential, so the model can learn what each one actually looks like from above. Once trained, it can look at a brand new satellite photo of a parcel and predict its real land use. To test whether this could work as an actual compliance tool, the project then simulates a realistic scenario: some parcels are randomly given a false declared land type, and the model's prediction is compared against that declaration. When the two disagree, the parcel gets flagged for a human inspector to review, turning a plain image classifier into a practical way of deciding where limited inspection time is best spent.

## Results
- 85.7% training / 85.15% validation accuracy
- Compliance screening: 98.5% recall / 54.7% precision (no filter)
- With confidence filtering (>0.90): 90.2% precision / 62.9% recall
- [insert your accuracy chart and precision/recall chart images here]

## Key Insight
[your precision/recall trade-off insight — this is the strongest part]

## Tech Stack
Python, TensorFlow/Keras, EuroSAT dataset (Sentinel-2 imagery)
