# Chapter 1 引子
> “数据！数据！数据！”他焦急地高叫着，“(如果没有数据)，巧妇难为无米之炊啊！”

> --Arthur Conan Doyle

## 数据力量
我们正生活在一个被数据淹没的世界。各大网站都会记录每一个访问者的每一次点击数据，智能手机会记录使用者每一天每一秒的位置和速度数据。量化生活者会使用计步器记录自己的心跳，运动习惯，饮食和睡眠数据。智能汽车会搜集行车习惯数据，智能住宅会搜集生活习惯数据，智能店铺会搜集购物习惯数据。就连互联网本身所代表的无所不知的巨大知识库也是由无数相互链接的数据组成的一本百科全书；专业领域知识库可以提供关于电影、音乐、体育赛事结果、弹珠台机器、文化基因和鸡尾酒的各种数据；以及无数由政府提供的统计数据(有一部分还是接近事实的)，这些数据都充斥在你的生活中。

埋藏在这些数据下面的是对于无数问题的惊奇的答案。在这本书中，我们将会教会你如何寻找这些答案。

## 数据科学是什么？
有一个关于数据科学家的笑话说，数据科学家就是那些比计算科学家知道更多统计知识而且比统计学家知道更多计算机知识的人(我个人并不认为这是一个好笑话)。事实上，从实用角度说，一些数据科学家确实是统计学家，但是另外的数据科学家则更像计算机工程师。一些数据科学家是机器学习专家，但是也存在不少数据科学家从幼儿园开始就没有接触过机器学习。一些数据科学家是发表过出色论文的博士，但是也有不少数据科学家是从来没有读过学术论文的人(对此我深表遗憾，他们应当感到羞愧)。一言以蔽之，无论人们如何定义数据科学，你一定可以找到让这个定义完全错误的数据科学家。

当然这并意味着我们不能尝试对于数据科学家下一个定义。我们认为数据科学家就是那些从混乱的原始数据中提取有用经验和启发性观点的人。事实上，现实生活中也的确有不少人正在努力从数据中得到有用经验和启发性观点。

比如，相亲网站 OkCupid 要求用户回答很多问题，这些问题可以帮助 OkCupid 寻找该用户最匹配的约会对象。但是有时这些问题也可以帮助人们预测一些无伤大雅的精彩问题，比如你可以要求 OkCupid 预测你是不是能够和你的约会对象在第一次约会的时候发生一次超友谊的亲密接触。

Facebook 也同样要求用户列出他们的家乡和现居地，虽然表面上看这确实可以帮助真实生活中的朋友更加容易地联系到你，但是 Facebook 也利用这些数据来分析很多其他问题，比如：全球人口的移民模式以及某支球队的球迷大本营。

作为一家大型零售店，Target 会记录你在线上和线下店铺的购物交互数据。Target 会使用这些数据来预测客户是不是怀孕了来向怀孕的用户推销他们的婴幼儿用品。

2012年，奥巴马的竞选团队雇佣了很多数据科学家。这些数据科科学家使用数据挖掘技术识别出必须格外重视的选民，帮助竞选团队选择出最佳的竞选募捐策划，同时展开更有针对性的竞选募捐活动，并且用最有效的方式吸引选民参与投票。这些数据科学家们被普遍认为在奥巴马的第二次胜选中起到了重要作用。奥巴马的这次选举标志着未来的选举一定会变得越来越数据驱动，他们将使得竞选活动更加依赖数据进行决策，这也将会把竞选活动变成一场没有尽头的数据科学和数据搜集能力的军备竞赛。

在你开始感到厌烦之前，我不得不说：有些数据科学家有时也会运用他们的才智和掌握的数据来提高政府效率，比如救助无家可归者或者提高公众健康水平。当然如果你志不在此，而是希望研究出最好的吸引用户点击广告的方法等，这些致力于提高公众利益的数据科学家对于你的事业也完全没有任何伤害。

## 假设场景 : DataSciencester
恭喜你！你已经被任命为一家专为数据科学家服务的社交网站 DataSciencester 的首席数据科学家，你将全面负责 DataSciencester 网站的数据业务。

