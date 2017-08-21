对原有的过拟合问题进行了两个改进
- 简化模型，对原来resized为224的图像恢复为32，相对应的网络模型大大简化
- 增加了dropout正则化方法，
经过改进，测试精度提高了8%，从67%到75%左右

接下来准备做的改进：
- 增加l2正则化，设置λ为0.01，当前学习率为0.0001
- 数据增强

思考一下过拟合问题出现的原因和处理方案：
- 数据集自身的问题，局部特征或者噪声过多，相对于希望获得的模型能力，数据集的泛化性不够
- 模型的设计与数据集不匹配（一般来说是过于复杂，再比如一个错误的模型），导致模型更多地学到了局部特征或者噪声带来的假特征

解决方案：
- 数据增强（增加数据集，去除噪声）
- 使用正则化方法限制模型的规模

另外，欠拟合一般是模型设计的过于简单的缘故

以下是训练结果的打印：

current step:500, example per seconds:290.951308, seconds per batch50:0.171850
Exception when remove old chk files: 'NoneType' object has no attribute 'split'
Saved checkpoint 500 steps.
current step:1000, example per seconds:293.956158, seconds per batch50:0.170093
Saved checkpoint 1000 steps.


step 1000, training accuracy 0.3528
step 1000, test accuracy 0.3596
current step:1500, example per seconds:198.310334, seconds per batch50:0.252130
Saved checkpoint 1500 steps.
current step:2000, example per seconds:293.211561, seconds per batch50:0.170525
Saved checkpoint 2000 steps.
step 2000, training accuracy 0.47656
step 2000, test accuracy 0.4757
current step:2500, example per seconds:198.628283, seconds per batch50:0.251726
Saved checkpoint 2500 steps.
current step:3000, example per seconds:293.621508, seconds per batch50:0.170287
Saved checkpoint 3000 steps.
step 3000, training accuracy 0.57654
step 3000, test accuracy 0.5611
current step:3500, example per seconds:197.696140, seconds per batch50:0.252913
Saved checkpoint 3500 steps.
current step:4000, example per seconds:281.766504, seconds per batch50:0.177452
Saved checkpoint 4000 steps.
step 4000, training accuracy 0.63916
step 4000, test accuracy 0.6042
current step:4500, example per seconds:196.952439, seconds per batch50:0.253868
Saved checkpoint 4500 steps.
current step:5000, example per seconds:291.914248, seconds per batch50:0.171283
Saved checkpoint 5000 steps.
step 5000, training accuracy 0.69304
step 5000, test accuracy 0.6378
current step:5500, example per seconds:196.401816, seconds per batch50:0.254580
Saved checkpoint 5500 steps.
current step:6000, example per seconds:294.672841, seconds per batch50:0.169680
Saved checkpoint 6000 steps.
step 6000, training accuracy 0.74618
step 6000, test accuracy 0.6701
current step:6500, example per seconds:198.456159, seconds per batch50:0.251945
Saved checkpoint 6500 steps.
current step:7000, example per seconds:283.470925, seconds per batch50:0.176385
Saved checkpoint 7000 steps.
step 7000, training accuracy 0.794
step 7000, test accuracy 0.6896
current step:7500, example per seconds:197.777285, seconds per batch50:0.252810
Saved checkpoint 7500 steps.
current step:8000, example per seconds:283.170211, seconds per batch50:0.176572
Saved checkpoint 8000 steps.
step 8000, training accuracy 0.8382
step 8000, test accuracy 0.701
current step:8500, example per seconds:196.990696, seconds per batch50:0.253819
Saved checkpoint 8500 steps.
current step:9000, example per seconds:291.408819, seconds per batch50:0.171580
Saved checkpoint 9000 steps.
step 9000, training accuracy 0.86524
step 9000, test accuracy 0.7083
current step:9500, example per seconds:197.236798, seconds per batch50:0.253502
Saved checkpoint 9500 steps.
current step:10000, example per seconds:293.581792, seconds per batch50:0.170310
Saved checkpoint 10000 steps.
step 10000, training accuracy 0.90374
step 10000, test accuracy 0.7036
current step:10500, example per seconds:198.785675, seconds per batch50:0.251527
Saved checkpoint 10500 steps.
current step:11000, example per seconds:291.930477, seconds per batch50:0.171274
Saved checkpoint 11000 steps.
step 11000, training accuracy 0.91148
step 11000, test accuracy 0.6917
current step:11500, example per seconds:196.786348, seconds per batch50:0.254083
Saved checkpoint 11500 steps.
current step:12000, example per seconds:292.568357, seconds per batch50:0.170900
Saved checkpoint 12000 steps.
step 12000, training accuracy 0.94352
step 12000, test accuracy 0.7086
current step:12500, example per seconds:198.118702, seconds per batch50:0.252374
Saved checkpoint 12500 steps.
current step:13000, example per seconds:291.033606, seconds per batch50:0.171801
Saved checkpoint 13000 steps.
step 13000, training accuracy 0.95754
step 13000, test accuracy 0.7169
current step:13500, example per seconds:195.872055, seconds per batch50:0.255269
Saved checkpoint 13500 steps.
current step:14000, example per seconds:291.642640, seconds per batch50:0.171443
Saved checkpoint 14000 steps.
step 14000, training accuracy 0.97012
step 14000, test accuracy 0.7305
current step:14500, example per seconds:196.200142, seconds per batch50:0.254842
Saved checkpoint 14500 steps.
current step:15000, example per seconds:292.149725, seconds per batch50:0.171145
Saved checkpoint 15000 steps.
step 15000, training accuracy 0.97254
step 15000, test accuracy 0.7195
current step:15500, example per seconds:198.875384, seconds per batch50:0.251414
Saved checkpoint 15500 steps.
current step:16000, example per seconds:291.886870, seconds per batch50:0.171299
Saved checkpoint 16000 steps.
step 16000, training accuracy 0.97842
step 16000, test accuracy 0.7221
current step:16500, example per seconds:197.022696, seconds per batch50:0.253778
Saved checkpoint 16500 steps.
current step:17000, example per seconds:285.976197, seconds per batch50:0.174840
Saved checkpoint 17000 steps.
step 17000, training accuracy 0.97426
step 17000, test accuracy 0.7123
current step:17500, example per seconds:198.229010, seconds per batch50:0.252234
Saved checkpoint 17500 steps.
current step:18000, example per seconds:293.235829, seconds per batch50:0.170511
Saved checkpoint 18000 steps.
step 18000, training accuracy 0.98182
step 18000, test accuracy 0.7242
current step:18500, example per seconds:197.983758, seconds per batch50:0.252546
Saved checkpoint 18500 steps.
current step:19000, example per seconds:290.893078, seconds per batch50:0.171884
Saved checkpoint 19000 steps.
step 19000, training accuracy 0.97922
step 19000, test accuracy 0.7168
current step:19500, example per seconds:197.740840, seconds per batch50:0.252856
Saved checkpoint 19500 steps.
current step:20000, example per seconds:293.001521, seconds per batch50:0.170648
Saved checkpoint 20000 steps.
step 20000, training accuracy 0.9694
step 20000, test accuracy 0.7188
current step:20500, example per seconds:198.452388, seconds per batch50:0.251950
Saved checkpoint 20500 steps.
current step:21000, example per seconds:294.259805, seconds per batch50:0.169918
Saved checkpoint 21000 steps.
step 21000, training accuracy 0.99122
step 21000, test accuracy 0.7341
current step:21500, example per seconds:197.361745, seconds per batch50:0.253342
Saved checkpoint 21500 steps.
current step:22000, example per seconds:294.727850, seconds per batch50:0.169648
Saved checkpoint 22000 steps.
step 22000, training accuracy 0.98264
step 22000, test accuracy 0.7271
current step:22500, example per seconds:196.650706, seconds per batch50:0.254258
Saved checkpoint 22500 steps.
current step:23000, example per seconds:292.910643, seconds per batch50:0.170701
Saved checkpoint 23000 steps.
step 23000, training accuracy 0.98882
step 23000, test accuracy 0.7306
current step:23500, example per seconds:195.838746, seconds per batch50:0.255312
Saved checkpoint 23500 steps.
current step:24000, example per seconds:293.894053, seconds per batch50:0.170129
Saved checkpoint 24000 steps.
step 24000, training accuracy 0.98584
step 24000, test accuracy 0.7335
current step:24500, example per seconds:198.129661, seconds per batch50:0.252360
Saved checkpoint 24500 steps.
current step:25000, example per seconds:295.551684, seconds per batch50:0.169175
Saved checkpoint 25000 steps.
step 25000, training accuracy 0.97882
step 25000, test accuracy 0.7224
current step:25500, example per seconds:197.282294, seconds per batch50:0.253444
Saved checkpoint 25500 steps.
current step:26000, example per seconds:289.747997, seconds per batch50:0.172564
Saved checkpoint 26000 steps.
step 26000, training accuracy 0.9893
step 26000, test accuracy 0.7331
current step:26500, example per seconds:198.053052, seconds per batch50:0.252458
Saved checkpoint 26500 steps.
current step:27000, example per seconds:295.174345, seconds per batch50:0.169391
Saved checkpoint 27000 steps.
step 27000, training accuracy 0.9887
step 27000, test accuracy 0.7325
current step:27500, example per seconds:196.421448, seconds per batch50:0.254555
Saved checkpoint 27500 steps.
current step:28000, example per seconds:291.720963, seconds per batch50:0.171397
Saved checkpoint 28000 steps.
step 28000, training accuracy 0.9903
step 28000, test accuracy 0.7354
current step:28500, example per seconds:197.186238, seconds per batch50:0.253567
Saved checkpoint 28500 steps.
current step:29000, example per seconds:290.802541, seconds per batch50:0.171938
Saved checkpoint 29000 steps.
step 29000, training accuracy 0.98974
step 29000, test accuracy 0.7242
current step:29500, example per seconds:197.363013, seconds per batch50:0.253340
Saved checkpoint 29500 steps.
current step:30000, example per seconds:290.373811, seconds per batch50:0.172192
Saved checkpoint 30000 steps.
step 30000, training accuracy 0.98578
step 30000, test accuracy 0.7261
current step:30500, example per seconds:197.554254, seconds per batch50:0.253095
Saved checkpoint 30500 steps.
current step:31000, example per seconds:291.855072, seconds per batch50:0.171318
Saved checkpoint 31000 steps.
step 31000, training accuracy 0.9872
step 31000, test accuracy 0.7284
current step:31500, example per seconds:197.543729, seconds per batch50:0.253109
Saved checkpoint 31500 steps.
current step:32000, example per seconds:292.803784, seconds per batch50:0.170763
Saved checkpoint 32000 steps.
step 32000, training accuracy 0.99328
step 32000, test accuracy 0.7354
current step:32500, example per seconds:197.786356, seconds per batch50:0.252798
Saved checkpoint 32500 steps.
current step:33000, example per seconds:292.663587, seconds per batch50:0.170845
Saved checkpoint 33000 steps.
step 33000, training accuracy 0.98478
step 33000, test accuracy 0.7284
current step:33500, example per seconds:197.332858, seconds per batch50:0.253379
Saved checkpoint 33500 steps.
current step:34000, example per seconds:293.687416, seconds per batch50:0.170249
Saved checkpoint 34000 steps.
step 34000, training accuracy 0.98626
step 34000, test accuracy 0.7297
current step:34500, example per seconds:197.698059, seconds per batch50:0.252911
Saved checkpoint 34500 steps.
current step:35000, example per seconds:290.348123, seconds per batch50:0.172207
Saved checkpoint 35000 steps.
step 35000, training accuracy 0.98712
step 35000, test accuracy 0.7295
current step:35500, example per seconds:197.561263, seconds per batch50:0.253086
Saved checkpoint 35500 steps.
current step:36000, example per seconds:291.994615, seconds per batch50:0.171236
Saved checkpoint 36000 steps.
step 36000, training accuracy 0.99172
step 36000, test accuracy 0.7331
current step:36500, example per seconds:197.547597, seconds per batch50:0.253104
Saved checkpoint 36500 steps.
current step:37000, example per seconds:290.962975, seconds per batch50:0.171843
Saved checkpoint 37000 steps.
step 37000, training accuracy 0.991
step 37000, test accuracy 0.7322
current step:37500, example per seconds:198.382943, seconds per batch50:0.252038
Saved checkpoint 37500 steps.
current step:38000, example per seconds:287.155090, seconds per batch50:0.174122
Saved checkpoint 38000 steps.
step 38000, training accuracy 0.98426
step 38000, test accuracy 0.7221
current step:38500, example per seconds:197.331208, seconds per batch50:0.253381
Saved checkpoint 38500 steps.
current step:39000, example per seconds:292.428882, seconds per batch50:0.170982
Saved checkpoint 39000 steps.
step 39000, training accuracy 0.9815
step 39000, test accuracy 0.7195
current step:39500, example per seconds:197.172709, seconds per batch50:0.253585
Saved checkpoint 39500 steps.
current step:40000, example per seconds:284.700680, seconds per batch50:0.175623
Saved checkpoint 40000 steps.
step 40000, training accuracy 0.98836
step 40000, test accuracy 0.7308
current step:40500, example per seconds:197.155466, seconds per batch50:0.253607
Saved checkpoint 40500 steps.
current step:41000, example per seconds:293.517349, seconds per batch50:0.170348
Saved checkpoint 41000 steps.
step 41000, training accuracy 0.99058
step 41000, test accuracy 0.7361
current step:41500, example per seconds:198.275860, seconds per batch50:0.252174
Saved checkpoint 41500 steps.
current step:42000, example per seconds:292.700073, seconds per batch50:0.170823
Saved checkpoint 42000 steps.
step 42000, training accuracy 0.98986
step 42000, test accuracy 0.7411
current step:42500, example per seconds:197.507494, seconds per batch50:0.253155
Saved checkpoint 42500 steps.
current step:43000, example per seconds:292.209161, seconds per batch50:0.171110
Saved checkpoint 43000 steps.
step 43000, training accuracy 0.98878
step 43000, test accuracy 0.7299
current step:43500, example per seconds:195.835575, seconds per batch50:0.255316
Saved checkpoint 43500 steps.
current step:44000, example per seconds:293.294847, seconds per batch50:0.170477
Saved checkpoint 44000 steps.
step 44000, training accuracy 0.98728
step 44000, test accuracy 0.7323
current step:44500, example per seconds:199.096064, seconds per batch50:0.251135
Saved checkpoint 44500 steps.
current step:45000, example per seconds:293.467034, seconds per batch50:0.170377
Saved checkpoint 45000 steps.
step 45000, training accuracy 0.98952
step 45000, test accuracy 0.7334
current step:45500, example per seconds:197.364726, seconds per batch50:0.253338
Saved checkpoint 45500 steps.
current step:46000, example per seconds:295.798010, seconds per batch50:0.169034
Saved checkpoint 46000 steps.
step 46000, training accuracy 0.99284
step 46000, test accuracy 0.7336
current step:46500, example per seconds:196.339988, seconds per batch50:0.254660
Saved checkpoint 46500 steps.
current step:47000, example per seconds:295.256940, seconds per batch50:0.169344
Saved checkpoint 47000 steps.
step 47000, training accuracy 0.99076
step 47000, test accuracy 0.7385
current step:47500, example per seconds:197.699663, seconds per batch50:0.252909
Saved checkpoint 47500 steps.
current step:48000, example per seconds:291.535928, seconds per batch50:0.171505
Saved checkpoint 48000 steps.
step 48000, training accuracy 0.98948
step 48000, test accuracy 0.7406
current step:48500, example per seconds:197.324536, seconds per batch50:0.253390
Saved checkpoint 48500 steps.
current step:49000, example per seconds:288.850552, seconds per batch50:0.173100
Saved checkpoint 49000 steps.
step 49000, training accuracy 0.99348
step 49000, test accuracy 0.7441
current step:49500, example per seconds:197.922197, seconds per batch50:0.252625
Saved checkpoint 49500 steps.
current step:50000, example per seconds:285.507616, seconds per batch50:0.175127
Saved checkpoint 50000 steps.
step 50000, training accuracy 0.99278
step 50000, test accuracy 0.7426
current step:50500, example per seconds:197.830049, seconds per batch50:0.252742
Saved checkpoint 50500 steps.
current step:51000, example per seconds:295.691303, seconds per batch50:0.169095
Saved checkpoint 51000 steps.
step 51000, training accuracy 0.9875
step 51000, test accuracy 0.7371
current step:51500, example per seconds:197.735763, seconds per batch50:0.252863
Saved checkpoint 51500 steps.
current step:52000, example per seconds:291.346213, seconds per batch50:0.171617
Saved checkpoint 52000 steps.
step 52000, training accuracy 0.9937
step 52000, test accuracy 0.7448
current step:52500, example per seconds:199.917874, seconds per batch50:0.250103
Saved checkpoint 52500 steps.
current step:53000, example per seconds:293.424002, seconds per batch50:0.170402
Saved checkpoint 53000 steps.
step 53000, training accuracy 0.99042
step 53000, test accuracy 0.7396
current step:53500, example per seconds:197.959170, seconds per batch50:0.252577
Saved checkpoint 53500 steps.
current step:54000, example per seconds:294.576662, seconds per batch50:0.169735
Saved checkpoint 54000 steps.
step 54000, training accuracy 0.993
step 54000, test accuracy 0.7404
current step:54500, example per seconds:197.030714, seconds per batch50:0.253768
Saved checkpoint 54500 steps.
current step:55000, example per seconds:292.711129, seconds per batch50:0.170817
Saved checkpoint 55000 steps.
step 55000, training accuracy 0.99548
step 55000, test accuracy 0.7416
current step:55500, example per seconds:195.359206, seconds per batch50:0.255939
Saved checkpoint 55500 steps.
current step:56000, example per seconds:293.619484, seconds per batch50:0.170288
Saved checkpoint 56000 steps.
step 56000, training accuracy 0.99262
step 56000, test accuracy 0.7418
current step:56500, example per seconds:197.317408, seconds per batch50:0.253399
Saved checkpoint 56500 steps.
current step:57000, example per seconds:294.023885, seconds per batch50:0.170054
Saved checkpoint 57000 steps.
step 57000, training accuracy 0.99346
step 57000, test accuracy 0.7427
current step:57500, example per seconds:196.903358, seconds per batch50:0.253932
Saved checkpoint 57500 steps.
current step:58000, example per seconds:295.707395, seconds per batch50:0.169086
Saved checkpoint 58000 steps.
step 58000, training accuracy 0.98964
step 58000, test accuracy 0.7407
current step:58500, example per seconds:198.354570, seconds per batch50:0.252074
Saved checkpoint 58500 steps.
current step:59000, example per seconds:291.908448, seconds per batch50:0.171287
Saved checkpoint 59000 steps.
step 59000, training accuracy 0.99132
step 59000, test accuracy 0.7448
current step:59500, example per seconds:197.308203, seconds per batch50:0.253411
Saved checkpoint 59500 steps.
current step:60000, example per seconds:296.876135, seconds per batch50:0.168420
Saved checkpoint 60000 steps.
step 60000, training accuracy 0.9943
step 60000, test accuracy 0.7376
current step:60500, example per seconds:198.234244, seconds per batch50:0.252227
Saved checkpoint 60500 steps.
current step:61000, example per seconds:291.460219, seconds per batch50:0.171550
Saved checkpoint 61000 steps.
step 61000, training accuracy 0.99114
step 61000, test accuracy 0.7299
current step:61500, example per seconds:197.827151, seconds per batch50:0.252746
Saved checkpoint 61500 steps.
current step:62000, example per seconds:294.238812, seconds per batch50:0.169930
Saved checkpoint 62000 steps.
step 62000, training accuracy 0.99452
step 62000, test accuracy 0.7419
current step:62500, example per seconds:198.810751, seconds per batch50:0.251495
Saved checkpoint 62500 steps.
current step:63000, example per seconds:294.514837, seconds per batch50:0.169771
Saved checkpoint 63000 steps.
step 63000, training accuracy 0.99374
step 63000, test accuracy 0.7405
current step:63500, example per seconds:197.400325, seconds per batch50:0.253292
Saved checkpoint 63500 steps.
current step:64000, example per seconds:294.507058, seconds per batch50:0.169775
Saved checkpoint 64000 steps.
step 64000, training accuracy 0.98694
step 64000, test accuracy 0.7343
current step:64500, example per seconds:197.009730, seconds per batch50:0.253795
Saved checkpoint 64500 steps.
current step:65000, example per seconds:296.230532, seconds per batch50:0.168787
Saved checkpoint 65000 steps.
step 65000, training accuracy 0.98648
step 65000, test accuracy 0.7376
current step:65500, example per seconds:198.587644, seconds per batch50:0.251778
Saved checkpoint 65500 steps.
current step:66000, example per seconds:294.219479, seconds per batch50:0.169941
Saved checkpoint 66000 steps.
step 66000, training accuracy 0.99488
step 66000, test accuracy 0.7516
current step:66500, example per seconds:197.198026, seconds per batch50:0.253552
Saved checkpoint 66500 steps.
current step:67000, example per seconds:293.387553, seconds per batch50:0.170423
Saved checkpoint 67000 steps.
step 67000, training accuracy 0.9852
step 67000, test accuracy 0.73
current step:67500, example per seconds:197.742577, seconds per batch50:0.252854
Saved checkpoint 67500 steps.
current step:68000, example per seconds:296.129960, seconds per batch50:0.168845
Saved checkpoint 68000 steps.
step 68000, training accuracy 0.99662
step 68000, test accuracy 0.7506
current step:68500, example per seconds:196.808640, seconds per batch50:0.254054
Saved checkpoint 68500 steps.
current step:69000, example per seconds:292.333128, seconds per batch50:0.171038
Saved checkpoint 69000 steps.
step 69000, training accuracy 0.99146
step 69000, test accuracy 0.7416
current step:69500, example per seconds:196.321516, seconds per batch50:0.254684
Saved checkpoint 69500 steps.
current step:70000, example per seconds:292.098107, seconds per batch50:0.171175
Saved checkpoint 70000 steps.
step 70000, training accuracy 0.98482
step 70000, test accuracy 0.7368
current step:70500, example per seconds:197.978963, seconds per batch50:0.252552
Saved checkpoint 70500 steps.
current step:71000, example per seconds:295.673321, seconds per batch50:0.169106
Saved checkpoint 71000 steps.
step 71000, training accuracy 0.99406
step 71000, test accuracy 0.7424
current step:71500, example per seconds:198.056313, seconds per batch50:0.252453
Saved checkpoint 71500 steps.
current step:72000, example per seconds:291.695004, seconds per batch50:0.171412
Saved checkpoint 72000 steps.
step 72000, training accuracy 0.9939
step 72000, test accuracy 0.7423
current step:72500, example per seconds:197.322331, seconds per batch50:0.253393
Saved checkpoint 72500 steps.
current step:73000, example per seconds:294.118569, seconds per batch50:0.169999
Saved checkpoint 73000 steps.
step 73000, training accuracy 0.99606
step 73000, test accuracy 0.7482
current step:73500, example per seconds:197.679052, seconds per batch50:0.252935
Saved checkpoint 73500 steps.
current step:74000, example per seconds:296.273854, seconds per batch50:0.168763
Saved checkpoint 74000 steps.
step 74000, training accuracy 0.99026
step 74000, test accuracy 0.7321
current step:74500, example per seconds:198.428274, seconds per batch50:0.251980
Saved checkpoint 74500 steps.
current step:75000, example per seconds:292.438264, seconds per batch50:0.170976
Saved checkpoint 75000 steps.
step 75000, training accuracy 0.99344
step 75000, test accuracy 0.7355
current step:75500, example per seconds:196.367384, seconds per batch50:0.254625
Saved checkpoint 75500 steps.
current step:76000, example per seconds:292.723505, seconds per batch50:0.170810
Saved checkpoint 76000 steps.
step 76000, training accuracy 0.99604
step 76000, test accuracy 0.7441
current step:76500, example per seconds:197.565382, seconds per batch50:0.253081
Saved checkpoint 76500 steps.
current step:77000, example per seconds:295.799256, seconds per batch50:0.169034
Saved checkpoint 77000 steps.
step 77000, training accuracy 0.99646
step 77000, test accuracy 0.7481
current step:77500, example per seconds:197.637497, seconds per batch50:0.252988
Saved checkpoint 77500 steps.
current step:78000, example per seconds:293.784165, seconds per batch50:0.170193
Saved checkpoint 78000 steps.
step 78000, training accuracy 0.98824
step 78000, test accuracy 0.7365
current step:78500, example per seconds:197.277836, seconds per batch50:0.253450
Saved checkpoint 78500 steps.
current step:79000, example per seconds:294.820197, seconds per batch50:0.169595
Saved checkpoint 79000 steps.
step 79000, training accuracy 0.99218
step 79000, test accuracy 0.7436
current step:79500, example per seconds:198.322529, seconds per batch50:0.252115
Saved checkpoint 79500 steps.
current step:80000, example per seconds:294.306543, seconds per batch50:0.169891
Saved checkpoint 80000 steps.
step 80000, training accuracy 0.99402
step 80000, test accuracy 0.7474
current step:80500, example per seconds:196.824128, seconds per batch50:0.254034
Saved checkpoint 80500 steps.
current step:81000, example per seconds:291.379395, seconds per batch50:0.171598
Saved checkpoint 81000 steps.
step 81000, training accuracy 0.99568
step 81000, test accuracy 0.745
current step:81500, example per seconds:197.335431, seconds per batch50:0.253376
Saved checkpoint 81500 steps.
current step:82000, example per seconds:289.138420, seconds per batch50:0.172928
Saved checkpoint 82000 steps.
step 82000, training accuracy 0.99478
step 82000, test accuracy 0.7507
current step:82500, example per seconds:197.323332, seconds per batch50:0.253391
Saved checkpoint 82500 steps.
current step:83000, example per seconds:293.212932, seconds per batch50:0.170525
Saved checkpoint 83000 steps.
step 83000, training accuracy 0.9882
step 83000, test accuracy 0.7351
current step:83500, example per seconds:196.296710, seconds per batch50:0.254716
Saved checkpoint 83500 steps.
current step:84000, example per seconds:294.436702, seconds per batch50:0.169816
Saved checkpoint 84000 steps.
step 84000, training accuracy 0.9967
step 84000, test accuracy 0.7512
current step:84500, example per seconds:197.104605, seconds per batch50:0.253672
Saved checkpoint 84500 steps.
current step:85000, example per seconds:294.094144, seconds per batch50:0.170014
Saved checkpoint 85000 steps.
step 85000, training accuracy 0.99428
step 85000, test accuracy 0.7504
current step:85500, example per seconds:197.217746, seconds per batch50:0.253527
Saved checkpoint 85500 steps.
current step:86000, example per seconds:293.804611, seconds per batch50:0.170181
Saved checkpoint 86000 steps.
step 86000, training accuracy 0.9953
step 86000, test accuracy 0.7514
current step:86500, example per seconds:197.211661, seconds per batch50:0.253535
Saved checkpoint 86500 steps.
current step:87000, example per seconds:294.599888, seconds per batch50:0.169722
Saved checkpoint 87000 steps.
step 87000, training accuracy 0.99664
step 87000, test accuracy 0.7518
current step:87500, example per seconds:197.665943, seconds per batch50:0.252952
Saved checkpoint 87500 steps.
current step:88000, example per seconds:294.524426, seconds per batch50:0.169765
Saved checkpoint 88000 steps.
step 88000, training accuracy 0.99422
step 88000, test accuracy 0.7527
current step:88500, example per seconds:195.881285, seconds per batch50:0.255257
Saved checkpoint 88500 steps.
current step:89000, example per seconds:295.625992, seconds per batch50:0.169133
Saved checkpoint 89000 steps.
step 89000, training accuracy 0.99684
step 89000, test accuracy 0.7523
current step:89500, example per seconds:198.022530, seconds per batch50:0.252497
Saved checkpoint 89500 steps.
current step:90000, example per seconds:292.791445, seconds per batch50:0.170770
Saved checkpoint 90000 steps.
step 90000, training accuracy 0.99604
step 90000, test accuracy 0.7475
current step:90500, example per seconds:197.219058, seconds per batch50:0.253525
Saved checkpoint 90500 steps.
current step:91000, example per seconds:294.330921, seconds per batch50:0.169877
Saved checkpoint 91000 steps.
step 91000, training accuracy 0.99736
step 91000, test accuracy 0.7608
current step:91500, example per seconds:197.545207, seconds per batch50:0.253107
Saved checkpoint 91500 steps.
current step:92000, example per seconds:294.391754, seconds per batch50:0.169842
Saved checkpoint 92000 steps.
step 92000, training accuracy 0.99646
step 92000, test accuracy 0.7443
current step:92500, example per seconds:198.695717, seconds per batch50:0.251641
Saved checkpoint 92500 steps.
current step:93000, example per seconds:296.363455, seconds per batch50:0.168712
Saved checkpoint 93000 steps.
step 93000, training accuracy 0.99802
step 93000, test accuracy 0.7534
current step:93500, example per seconds:196.229426, seconds per batch50:0.254804
Saved checkpoint 93500 steps.
current step:94000, example per seconds:295.580002, seconds per batch50:0.169159
Saved checkpoint 94000 steps.
step 94000, training accuracy 0.99586
step 94000, test accuracy 0.7469
current step:94500, example per seconds:198.746608, seconds per batch50:0.251577
Saved checkpoint 94500 steps.
current step:95000, example per seconds:293.778123, seconds per batch50:0.170196
Saved checkpoint 95000 steps.
step 95000, training accuracy 0.99426
step 95000, test accuracy 0.7435
current step:95500, example per seconds:198.670157, seconds per batch50:0.251673
Saved checkpoint 95500 steps.
current step:96000, example per seconds:291.153509, seconds per batch50:0.171731
Saved checkpoint 96000 steps.
step 96000, training accuracy 0.99674
step 96000, test accuracy 0.7508
current step:96500, example per seconds:197.796029, seconds per batch50:0.252786
Saved checkpoint 96500 steps.
current step:97000, example per seconds:295.470861, seconds per batch50:0.169221
Saved checkpoint 97000 steps.
step 97000, training accuracy 0.99588
step 97000, test accuracy 0.7441
current step:97500, example per seconds:197.157363, seconds per batch50:0.253605
Saved checkpoint 97500 steps.
current step:98000, example per seconds:290.391080, seconds per batch50:0.172182
Saved checkpoint 98000 steps.
step 98000, training accuracy 0.99784
step 98000, test accuracy 0.7558
current step:98500, example per seconds:197.110118, seconds per batch50:0.253665
Saved checkpoint 98500 steps.
current step:99000, example per seconds:291.792440, seconds per batch50:0.171355
Saved checkpoint 99000 steps.
step 99000, training accuracy 0.98968
step 99000, test accuracy 0.7395
current step:99500, example per seconds:199.283242, seconds per batch50:0.250899
Saved checkpoint 99500 steps.
current step:100000, example per seconds:295.517401, seconds per batch50:0.169195
Saved checkpoint 100000 steps.
step 100000, training accuracy 0.99498
step 100000, test accuracy 0.7525
