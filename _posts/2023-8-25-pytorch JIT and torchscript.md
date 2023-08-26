# Pytorch JIT and TorchScript
Pytorch supports two seperate modes to handle the whole reasearch and production.

First is the Eager mode. It is built for faster prototyping, training, and experimentation.

Second is the Script mode. It is focused on the production use case. It has 2 components PyTorch JIT and TorchScript.

### Script Mode
Script mode creates an intermediate representation (IR) of your PyTorch Eager module(throughtorch.jit.trace/torch.jit.script). The IR is internally optimized and utilizes PyTorch JIT compilation at runtime. PyTorch JIT compiler uses runtime information to optimize the IR. This IR is decoupled from the Python runtime.

The script mode works by utilizing PyTorch JIT and TorchScript.

### What is PyTorch JIT?
PyTorch JIT is an optimized compiler for PyTorch programs.

It is a lightweight threadsafe interpreter
Supports easy to write custom transformations
It’s not just for inference as it has auto diff support

### What is TorchScript?

TorchScript is a static high-performance subset of Python language, specialized for ML applications. It supports

1. Complex control flows
2. Common data structures
3. User-defined classes

Script mode is invoked by either torch.jit.trace or torch.jit.script.

### JIT Trace
torch.jit.trace take a data instance and your trained eager module as input. The tracer runs the supplied module and records the tensor operations performed. This recording is turned into a TorchScript module.

jit.trace way doesn't support any control flow like if else and loop. If there is any control flow in the module, the jit.trace way will ignore the control flow and treat the vlaue as constant.

### JIT Script
torch.jit.script allows you to write your code directly into TorchScript. It's more verbose but it more versatile and with a little tweaking can support the majority of the PyTorch models.

In contrast to trace mode you only need to pass an instance of your model/module to torch.jit.script. A data sample is not necessary.