虽然这是专为数据科学家服务的网站，但是 DataSciencester 从来没有建立过自己的数据科学实践(更准确地说，DataSciencester 也从来没有建立过自己的产品)。现在该你出场了！在这本书中，你将通过解决实际工作中遇到的问题来学习数据科学的基本概念。有时我们需要研究用户直接提供的数据，有时我们需要研究用户和网站间接交互的数据，有时我们甚至需要研究通过我们自己设计的实验获得的数据。

同时因为 DataSciencester 有强烈的极客原创精神，我们需要从头构建自己的工具。通过这本书，你会对于数据科学有一个完整的详实理解。学完本书，在将来的工作中，我们希望你能够运用学到的知识和技能为陷入困境的公司提供帮助或者去研究任何吸引你的问题。

欢迎加入，祝你一帆风顺！(闲谈一句，通常，作为数据科学家你可以在周五穿着牛仔裤上班而且楼下的浴室随时待命。)

###寻找关键联系人
好了，现在你开始了在 DataSciencester 工作的第一天，公司负责客户网络的高管对于 DataSciencester 网站的用户有不少疑问，以前他找不到人帮忙，现在他非常高兴你加入了公司并且希望你可以帮助到他。

首先，他特别希望你帮助他在数据科学家用户中找出那些“关键联系人”。所以他给了你他已经得到的关于整个DataSciencester 用户关系的数据(但是，你需要注意的是，在真实的工作中，你常常得不到到你希望的数据而不得不自己动手获取数据，我们将在第 9 章详细讨论如何获取需要的数据)。

这些数据到底是什么呢？它是一个包括所有用户的 Python 列表，列表的每一个元素都是一个字典，字典包含了用户的 id 数字和用户的姓名(巧合的是，这些 id 的用户名都有和 id 数字谐音的部分)

```python
users = [
    { "id": 0, "name": "Hero" },
    { "id": 1, "name": "Dunn" },
    { "id": 2, "name": "Sue" },
    { "id": 3, "name": "Chi" },
    { "id": 4, "name": "Thor" },
    { "id": 5, "name": "Clive" },
    { "id": 6, "name": "Hicks" },
    { "id": 7, "name": "Devin" },
    { "id": 8, "name": "Kate" },
    { "id": 9, "name": "Klein" }
    ]
```

同时你得到了一组表示“友谊关系”的数据，就是如下的这个包含 id 号码的`friendships`列表：

比如，元组 (0, 1) 代表 id 为 0 的数据科学家( Hero ) 和 id 为 1 的数据科学家 ( Dunn ) 是朋友。这个关系也可以用图 1-1 来表示：
![](F1-1.png)
>![](images_001.jpg)
> 暂时不要在代码的细节上纠缠太久。在第 2 章中，我们会带着你快速的学习 Python 。现在你只需要大致理解这些代码是为了实现哪些目标即可。

因为我们使用 Python 的字典结构来表示用户，所以我们可以非常方便地添加更多的数据。

比如，我们可以尝试给每一个用户添加一个朋友列表。首先我们对每一个用户创建一个代表朋友属性的空列表。

```python
for user in users:
    user["friends"] = []
```
然后我们可以通过`friendships`数据来填充`friends`属性列表。
```python
for i, j in friendships:
#这段代码可以工作是因为 users[i] 就是 id 为 i 的用户
    users[i]["friends"].append(users[j])                   # 给用户 i 添加朋友 j
    users[j]["friends"].append(users[i])                   # 给用户 j 添加朋友 i
```

一旦每一个用户字典都包括了一个朋友列表，我们就可以很容易地进一步探索朋友关系图的性质，比如 “平均一个用户有多少个朋友？”。

要回答这个问题，首先我们必须找出所有的朋友关系数，这只需要统计朋友列表的长度就可以了。

