# Mobike_Data_Tableau
Visualization by
# Mobike Data Visualization

## 作品
**第一版** __[link text](https://public.tableau.com/profile/junqi.hu#!/vizhome/Mobike_Data_Tableau/1?publish=yes)__

**第二版** __[link text](https://public.tableau.com/profile/junqi.hu#!/vizhome/Mobike_Data_Tableau2_0/1_1?publish=yes)__

## 总结： 
>这份Tableau可视化的报告数据来源于摩拜提供的的上海城区2016年8月份随机抽样用户使用数据,包含起点、目的地、租赁时间、还车时间、用户ID、车辆ID、交易编号等信息,该数据集为 上海 SODA 比赛样本数据。我主要做了八月份每日的平均骑行时间统计,用户每次骑行时长的统计,每日骑行订单数统计,用户的骑行轨迹图,用户的骑行出发点分布图，用户的骑行结束点分布图,一天中各时段用户骑行时间统计。目的是为了探究Mobike共享单车用户的使用时间，常用时间以及常用地点。结果我发现,用户的骑行时间主要分布在5Min至20Min,骑行的高峰时间为上午8点和下午18点上下班时间，用户对共享单车的需求逐日增长，以及单车的使用地点分布在个地铁站附近。
## 设计： 解释你所做的任何设计选择，包括收集反馈后对可视化进行的更改
1. 一日中用户每日各时段骑行订单数统计
>首先我想做的分析是统计一天中用户骑行订单的高峰期,于是我将start_time展开到小时作为X轴,将自己创建的计算字段(不同订单的总数)作为y轴,创建了一个折线图。

![Total Number of Orders](https://github.com/Mesilenceki/Mobike_Data_Tableau/blob/master/img/1.PNG)

>通过上面的折线图我们可以看到,在一天中,用户的骑行订单数呈现除两个高峰:上午8时和下午18时,这一时间段也恰好与人们的上下班高峰时间吻合,说明人们经常使用共享单车作为通勤工具。
2. 每日骑行订单数统计
>随后我想分析在整个八月份中,用户每日的骑行订单总数的变化趋势,类似于1中的分析,于是我将start_time展开到以天为计算单位作为x轴,将自己创建的计算字段(不同订单的总数)作为y轴,创建了一个折线图。

![Total Number of Orders in August](https://github.com/Mesilenceki/Mobike_Data_Tableau/blob/master/img/2.PNG)

>通过上面的折线图我们可以发现,整个八月份,用户每日的骑行订单数呈现着逐步上升的趋势,这说明人们以及在逐步接受共享单车这一出行方式。
3. 用户每次骑行时长的统计 
>接着我想要分析用户每次使用Mobike共享单车的骑行时间,于是我通过python：将"start_time"-"end_time",并且将其除于60取整,以min作为单位,创建了一个名为"Duration"的变量作为x轴，并且将自己创建的计算字段(不同订单的总数)作为y轴，创建了一个条形图。

![Total Number of different duration](https://github.com/Mesilenceki/Mobike_Data_Tableau/blob/master/img/3.PNG)

>通过对用户每次骑行时长的统计,我们可以发现每次骑行时长基本在5min到20min之间,这也符合人们对共享单车的需求,说明大家更多的只是将共享单车作为短距离代步的工具。
4. 八月份每日的平均骑行时间统计
>我接着分析了八月份中用户每日的骑行时间的统计,于是我将start_time展开到以天为计算单位作为x轴,将duration作为y轴,创建了一个折线图。

![Average Duration of the Day in Aug](https://github.com/Mesilenceki/Mobike_Data_Tableau/blob/master/img/4.PNG)

>从上面的折线图我们可以发现，用户每日的骑行时间没有太大的变化,基本在[25,33]之间波动变化,我猜想这是否与上海当地的天气状况有关,于是我查阅了上海2016年8月份的天气,果然用户时间较短的那几天上海的天气基本为阵雨,中雨或者是雷阵雨。
5. 用户的骑行出发点分布图
>我接着分析了用户的骑行出发点的分布图,我将"start_location_x"作为x轴,"start_location_y"作为y轴,绘制了一个密度图,并且添加了上海地铁的线路图作为比较和参考

![Plot of Start Location](https://github.com/Mesilenceki/Mobike_Data_Tableau/blob/master/img/5.PNG)

>我发现,用户骑行出发点比较密集的地方普遍是地铁站的附近。
6. 用户的骑行结束点分布图
>接着分析了用户的骑行出发点的分布图,我将"end_location_x"作为x轴,"end_location_y"作为y轴,绘制了一个密度图.

![Plot of End Location](https://github.com/Mesilenceki/Mobike_Data_Tableau/blob/master/img/6.PNG)

>结合上面两幅地理密度图的观察,我发现用户一般喜欢将共享单车作为地铁的接驳工具,这告诉我们可以在地铁站的附近设置多点共享单车
7. 用户的骑行轨迹图
>出于好奇,我想观察用户每次骑行的轨迹图,于是我通过Python处理了数据集中的Track数据,提取了每次轨迹的所有路径的经纬度,并将其作为坐标绘制了用户的骑行轨迹图。

![Riding Trajectory Map](https://github.com/Mesilenceki/Mobike_Data_Tableau/blob/master/img/7.PNG)


## 反馈： 

1. 版本1.0
    1.第一幅图的坐标不够准确,此外两条线的区别程度不是很大,放在一起反而容易使读者混淆,建议删除一条。
    2.第五幅图关于出发点的分布图不太容易辨别。
    3.用户的骑行时长可能和周末或者工作日有关。
        于是我新增加了一个计算字段，判断用户出行的日期是工作日还是周末，并将其作为颜色辨别。我发现这样使得我的分析更有说服力。
 

## 资源： 
__[link text](http://https://onlinehelp.tableau.com/current/pro/desktop/zh-cn/maps_howto_origin_destination.htm)__

__[link text](https://community.tableau.com/thread/125088)__
