
`torch.from_numpy( )` vs. `torch.Tensor( )`.

`torch.from_numpy( )` inherits its input's `dtype`; it also shares the same memory with its input array. Modifications to the tensor will be reflected in the ndarray and vice versa.

```python
import numpy as np
import torch
a = np.arange(3)
a_tensor_1 = torch.Tensor(a)      # does NOT share memory
a_tensor_2 = torch.from_numpy(a)  # does share memory on CPU
a_tensor_1_cuda = torch.Tensor(a).to("cuda")
a_tensor_2_cuda = torch.from_numpy(a).to("cuda")
a_tensor_1_CPU = torch.Tensor(a).to("cpu")
a_tensor_2_CPU = torch.from_numpy(a).to("cpu")
a, a.dtype, hex(id(a)) # get the value, data type and memmry address
# (array([0, 1, 2]), dtype('int64'), '0x7f25dbb11f30')
a_tensor_1, a_tensor_1.dtype, hex(id(a_tensor_1))
(tensor([0., 1., 2.]), torch.float32, '0x7f25db8c30e0')
a_tensor_2, a_tensor_2.dtype, hex(id(a_tensor_2))
# (tensor([0, 1, 2]), torch.int64, '0x7f25db8c3bd0')
a_tensor_1_cuda, a_tensor_1_cuda.dtype, hex(id(a_tensor_1_cuda))
# (tensor([0., 1., 2.], device='cuda:0'), torch.float32, '0x7f25f3775220')
a_tensor_2_cuda, a_tensor_2_cuda.dtype, hex(id(a_tensor_2_cuda))
# (tensor([0, 1, 2], device='cuda:0'), torch.int64, '0x7f2577f83ae0')
a_tensor_1_CPU, a_tensor_1_CPU.dtype, hex(id(a_tensor_1_CPU))
# (tensor([0., 1., 2.]), torch.float32, '0x7f25db8c3f90')
a_tensor_2_CPU, a_tensor_2_CPU.dtype, hex(id(a_tensor_2_CPU))
# (tensor([0, 1, 2]), torch.int64, '0x7f25db8b7d10')
>>> a *= 3 # change the variable's value
a, a.dtype, hex(id(a))
# (array([0, 3, 6]), dtype('int64'), '0x7f25dbb11f30') # the same memory address 
a_tensor_1, a_tensor_1.dtype, hex(id(a_tensor_1_CPU))
# (tensor([0., 1., 2.]), torch.float32, '0x7f25db8c3f90')
a_tensor_2, a_tensor_2.dtype, hex(id(a_tensor_2_CPU))
# (tensor([0, 3, 6]), torch.int64, ' ') # does share memory with a on CPU
a_tensor_1_cuda, a_tensor_1_cuda.dtype
# (tensor([0., 1., 2.], device='cuda:0'), torch.float32)
a_tensor_2_cuda, a_tensor_2_cuda.dtype
# (tensor([0, 1, 2], device='cuda:0'), torch.int64) # does NOT share memory with a on GPU
a_tensor_1_CPU, a_tensor_1_CPU.dtype
# (tensor([0., 1., 2.]), torch.float32)
a_tensor_2_CPU, a_tensor_2_CPU.dtype
# (tensor([0, 3, 6]), torch.int64)
a = a * 3 # change the variable's value
hex(id(a))
# '0x7f2577f7d990' # same memory address
a
# array([0, 9, 18])
a_tensor_2_CPU, a_tensor_2_CPU.dtype
# (tensor([0, 3, 6]), torch.int64) # the memory address is different now



```
