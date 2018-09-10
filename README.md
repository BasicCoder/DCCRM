# DCCM

## Model Configuration
- Optimizer
   - Adam
   
## DataSet
- Sketchy
- Flickr15K
- Flickr30K-Sketchy Overlapped
- MSCOCO-Sketchy Overlapped

## Model Parameters
| Model branch | Loss Function     | clip_grad_norm(max_norm) | weight_decay | Margin | lr          |
| ------------ | ----------------- | :----------------------: | :----------: | :----: | ----------- |
| ResNet18     | MarginRankingLoss | 100.0                    | 0.0005       | 15     | 2e-4 - 2e-7 |

| epoch | 1 - 90 | 90 - 170 | 170 - 300 | 300 -   |
| ----- | ------ | -------- | --------- | ------- |
| lr    | 2e-4   | 2e-5     | 2e-5      | 2e-6    |
| alpha | 1      | 1        | 1         | 1       |
| beta  | 1      | 1        | 5         | 15      |
| top1  |        | 0.16126  | 0.17670   | 0.20501 |


### Result

#### Branch Classfication
<table>
  <tr>
    <th>Model branch</th>
    <th>Sketch Prec@1</th>
    <th>Image Prec@1</th>
  </tr>
  <tr>
    <td>Resnet18</td>
    <td>89.4096</td>
    <td>92.2129</td>
  </tr>
  <tr>
    <td>AlexNet</td>
    <td>81.4810</td>
    <td>78.0830</td>
  </tr>
</table>

#### Origin
| Model Type | Prec@1 |
| ---------- | ------ |
| GoogleNet  | 37.10% |

#### Stage fc
<table>
  <tr>
    <th>Model branch</th>
    <th>Model Type</th>
    <th>Prec@1</th>
    <th>Prec@5</th>
    <th>Prec@10</th>
  </tr>
  <tr>
    <td rowspan="2">Resnet18</td>
    <td>one layer</td>
    <td>0.13974</td>
    <td>0.42277</td>
    <td>0.57865</td>
  </tr>
  <tr>
    <td>two layers</td>
    <td>0.13889</td>
    <td>0.39785</td>
    <td>0.54920</td>
  </tr>
  <tr>
    <td>AlexNet</td>
    <td>one layer</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
</table>

#### Stage all
<table>
  <tr>
    <th>Model branch</th>
    <th>Model Type</th>
    <th>Prec@1</th>
    <th>Prec@5</th>
    <th>Prec@10</th>
  </tr>
  <tr>
    <td rowspan="2">Resnet18</td>
    <td>one layer</td>
    <td>0.20133</td>
    <td>0.51635</td>
    <td>0.64802</td>
  </tr>
  <tr>
    <td>two layers</td>
    <td>0.19892</td>
    <td>0.49327</td>
    <td>0.61645</td>
  </tr>
  <tr>
    <td>AlexNet</td>
    <td>one layer</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
</table>


#### 1250
<table>
  <tr>
    <th>Model branch</th>
    <th>Model Type</th>
    <th>Prec@1</th>
    <th>Prec@5</th>
    <th>Prec@10</th>
  </tr>
  <tr>
    <td rowspan="3">Resnet18</td>
    <td>zero layer</td>
    <td>0.20240</td>
    <td>0.50000</td>
    <td>0.64640</td>
  </tr>
  <tr>
    <td>one layer</td>
    <td>0.22400</td>
    <td>0.53760</td>
    <td>0.66320</td>
  </tr>
  <tr>
    <td>two layers</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>AlexNet</td>
    <td>one layer</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
</table>


#### Result on Flickr8K-Sketchy Overlapped
| Evaluation Model | Prec@1 | Prec@5 | Prec@10 |
| ---------------- | ------ | ------ | ------- |
| GoogLeNet        |        |        |         |

#### Result on Flickr15K
| Evaluation Model | Prec@1  | Prec@5 | Prec@10 |
| ---------------- | ------- | ------ | ------- |
| GoogLeNet        | 0.33333 |        |         |
| DMEM(S+I)        | 0.69697 |        |         |


#### Result on Flickr30K-Sketchy Overlapped
| Evaluation Model | Recall@1<br>(0.01384)    | Recall@5<br>(0.06921)    | Recall@10<br>(0.13841)   | Precision@1 | Precision@5 | Precision@10 |
| ---------------- | :----------------------: | :----------------------: | :----------------------: | ----------- | ----------- | ------------ |
| GoogLeNet        | 0.01014    (**0.73266**) | 0.04569    (**0.66016**) | 0.08469    (**0.61188**) | 0.78685     | 0.71791     | 0.67574      |
| DMEM(S+I)        | 0.01193    (**0.86199**) | 0.05180    (**0.74845**) | 0.09779    (**0.70652**) | 0.89569     | 0.81406     | 0.77279      |
| DCCRM(S+I)       | 0.01206    (**0.87200**) | 0.05198    (**0.75105**) | 0.09783    (**0.70681**) | 0.89569     | 0.81897     | 0.78012      |
| DMEM(S+I+D)      | 0.01286    (**0.92919**) | 0.05594    (**0.80826**) | 0.10841    (**0.78325**) | 0.94785     | 0.86984     | 0.85306      |
| DCCRM(S+I+D)     | 0.01287    (**0.93005**) | 0.05620    (**0.81214**) | 0.11087    (**0.80106**) | 0.94897     | 0.87534     | 0.86765      |


#### Result on MSCOCO-Sketchy Overlapped
| Evaluation Model | Recall@1<br>(0.00864)    | Recall@5<br>(0.04321)    | Recall@10<br>(0.08643)   | Precision@1 | Precision@5 | Precision@10 |
| ---------------- | :----------------------: | :----------------------: | :----------------------: | ----------- | ----------- | ------------ |
| GoogLeNet        | 0.00511    (**0.59143**) | 0.02371    (**0.54872**) | 0.04259    (**0.49277**) | 0.62211     | 0.59152     | 0.55384      |
| DMEM(S+I)        | 0.00510    (**0.59028**) | 0.02356    (**0.54524**) | 0.04609    (**0.53326**) | 0.65271     | 0.62115     | 0.61583      |
| DCCRM(S+I)       | 0.00510    (**0.59028**) | 0.02373    (**0.54921**) | 0.04712    (**0.54517**) | 0.65583     | 0.63017     | 0.62759      |
| DMEM(S+I+D)      | 0.00581    (**0.67245**) | 0.02778    (**0.64291**) | 0.05302    (**0.61344**) | 0.74503     | 0.70488     | 0.68712      |
| DCCRM(S+I+D)     | 0.00581    (**0.67300**) | 0.02818    (**0.65214**) | 0.05442    (**0.62967**) | 0.75301     | 0.71519     | 0.69773      |