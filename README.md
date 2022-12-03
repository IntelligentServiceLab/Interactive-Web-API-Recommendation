# LNGCF
This is the comprehensive introduction for our method:

>Jiayan Xiang, Wanjun Chen, Bowen Liang, Zihao Liu, Guosheng Kang*. Interactive Web API Recommendation for Mashup Development based on Light Neural Graph Collaborative Filtering.

## Introduction
To improve both the optimality and scalability of Web API recommendation, we propose a Light Neural Graph Collaborative Filtering based Web API recommendation approach, named LNGCF. Specifically, LNGCF learns user and item embeddings by linearly propagating them on the user-item interaction graph, and uses the weighted summation of the embeddings learned at all layers as the final embedding. Such simple, linear, and neat model is much easier to implement and train. 


## Environment Requirement
The code has been tested running under Python 3.6.5. The required packages are as follows:
* tensorflow == 2.10.0
* numpy == 1.22.4
* scipy == 1.9.1
* sklearn == 1.1.2
* cython == 0.29.32

## Examples to run a 5-layer LNGCF
The instruction of commands has been clearly stated in the codes (see the parser function in LNGCF/utility/parser.py).

### Programmable-web
* Command
```
python LNGCF.py --dataset programmable-web --regs [1e-2] --embed_size 256 --layer_size [256,256,256,256,256] --lr 0.01 --batch_size 1024 --epoch 500
```
* Output log :
```
eval_score_matrix_foldout with python
n_users=2906, n_items=1255
n_interactions=9807
n_train=6497, n_test=3310, sparsity=0.00269
    ...
Epoch 1 [6.9s]: train==[0.60688=0.60465 + 0.00224]
Epoch 2 [4.0s]: train==[0.26251=0.24448 + 0.01803]
    ...
Epoch 200 [5.6s + 1.1s]: test==[0.49889=0.44503 + 0.05386 + 0.00000], recall=[0.46364], precision=[0.05213], ndcg=[0.32193]
Early stopping is trigger at step: 5 log:0.46364137530326843
Best Iter=[4]@[871.9]	recall=[0.46615], precision=[0.05224], ndcg=[0.33127]
```

NOTE : the duration of training and testing depends on the running environment.
## Dataset
We provide a processed real-world datasets: PW dataset.
* `train.txt`
  * Train file.
  * Each line is a user with her/his positive interactions with items: userID\t a list of itemID\n.

* `test.txt`
  * Test file (positive instances).
  * Each line is a user with her/his positive interactions with items: userID\t a list of itemID\n.
  * Note that here we treat all unobserved interactions as the negative instances when reporting performance.
  
* `user_list.txt`
  * User file.
  * Each line is a triplet (org_id, remap_id) for one user, where org_id and remap_id represent the ID of the user in the original and our datasets, respectively.
  
* `item_list.txt`
  * Item file.
  * Each line is a triplet (org_id, remap_id) for one item, where org_id and remap_id represent the ID of the item in the original and our datasets, respectively.



=======
