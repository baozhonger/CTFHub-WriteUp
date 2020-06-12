# # 题目

![image-20200525184259655](https://shaun.oss-cn-beijing.aliyuncs.com/typora/202005/25/184301-253568.png/watermark)

![image-20200525184320996](https://shaun.oss-cn-beijing.aliyuncs.com/typora/202005/25/184336-633602.png/watermark)

打开环境，会发现需要admin才能拿到旗子。检查cookie，发现name已经是admin。

![image-20200525184419102](https://shaun.oss-cn-beijing.aliyuncs.com/typora/202005/25/184420-979389.png/watermark)

# # 题解

## ## curl

使用控制台，curl命令的`--cookie`参数，传入cookie。

```shell
curl http://challenge-467c9e9c546efda9.sandbox.ctfhub.com:10080/ --cookie "admin=1;"
```

如图，这样就可以得到旗子了。

![image-20200525184627439](https://shaun.oss-cn-beijing.aliyuncs.com/typora/202005/25/184629-296196.png/watermark)

## ## Burp Suite

抓包结果如图所示👇。将其中的`Cookie`中的`admin=0`改为**`admin=1`**，释放。

![image-20200525184756631](https://shaun.oss-cn-beijing.aliyuncs.com/typora/202005/25/184759-297036.png/watermark)

![image-20200525184944596](https://shaun.oss-cn-beijing.aliyuncs.com/typora/202005/25/184946-217702.png/watermark)

![image-20200525184959731](https://shaun.oss-cn-beijing.aliyuncs.com/typora/202005/25/184959-613074.png/watermark)

# # 总结

在得到正确答案之前，我进行了很多错误的尝试。对于cookie中name已经是admin却任然拿不到旗子很费解。
得到正确答案，根据答案来看，**cookie的一行应该为一条数据**。也就是说这条数据的 **“名字”** 叫做admin，其 **值** 为0。当值等于1的时候，才符合要求。

![20200409000203567](https://shaun.oss-cn-beijing.aliyuncs.com/typora/202005/25/192003-453583.png/watermark)