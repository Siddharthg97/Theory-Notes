**LLM model theory**

### 1) Model evaluate

model.eval() is a kind of switch for some specific layers/parts of the model that behave differently during training and inference (evaluating) time. For example, 
Dropouts Layers, BatchNorm Layers etc. You need to turn them off during model evaluation, and .eval() will do it for you.
In addition, the common practice for evaluating/validation is using torch.no_grad() in pair with model.eval() to turn off gradients computation:

#### evaluate model:
model.eval()

with torch.no_grad():
    ...
    out_data = model(data)

  BUT, don't forget to turn back to training mode after eval step:

# training step
...
model.train()
...
