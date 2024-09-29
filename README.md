# Adaptive Continual Learning with Dynamic Weight Pruning

This repository contains the code and report for applying adaptive continual learning with dynamic weight pruning method.

## Introduction

The proposed method dynamically adjusts learning rates based on weight magnitudes, and assigns lower rates to important weights and higher rates to less critical ones. A weight pruning mechanism further enhances retention by freezing key synapses, thus protecting previously acquired knowledge. The method was evaluated on the Split MNIST task, demonstrating its ability to maintain high performance across sequential tasks while effectively incorporating new information. Validation accuracy and loss metrics indicate superior retention of prior knowledge compared to existing methods. Additionally, the results align with the "Lottery Ticket Hypothesis," suggesting that pruned subnetworks can sustain high performance. This approach offers a scalable and resource-efficient solution for real-world AI systems, with future work focusing on enhancing pruning techniques and expanding applicability to more complex datasets.

## Execution Flow

The following diagram illustrates the execution flow to apply the proposed method for continual learning experiment shown in the report:

![Execution Flow](codeflow.png)

## Jupyter Notebook Execution Stream

To reproduce the experiments and results, run the Jupyter notebooks in the following order:

### Without Any Continual Learning Method
1. `MNIST_0&1_vgg16.ipynb`: Training on task A.
2. `CL_MNIST_0&1_2&3.ipynb`: Continual training on task B with pre-trained model from task A.
3. `CL_MNIST_0&1_2&3_4&5.ipynb`: Continual training on task C with pre-trained model from task A and B.

### Applying Only Dynamic Learning Rate
1. `MNIST_0&1_vgg16.ipynb`: Training on task A.
2. `freezing_value_MNIST_0&1.ipynb`: Calculate freezing value for each weight to determain the individual learning rate for each weight.
3. `MAG_MNIST_0&1_2&3_0%.ipynb`: Training on task B with pre-trained model and individual learning rate set from task A.
4. `freezing_value_MNIST_0&1_2&3.ipynb`: Calculate freezing value for each weight to determain the individual learning rate for each weight.
5. `MAG_MNIST_0&1_2&3_4&5_0%.ipynb`: Training on task C with pre-trained model and individual learning rate set from task A and B.

### Applying Both Dynamic Learning Rate And Weight Pruning
1. `MNIST_0&1_vgg16.ipynb`: Training on task A.
2. `freezing_value_MNIST_0&1.ipynb`: Calculate freezing value for each weight to determain the individual learning rate for each weight.
3. `MAG_MNIST_0&1_2&3_?%.ipynb`: Training on task B with pre-trained model and individual learning rate set with different percentage weight pruning from task A.
4. `freezing_value_progress_MNIST_0&1_2&3.ipynb`: Update the freezing value progress.
5. `freezing_value_MNIST_0&1_2&3.ipynb`: Calculate freezing value for each weight to determain the individual learning rate for each weight.
6. `MAG_MNIST_0&1_2&3_4&5_?%.ipynb`: Training on task C with pre-trained model and individual learning rate set with different percentage weight pruning from task A and B.
