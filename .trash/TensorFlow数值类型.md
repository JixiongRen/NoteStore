* Scalar（标量）Dimension=0，shape=[]
* Vector (向量)  n 个实数的有序集合，如 $[1.2], [1.2, 3.4]$ 等，Dimension=1，shape=[n]
* Matrix (矩阵)  n 行 m 列实数的有序集合，如  $[[1, 2], [3, 4]]$，Dimension=2，每一维度上长度不定，shape=[n, m]
* **Tensor (张量)**  dim>2 的数组，shape=[a, b, c, d]

***

# 标量的创建

```Python
a = 1.2
aa = tf.constant(1.2)  # 创建标量
print(type(aa))
print(tf.is_tensor(aa))
```

结果

```
<class 'tensorflow.python.framework.ops.EagerTensor'>
True
```

# 向量的创建

```Python
x = tf.constant([1, 2., 3.3])  
print(x)
```

结果

```
tf.Tensor([1.  2.  3.3], shape=(3,), dtype=float32)
```

# 多维张量的创建

```Python
# 多维张量的创建  
c = tf.constant([[[1., 2., 3.], [4., 5., 6.], [7., 8., 9.]]])  
print(c.shape)  
print(c)
```

结果

```
(1, 3, 3)
tf.Tensor(
[[[1. 2. 3.]
  [4. 5. 6.]
  [7. 8. 9.]]], shape=(1, 3, 3), dtype=float32)
```

# 数值精度

>一般对于大部分深度学习算法，一般使用 tf. int32、tf. float32 可满足运算精度要求，对于强化学习，一般使用 tf. int64、tf. float64

## 访问张量的 dtype 成员属性判断张量精度

```Python
c = tf.constant([[[1., 2., 3.], [4., 5., 6.], [7., 8., 9.]]])  
print(c.dtype)
```

结果

```
<dtype: 'float32'>
```

## 使用 `tf. cast ()` 函数进行张量类型的转换

>布尔型与整形之间的相互转换比较常见




