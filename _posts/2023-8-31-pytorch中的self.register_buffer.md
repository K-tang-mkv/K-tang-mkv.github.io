在PyTorch中,self.register_buffer()是一个用于注册buffer的方法,它通常用于注册不需要求梯度的tensors。
```python3
class Test(nn.Module):
  def __init__(self):
    pe = torch.rand((3,4))
    self.register_buffer('pe', pe)
```

self.register_buffer的作用主要有:

1. 把pe注册为buffer,可以避免pe参与参数优化。

2. pe会作为模块的状态保存,register_buffer()会把pe附加到self._buffers字典上。

3. 模型保存时可以序列化buffer,register_buffer()方便保存和加载整个模型。

4. 在forward方法中可以直接通过self.pe访问register的buffer。

5. register_buffer()会给pe加上_buffers后缀,方便与参数区分开。

6. buffer通常不需要梯度,但我们仍然可以对buffer调用.requires_grad_()来获得梯度。

7. buffer会随模块一起移动到GPU上,register_buffer()会自动处理DEVICE。

所以注册pe为buffer的好处是pe不需要优化,可以随模块一起保存和加载,forward时直接访问,也可以方便地放到GPU上,而无需手动处理。

总之,register_buffer为我们提供了一个注册tensor的简单方法,使其成为模块状态的一部分,并自动处理与优化、保存相关的问题。
