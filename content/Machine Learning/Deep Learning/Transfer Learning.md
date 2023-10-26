**Transfer Learning** and domain adaptation refer to the situation where what has been learned in one setting... is expoilted to improve generalization in another setting.
Is the improvement of learning a new task through thew transfer of knowledge from a related task that has already been learned.

>> Learning a new task relies on the previous learned task

Terminology:
- **source domain** the previous learned task
- **target domain** the new task

### Transductive Transfer Learning
Refers to the situations where the label information only comes from the source domain, it the task is the same but the domain are different (still related e.g image/audio of animals) it's called _domain adaptation_


### Inductive Transfer Learning
We can have source and target label, in this case it's called _multi-task learning_, or just the target labels _self-taught learning_.


### Unsupervised transfer Learning
No labels on both source and target, clustering and dimensionality reduction.