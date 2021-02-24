<h1 align='center'>Few-Shot Learning - Radiology</h1> <br>

## Tables  of Contents
- [Introduction](#introduction)
- [Architecture](#architecture)
- [Algorithm Modelling](#algorithm)
- [Dependencies](#dependencies)
- [Results](#results)
- [Acknowledgements](#acknowledgements)


## Introduction

This GitHub repository is the codebase for the research paper titled - '**Few-shot Transfer Learning to Improve Chest X-Ray Pathology Detection using limited Triplets**'. The paper discusses about the training of Few-Shot Learning coupled with triplet images to boost the classification of Chest X-Ray Images. The traning method proposed in the paper can be used in rapid re-training oppurtunities for human-in-the-loop systems, where a radiologist can relabel false inferences and the model can be quickly retrained.

## Architecture

A DenseNet 121 pre-trained model is used as the baseline algorithm. The validation inference of baseline algorithm is used to create dataset (using image triplets) to train Few-Shot Learning algorithm. The data creation and further treatment of data is provided in the following flow chart.

![Architectural Flowchart](/images/few_shot_learning.jpeg)

Creating data for trianing and validation does involve same steps. Only 150 image triplets are collected for training the algorithm, whereas all the false inference images are used for validation.

## Algorithm Modelling

The pre-trained model was modified to create 128-dimensional vectors for each image in a triplet. The few-Shot Learning model is trained using Adam optimizer for 5 epochs. PPV(Positive Prediction Value) and NPV (Negative Prediction Value) are used as evaluation metrics. We experimented by creating another Few-Shot Learning model where all the pahologies are trained and validated at once, which is referred as **Incremental Training**. 

```math
PPV = TP/(TP+FP)
```

```math
NPV = TN/(TN+FN)
```

## Dependencies

## Results

<table cellspacing="0" summary="" class="chart">
<caption>
Results from Fine-tuned Algorithm, Few-Shot Learning and Incremental FSL Algorithm
</caption>
<thead>
<tr>
<th class="toplevel"></th>
<th class="toplevel"></th>
<th class="toplevel" colspan="2">Baseline Algorithm</th>
<th class="toplevel" colspan="2">FSL Algorithm</th>
<th class="toplevel" colspan="2">Incremental FSL Algorithm</th>
</tr>
<tr>
<th headers="sno">S.No</th>
<th headers="disease">Pathology</th>
<th headers="bsl">PPV</th>
<th headers="bsl">NPV</th>
<th headers="fsl">PPV</th>
<th headers="fsl">NPV</th>
<th headers="ifsl">PPV</th>
<th headers="ifsl">NPV</th>
</tr>
</thead>
<tbody>
<tr>
<th headers="sno">1</th>
<th headers="disease">No Finding</th>
<th headers="bsl">89.99</th>
<th headers="bsl">10.35</th>
<th headers="fsl">94.06</th>
<th headers="fsl">44.38</th>
<th headers="ifsl">94.53</th>
<th headers="ifsl">47.91</th>
</tr>
</tbody>
</table>

## Acknowledgements