```python
def number_of_friends(user):
    """每一个用户有多少朋友"""
    return len(user["friends"])                                         # 朋友列表长度

total_connections = sum(number_of_friends(user)
                    for user in users)                                  # 24
```
这样我们只需要简单地除以用户数即可得到平均一个用户有多少朋友了：
```python
from __future__ import division                 #引入整数除法特性
#注意该语句必须是模块或程序的第一个语句。
num_users = len(users)  #列表长度为10
avg_connections = total_connections / num_users #每一个用户平均拥有的朋友数 2.4
```
同样的思路我们也可以很容易地找出朋友关系最多的人——他们就是有最多朋友数目的人。

因为数据量不是特别大，所以我们可以很容易地对所有的用户按照从“朋友最多的人”到“朋友最少的人”的顺序进行排序：
```python
#创建一个朋友数目列表num_friends_by_id
num_friends_by_id = [(user["id"],number_of_friends(user))
                 for user in users]

sorted(num_friends_by_id,                             #排序列表
   key=lambda (users_id , num_friends): num_friends,  #依照num_friends排序
   reverse=True)                                      #倒序输出，从最大到最小

#num_friends_by_id输出结果如下，每一对都是(user_id，num_friends)组合：
#[(0, 2), (1, 3), (2, 3), (3, 3), (4, 2),
# (5, 3),(6, 2), (7, 2), (8, 3), (9, 1)]
```
如果换一个思路，从社交网络的角度来理解我们刚刚完成的工作，就是找出这个用户关系网络中占据最中心位置的人。事实上，我们刚刚计算了这个网络的重要属性之一：程度中心性(见图 1-2).
![](F1-2.png)

程度中心性非常方便计算， 但是不能给出更多准确的细节信息。比如，在 DateSciencester 的用户朋友网络中我们知道，用户 Thor (id 为 4 )只有 2 个朋友关系，而用户 Dunn ( id 为 1 )有 3 个朋友关系。但是回头看一看上面展示的网络图，似乎 Thor 更加具有程度中心性。 在第 21 章，我们将会更加仔细地讨论网络的性质和研究更加复杂的中心性定义，这些更加复杂的中心性可能会更加合适。

### 你可能认识的数据科学家

当你正在努力填写新员工登记表的时候，负责人事的高管来到你的办公桌前。她希望能够激发数据科学家之间更多的交流和联系，因此她希望你能够策划一个“你可能认识的数据科学家”的提示功能。

你的直觉告诉你一个用户很有可能认识自己朋友的朋友。这个想法非常容易验证：对于每一个用户的朋友们，验证这个朋友的朋友是不是被这个用户认识，最后合并结果即可检测这个想法是不是可靠：

```python
def friends_of_friend_ids_bad(user):
# "foaf" 是 "friend of a friend"的简称
    return [foaf["id"]
        for friend in user["friends"] # 对于每一个用户的朋友们
        for foaf in friend["friends"]] # 检验这个朋友的朋友是不是这个用户的朋友
```

当我们把上面的函数作用在第一个用户`users[0]`上的时候,`friends_of_friend_ids_bad(users[0])`给出如下的结果
```python
[0, 2, 3, 0, 1, 3]
```
结果中包括了用户 0 两次，因为用户 0 ( Hero )确实同时是他的两个朋友的朋友。结果中也包括用户 1 和用户 2 ，虽然他们已经是用户 1 的朋友。同时他也包括了用户 3 两次，因为用户 3 ( Chi ) 可以通过用户 0 的两个朋友和用户 0 联系起来，具体的验证代码如下：

