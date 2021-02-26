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
<td headers="sno">1</td>
<td headers="disease">No Finding</td>
<td headers="bsl">89.99</td>
<td headers="bsl">10.35</td>
<td headers="fsl">94.06</td>
<td headers="fsl">44.38</td>
<td headers="ifsl">94.53</td>
<td headers="ifsl">47.91</td>
</tr>
<tr>
<td headers="sno">2</td>
<td headers="disease">Enlarged Cardiomediastinum</td>
<td headers="bsl">100.0</td>
<td headers="bsl">0.0</td>
<td headers="fsl">100.0</td>
<td headers="fsl">40.0</td>
<td headers="ifsl">100.0</td>
<td headers="ifsl">53.28</td>
</tr>
<tr>
<td headers="sno">3</td>
<td headers="disease">Cardiomegaly</td>
<td headers="bsl">88.63</td>
<td headers="bsl">11.30</td>
<td headers="fsl">93.88</td>
<td headers="fsl">47.87</td>
<td headers="ifsl">93.93</td>
<td headers="ifsl">51.32</td>
</tr>
<tr>
<td headers="sno">4</td>
<td headers="disease">Lung Opacity</td>
<td headers="bsl">71.83</td>
<td headers="bsl">28.51</td>
<td headers="fsl">86.14</td>
<td headers="fsl">61.23</td>
<td headers="ifsl">85.53</td>
<td headers="ifsl">63.56</td>
</tr>
<tr>
<td headers="sno">5</td>
<td headers="disease">Lung Lesion</td>
<td headers="bsl">99.91</td>
<td headers="bsl">0.0</td>
<td headers="fsl">99.97</td>
<td headers="fsl">44.14</td>
<td headers="ifsl">99.98</td>
<td headers="ifsl">48.16</td>
</tr>
<tr>
<td headers="sno">6</td>
<td headers="disease">Edema</td>
<td headers="bsl">80.49</td>
<td headers="bsl">20.01</td>
<td headers="fsl">89.33</td>
<td headers="fsl">50.49</td>
<td headers="ifsl">89.80</td>
<td headers="ifsl">54.14</td>
</tr>
<tr>
<td headers="sno">7</td>
<td headers="disease">Consolidation</td>
<td headers="bsl">99.98</td>
<td headers="bsl">0.0</td>
<td headers="fsl">100.0</td>
<td headers="fsl">42.79</td>
<td headers="ifsl">100.0</td>
<td headers="ifsl">46.97</td>
</tr>
<tr>
<td headers="sno">8</td>
<td headers="disease">Pneumonia</td>
<td headers="bsl">99.48</td>
<td headers="bsl">0.57</td>
<td headers="fsl">99.82</td>
<td headers="fsl">48.48</td>
<td headers="ifsl">99.70</td>
<td headers="ifsl">47.69</td>
</tr>
<tr>
<td headers="sno">9</td>
<td headers="disease">Atelectasis</td>
<td headers="bsl">94.48</td>
<td headers="bsl">5.74</td>
<td headers="fsl">97.31</td>
<td headers="fsl">47.29</td>
<td headers="ifsl">97.11</td>
<td headers="ifsl">50.04</td>
</tr>
<tr>
<td headers="sno">10</td>
<td headers="disease">Pneumothorax</td>
<td headers="bsl">99.92</td>
<td headers="bsl">0.0</td>
<td headers="fsl">99.94</td>
<td headers="fsl">42.46</td>
<td headers="ifsl">99.90</td>
<td headers="ifsl">48.64</td>
</tr>
<tr>
<td headers="sno">11</td>
<td headers="disease">Pleural Effusion</td>
<td headers="bsl">79.94</td>
<td headers="bsl">20.25</td>
<td headers="fsl">89.70</td>
<td headers="fsl">52.08</td>
<td headers="ifsl">88.56</td>
<td headers="ifsl">55.85</td>
</tr>
<tr>
<td headers="sno">12</td>
<td headers="disease">Pleural Other</td>
<td headers="bsl">100.0</td>
<td headers="bsl">0.0</td>
<td headers="fsl">100.0</td>
<td headers="fsl">49.47</td>
<td headers="ifsl">100.0</td>
<td headers="ifsl">46.31</td>
</tr>
<tr>
<td headers="sno">13</td>
<td headers="disease">Fracture</td>
<td headers="bsl">100.0</td>
<td headers="bsl">0.0</td>
<td headers="fsl">100.0</td>
<td headers="fsl">50.0</td>
<td headers="ifsl">100.0</td>
<td headers="ifsl">50.73</td>
</tr>
<tr>
<td headers="sno">14</td>
<td headers="disease">Support Devices</td>
<td headers="bsl">75.19</td>
<td headers="bsl">23.31</td>
<td headers="fsl">87.49</td>
<td headers="fsl">57.63</td>
<td headers="ifsl">86.96</td>
<td headers="ifsl">58.13</td>
</tr>
</tbody>
</table>

## Acknowledgements
