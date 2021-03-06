# deepLeaningDevolopment
Model&Algorithem&Data

国际会议 ICLR

作者：Naiyan Wang 链接：https://www.zhihu.com/question/47602063/answer/155705198
1. 针对特定问题的Unsupervised Learning： GAN自从去年NIPS之后就成了想AlphaGo一样火爆的关键词，似乎不搞GAN就不是做ML的一样 :-D 然而，Unsupervised Learning不仅仅有GAN。从我的角度来看，GAN这样的东西过于通用而不具有太多实用的价值。（当然这个不绝对，也有不少利用GAN思想很漂亮解决实际问题的工作。）我个人更关注的是来自Berkeley和CMU两个组的Unsupervised Learning的工作。这些工作的一个特性就是，充分利用了vision数据中的一些特点来寻找Supervision Signal，既可以是motion，也可以是context等等。然而所有这些方法最终都是在PASCAL VOC等这些通用的high level vision的数据集上测试，我们觉得是非常不合适的。不同类型的任务，需要的feature也应该是大相径庭的。所以，一方面，我们根据想解决的问题，灵活利用这些天然存在的supervision signal去设计我们的unsupervised learning算法，使得unsupervised learning的过程能真正帮助我们解决存在的问题；另一方面，在我们在做的自动驾驶中，存在更多multi modal的数据。除去RGB图像，可能还会有Lidar, GPS, IMU等等。如何交叉利用这些multi modal的信息，寻找最廉价有效的Supervision Signal，也会是一个很有意义的问题。最终我们希望，通过这些虽然噪声较大，但是廉价的自标注数据，大幅度降低对人工标注高精度数据的需求。我们去年最开始的一个尝试，也已经发表在ICRA2017上。

2. 传统问题的一些新的setting：像Object Detection这些传统问题，在众多大神这两年的快速推进中，单从性能上而言，已经达到了一个相当不错的阶段。我个人的观点来说，继续压榨这些传统setting，边际收益可能会很低。然而，单就detection而言，我们可以衍生出Video Detection，RGBD Detection，Instance Segmentation等等新的setting。如何利用好这些额外的信息，以比较小的代价获取最大的性能提升，对于这些新的setting来说都是非常值得研究的。而且这些新的setting的诞生，其实背后都是会有一些实际的应用场景，这些问题兼具研究的价值与实用性。其余一些传统的问题，例如Semantic Segmentation等，也存在这样的情况。

3. 模型加速（非压缩）：很多人前面都提到了这一点，然而这里有一个很大的误区是错把压缩当成加速。一个方法可以有很少的参数量，然而运算速度仍旧很慢。一个极端的例子就是RNN，每个time step共享参数，然而我们可以把RNN unroll无限的长度。我们更关心的其实在于加速，而非压缩。压缩做到一个几十倍甚至几百倍并非难事。尤其是可以充分现有硬件条件下，能实现的wall clock而非理论复杂度的加速更是凤毛麟角。单单这两个条件，应该就可以过滤掉目前90%的paper了。这仍然是有着无限可能性的一个领域。

4. Imitation Learning：如何从少量的demonstration中，快速学习一个还不错的policy，而后在环境中自由演化，甚至超越原始的demonstration。这方面一个很好的例子就是AlphaGo，会从棋谱中学习一个还不错的policy，然后再开始左右互搏。这样一个问题的意义在于，我们可以在模型初期避开一些完全毫无道理的bad case，在一些safety critical的问题中，得到一个较好的初始解。也可以加快后期policy迭代的收敛。

5. Confidence Learning：目前虽然deep learning在性能上取得了非常大的进步，甚至超越了人类的水平，然而仍然在一些corner case下，性能仍会一落千丈，输出的结果完全离谱。然而在一些高可靠性的系统中，我们需要保证worst case performance。这是一个更加困难的问题。退一步而言，我们有没有办法可以让模型对于输出的结果输出一个confidence？例如在无人车的一些场景中，如果我们发现算法本身并不可靠，与其盲目蛮干，我们可以安全路边停车，将控制权交还给驾驶员。这个方向虽然有一些初步研究，然而离实用仍又很大距离。这个问题的解法可能很多元，既可以用Bayes的角度来看，也可以从Sample Density的角度来看。仍然存在着各种可能性

---2017-12-21---
AAAI-17 The best paper-- Label-Free Supervision of Neural Networks with Physics and Domain Knowledge
http://baijiahao.baidu.com/s?id=1565706636578020&wfr=spider&for=pc 
6位大牛21场演讲，一文看尽最牛深度学习大会ICLR！