```python
print [friend["id"] for friend in users[0]["friends"]] #[1, 2]
print [friend["id"] for friend in users[1]["friends"]] #[0, 2, 3]
print [friend["id"] for friend in users[2]["friends"]] #[0, 1, 3]
```
知道人们可以借助自己朋友的朋友互相认识彼此是非常有趣的信息，所以或许我们应该统计下通过共同朋友可能成为朋友的数目。为了实现这个目的，我们需要借助辅助函数来排除已经彼此认识成为朋友的那批用户：
```python
from collections import Counter # 并不默认加载collection函数

def not_the_same(user, other_user):
"""排除相同用户"""
    return user["id"] != other_user["id"]

def not_friends(user, other_user):
"""other_user用户并不是user用户的朋友;也就是 other_user并不和user用户的friends列表中个的用户相同"""
     return all(not_the_same(friend, other_user)
           for friend in user["friends"])

def friends_of_friend_ids(user):
    return Counter(foaf["id"]
               for friend in user["friends"]  # 对于每一个user用户的朋友
               for foaf in friend["friends"]  # 对于每一个user用户朋友的朋友
               if not_the_same(user, foaf)    # 排除相同用户
               and not_friends(user, foaf))   # 排除已经是朋友的用户

print friends_of_friend_ids(users[3]) # Counter({0: 2, 5: 1})
```
这个输出结果正确地说明用户 Chi (id 为 3 ) 和用户 Hero ( id 为 0 ) 之间有 2 个共同朋友，而和用户 Clive ( id 为 5) 只有 1 个共同用户。

作为一个数据科学家，你知道大家都喜欢遇到和自己有共同兴趣的人。(事实上，下面要做的这个小探索是对数据科学家需要掌握的专业技能的精彩展示。) 通过咨询朋友，你得到了如下的数据，这个列表的每一个元素都包括一个由用户 id 和兴趣 interest 组成的元组 。
```python
interests = [
(0, "Hadoop"), (0, "Big Data"), (0, "HBase"), (0, "Java"),
(0, "Spark"), (0, "Storm"), (0, "Cassandra"),
(1, "NoSQL"), (1, "MongoDB"), (1, "Cassandra"), (1, "HBase"),
(1, "Postgres"), (2, "Python"), (2, "scikit-learn"), (2, "scipy"),
(2, "numpy"), (2, "statsmodels"), (2, "pandas"), (3, "R"), (3, "Python"),
(3, "statistics"), (3, "regression"), (3, "probability"),
(4, "machine learning"), (4, "regression"), (4, "decision trees"),
(4, "libsvm"), (5, "Python"), (5, "R"), (5, "Java"), (5, "C++"),
(5, "Haskell"), (5, "programming languages"), (6, "statistics"),
(6, "probability"), (6, "mathematics"), (6, "theory"),
(7, "machine learning"), (7, "scikit-learn"), (7, "Mahout"),
(7, "neural networks"), (8, "neural networks"), (8, "deep learning"),
(8, "Big Data"), (8, "artificial intelligence"), (9, "Hadoop"),
(9, "Java"), (9, "MapReduce"), (9, "Big Data")
]
```
比如，用户 Thor ( id 为 4 ) 和用户 Devin ( id 为 7 ) 没有任何相同的朋友，但是他们都对于机器学习有兴趣。

非常容易地我们就可以构建一个函数寻找有相同兴趣的用户：
```python
def data_scientists_who_like(target_interest):
    return [user_id
        for user_id, user_interest in interests
        if user_interest == target_interest]
```
虽然上面的方法可以正确得出我们期望的结果，但是每一次都必须遍历整个兴趣列表。如果我们有很多的用户和兴趣对或者我们希望做大量的查找，这样的程序效率就比较低来。因此，我们应该专门建立一个从兴趣到用户的检索：
```python
from collections import defaultdict

# 字典的键是兴趣，值是对该兴趣感兴趣用户名列表
user_ids_by_interest = defaultdict(list)

for user_id, interest in interests:
    user_ids_by_interest[interest].append(user_id)
```
另一种形式是从用户到兴趣的检索：
```python
# 键是用户名，值是该用户的兴趣列表
interests_by_user_id = defaultdict(list)

for user_id, interest in interests:
   interests_by_user_id[user_id].append(interest)
```
现在我们可以很容易的找到对于一个特定的用户和他有最多相同兴趣的用户了，具体思路如下：

* 对该用户的兴趣列表做一次循环
* 对于该用户的每一个兴趣，在相应的兴趣对应的用户列表中再次循环
* 记录下每一个用户在这样的循环中出现的次数

具体实现的代码为：
```python
def most_common_interests_with(user_id):
     return Counter(interested_user_id
         for interest in interests_by_user_id[user_id]
         for interested_user_id in user_ids_by_interest[interest]
         if interested_user_id != user_id)
```

