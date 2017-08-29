# Focal-Loss
loss layer of implementation.  
You can see "Focal Loss for Dense Object Detection" [arXiv](https://arxiv.org/abs/1708.02002) for more information.  

## Usage

```
// Focal Loss layer
optional FocalLossParameter focal_loss_param = 124;

message FocalLossParameter {
  optional float gamma = 1 [default = 2];
  optional float alpha = 2 [default = 0.25]; 
}

layer {
  name: "loss"
  type: "SoftmaxFocalLoss"
  bottom: "deconv"
  bottom: "labels"
  loss_param { ignore_label: -1 normalize: true }
  focal_loss_param { alpha: 0.25 gamma: 2 }
}
```

### Derivative
see https://github.com/zimenglan-sysu-512/paper-note/blob/master/focal_loss.pdf

### Done
All categories share the same `alpha`.

### Sigmoid Form
Here use `softmax` instead of `sigmoid` function.  
If you want see how to use `sigmoid` to implement `Focal Loss`, please see https://github.com/sciencefans/Focal-Loss to get more information.  

### MXNet Repo
https://github.com/unsky/focal-loss
