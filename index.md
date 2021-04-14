## Welcome to Jiatong Li's homepage!

---

## Index
- [Welcome to Jiatong Li's homepage!](#welcome-to-jiatong-lis-homepage)
- [Index](#index)
- [About me](#about-me)
- [My personal CV](#my-personal-cv)
- [About my research](#about-my-research)
  - [Cognitive diagnosis and its application in intelligent education](#cognitive-diagnosis-and-its-application-in-intelligent-education)
- [Awards](#awards)
- [Study notes](#study-notes)

## About me 

<img src="./My_personal_CV/profile.jpg" width="150" align="right">

* E-mail: satosasara[AT]mail[dot]ustc[dot]edu[dot]cn
  
I am currently a junior major in **data science** in **University of Science and Technology of China** (USTC). Before that, I lived in Canton for over 15 years. I like delicious food, gym and classic musics! After studying in the school of data science, I found my interest in the research of machine learning, and I am now doing research on the use of deep learning in **cognitive diagnosis**, which is part of an intelligent education system. 

## My personal CV
* English version: [click here](./My_personal_CV/LiJiatong.pdf)
* Chinese version: [click here](./My_personal_CV/LiJiatong_Chinese.pdf)

## About my research
### Cognitive diagnosis and its application in intelligent education
The research focuses on the use of deep learning in **cognitive diagnosis**, which is part of an intelligent education system. Given student list and students' performance record (including course video watching record, exam answer record, etc.), I research on how to model students and predict their future performance (i.e. score in exams).

## Awards
* National First Prize in the Contemporary Undergraduate Mathematical Contest in Modeling (CUMCM) **(Top %1)**
  <p align="right"> ——2019.10</p>
* Outstanding Student Scholarship Silver Award
  <p align="right"> ——2019.09</p>
* Outstanding Student Scholarship Silver Award
  <p align="right"> ——2020.09</p>

## Study notes
* Information Theory
* Java

---

[(Back to top)](#welcome-to-jiatong-lis-homepage)

`Pageview =`<span id="{{ post.url }}" class="leancloud_visitors" data-flag-title="{{ post.title }}"> - </span>

<!-- 同时兼容http与https -->
<script src="//cdn1.lncld.net/static/js/2.5.0/av-min.js"></script>
<script>
    // 第一个参数是appid，第二个参数是appkey，此处的只是示例
    AV.initialize("CHAnqLFqbeV3D9vqpG2fOfAq-gzGzoHsz", "1HknQSotpH61q56WMCqFWHEB");
    // 自己创建的Class的名字
    var name='Counter';
    function createRecord(Counter){
      // 设置 ACL
      var acl = new AV.ACL();
      acl.setPublicReadAccess(true);
      acl.setPublicWriteAccess(true);
      // 获得span的所有元素
      var elements=document.getElementsByClassName('leancloud_visitors');
      // 一次创建多条记录
      var allcounter=[];
      for (var i = 0; i < elements.length ; i++) {
        // 若某span的内容不包括 '-' ，则不必创建记录
        if(elements[i].textContent.indexOf('-') == -1){
          continue;
        }
        var title = elements[i].getAttribute('data-flag-title');
        var url = elements[i].id;
        var newcounter = new Counter();
        newcounter.setACL(acl);
        newcounter.set("title", title);
        newcounter.set("url", url);
        newcounter.set("time", 0);
        allcounter.push(newcounter);
        // 顺便更新显示span为默认值0
        elements[i].textContent=0;
      }
      AV.Object.saveAll(allcounter).then(function (todo) {
        // 成功保存记录之后
        console.log('创建记录成功！');
      }, function (error) {
        // 异常错误 
        console.error('创建记录失败: ' + error.message);
      });
    }
    function showCount(Counter){
      // 是否需要创建新纪录的标志（添加一篇新文章）
      var flag=false;
      var query = new AV.Query(name);
      query.greaterThanOrEqualTo('time', 0);
      query.find().then(function (results) {
        // 当获取到的记录为0时置默认值
        if(results.length==0){
          $('.leancloud_visitors').text('-');
          flag=true;
          console.log('返回查询记录为空');
          // 如果获取到空记录就创建新记录
          createRecord(Counter);
          return;
        }
        // 将获取到的数据设置为text
        for (var i = 0; i < results.length; i++) {
          var item = results[i];
          var url = item.get('url');
          var time = item.get('time');
          var element = document.getElementById(url);
          element.textContent = time;
        }
        // 当某个span含有默认值时说明需要创建记录
        if($('.leancloud_visitors').text().indexOf("-") != -1){
          flag=true;
        }
        // 当获取的记录数与span个数不吻合时
        if(results.length != $('.leancloud_visitors').length){
          flag=true;
        }
        if(flag){
          createRecord(Counter);
        }
      }, function (error) {
        console.log('query error:'+error.message);
      });
    }
    $(function() {
      var Counter = AV.Object.extend(name);
      showCount(Counter);
    });
</script>