或许将来，我们可以通过这个方法整合共同朋友和共同兴趣数据来构建一个更加丰富的“你应该知道的数据科学家”的功能。在第 22 章，我们将深入讨论这一点。

### 工资和经验的关系

现在你打算去吃午饭，但是负责公共关系的高管询问你是不是能够提供一些关于数据科学家收入的有趣事实。收入数据当然是非常敏感的数据，所以负责公共关系的高管给你提供的是匿名后的收入数据(单位:美元)和工作年限数据(单位:年)。
```python
salaries_and_tenures = [(83000, 8.7), (88000, 8.1),
                        (48000, 0.7), (76000, 6),
                        (69000, 6.5), (76000, 7.5),
                        (60000, 2.5), (83000, 10),
                        (48000, 1.9), (63000, 4.2)]
```
非常自然地，第一步就是先对这些数据先做一副关系图来探索可能存在的关系(我们将在第 3 章研究如何画图)。现在你可以在图 1-3 看到画图的结果：
![](F1-3.png)

趋势看起来非常明显，工作时间越长挣得越多。但是你怎么把这幅图转化成一个有趣的故事？你的第一个想法就是查看不同工作年限的平均工资：
```python
# 键是工作年限，值是每一个工作年限的工资
salary_by_tenure = defaultdict(list)

for salary, tenure in salaries_and_tenures:
    salary_by_tenure[tenure].append(salary)

# 键是工作年限，值是每一个工作年限的平均工资
average_salary_by_tenure = {
    tenure : sum(salaries) / len(salaries)
    for tenure, salaries in salary_by_tenure.items()
}
```
当然，这看起来不是特别有用，因为没有一个用户有相同的工作年限，这也就意味着我们其实只是在报告每一个单独用户的工资而不是多个用户的平均工资，具体结果如下：
```python
{0.7: 48000,
 1.9: 48000,
 2.5: 60000,
 4.2: 63000,
   6: 76000,
 6.5: 69000,
 7.5: 76000,
 8.1: 88000,
 8.7: 83000,
  10: 83000}
```
更有用的可能是将工作年限做一个粗略地分组再进行统计，代码如下：
```python
def tenure_bucket(tenure):
    if tenure < 2:
        return "less than two"
    elif tenure < 5:
        return "between two and five"
    else:
        return "more than five"
```
然后把属于同一个工作年限分组的工资数据合并到一个列表中，具体代码如下：
```python
#键是工作年限分组数据，值是该工作年限分组对应的工资列表
salary_by_tenure_bucket = defaultdict(list)

for salary, tenure in salaries_and_tenures:
     bucket = tenure_bucket(tenure)
     salary_by_tenure_bucket[bucket].append(salary)
```
最后对每一个工作年限分组计算平均值，具体代码如下：
```python
average_salary_by_bucket = {
    tenure_bucket : sum(salaries) / len(salaries)
    for tenure_bucket, salaries in salary_by_tenure_bucket.iteritems()
 }
```
这样我们可以得到一个更加有意思的结果：
```python
{'between two and five': 61500,
  'less than two': 48000,
  'more than five': 79166}
```

现在终于你有了一个可以大声宣传的有趣的事实：“有5年以上工作经验的数据科学家比菜鸟数据科学家可以多挣65%”。

当然，我们必须承认我们的分组标准是粗略选择的。事实上我们真正想说明的是，平均而言，更多的工作经验对于工资的会有积极的影响。更进一步，为了做出一些更加吸引人的有趣事实，或许我们应该对于未来做一些大胆的预测。虽然我们可能并不知道的这些工作年限对应的工资数据。我们将在第 14 章仔细研究这个思路。

### 付费用户

当你吃完午饭回到办公室的时候，负责财务的高管正在等你。她希望能够更好地区分出付费用户和未付费用户。(她已经知道付费用户和未付费用户的用户名，但是没有更进一步的信息。)

你注意到工作年限和是否付费之间似乎存在某种联系。