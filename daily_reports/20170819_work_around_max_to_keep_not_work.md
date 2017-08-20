#### 解决saver函数的max_to_keep参数无效的方法（Tensorflow）
#### issue链接：https://github.com/tensorflow/tensorflow/issues/5929
 
因为checkpoint文件太大可能会造成系统崩溃，所以提供了一个临时方案，如下：

```python
def rm_old_ckpfiles(log_dir):
    last_chk_path = tf.train.latest_checkpoint(checkpoint_dir=log_dir)

    last_chk = last_chk_path.split('/')[-1]
    old_chk_list = [f for f in os.listdir(log_dir) \
                if f.startswith('model.ckpt') and not f.startswith(last_chk)]

    for f in old_chk_list:
        os.remove(os.path.join(log_dir, f))
```
