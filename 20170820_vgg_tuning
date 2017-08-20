### 调试日志0820

昨晚的运行结果看起来是过拟合，test accuracy在67%～68%上下波动，但是train accuracy还在一路提高，冲到了98%以上。
过拟合的原因仔细考虑了一下，可能是因为数据集较小，但是模型过于复杂，所以产生过拟合，

可以尝试的解决办法：
1.数据增强
2.缩小模型
3.使用其他正则化方法

另外今天想做的，还有：
1.安装deep visualization toolbox
2.多gpu实现


batch size是50，cifar数据集是50000，所以1000次是完整的一轮

step 8500, training accuracy 0.8573
step 8500, test accuracy 0.6426

step 9500, training accuracy 0.92254
step 9500, test accuracy 0.6503

step 10500, training accuracy 0.94986
step 10500, test accuracy 0.6654

step 11500, training accuracy 0.964
step 11500, test accuracy 0.6626

step 12500, training accuracy 0.96776
step 12500, test accuracy 0.6817

step 13500, training accuracy 0.96864
step 13500, test accuracy 0.6604

step 14500, training accuracy 0.98308
step 14500, test accuracy 0.6784

step 15500, training accuracy 0.98346
step 15500, test accuracy 0.6783

step 16500, training accuracy 0.98476
step 16500, test accuracy 0.6764
