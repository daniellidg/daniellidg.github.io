---
layout: post
title: ȫջ��������ϵͳ(nodejs + vuejs + mongodb)
date: 2019-09-12
tags: [ȫջ]
---

��ƪ���½���������ʹ��nodejs+vuejs�������˲��͡�

��Ҫ�����������ݣ�
1. ����׼��
2. ���ͺ�˹���ϵͳ��admin��
3. ��˷�����Ҫ�ṩadmin��web�˽ӿڣ�
4. ����ǰ��չʾ��web��

### ����׼��
- nodejs
  
    ֱ��ȥ�����������µ��ȶ���ͺã�����Ϊ�������ӣ�    
    https://nodejs.org/en/download/
- vue-cli
    
    ����һ��ǿ��Ĺ������ߣ�ʹ�������Ժܷ���Ĺ���һ��vue����Ŀ�����Ҳ���Ҫ�����webpack���á�����ȫ�ְ�װ��
    ```
    npm install --global vue-cli
    ```
    
- mongodb

    ���Ҫ�õ������ݿ⡣ֱ��ȥ�������ض�Ӧϵͳ�İ汾�ͺã�ע��Ҫ����server�档���ص�ַ��    
    http://downloads.mongodb.com/
    
### ���ͺ�˹���ϵͳ

#### ��Ŀ����
���ȴ���һ��������vue�����Ŀ������ʹ���������    
```
    vue create admin
```
���ڳ��ֵ�һЩѡ�ֱ��ѡ��Ĭ�ϾͿɡ�
�����ú��Ŀ¼�ṹ���£�

![](https://user-gold-cdn.xitu.io/2019/9/11/16d1e124f895fb0c?w=787&h=387&f=png&s=48189)

#### router����
ʹ��vue-cli���Ժܷ���ļ���·�ɣ�
```
vue add router
```

![](https://user-gold-cdn.xitu.io/2019/9/11/16d1e11d85d9e500?w=490&h=64&f=png&s=3696)
ע�⣬Ĭ�ϻ����historyģʽ��Ϊ���Ժ󷽱�Щ������Ҫѡ��(n)����hashģʽ���������������historyģʽ��

#### element-ui����
Ϊ�˷��㣬��˵�ҳ�����ǲ���element-ui�ṩ��һЩ���ʵ�֣�����Ҫ��element-ui���ɽ�����
```
vue add element
```
��ʾѡ�ȫ��ѡ��Ĭ�ϾͿɡ�   

���ˣ���ĿǰΪֹ�������Ŀ�Ļ����ṹ���㹹������ˡ�����ͨ����������������
```
npm run serve
```
�������Ĭ��ҳ�����£�

![](https://user-gold-cdn.xitu.io/2019/9/11/16d1e111a57faf12?w=1351&h=693&f=png&s=59305)

#### ҳ���������
���Բ���element-ui��layout-container��ֱ�Ӱ���������copy�����ŵ�Home.vue ��template����Ϳ��ԡ�
����������һ��Ҫע�⣬�������л����˵���ʱ������ϣ��ֻ���Ҳ��Ǳ䶯�ģ����Ӧ�ñ��ֲ��䣬����������Ҫ�õ�`<router-view>`�����Ҳ�䶯�Ĳ��ֹ��ص�`<router-view>`���
![](https://user-gold-cdn.xitu.io/2019/9/11/16d1e10759a53d0d?w=623&h=325&f=png&s=30664)

### �½�����ҳ��
�����½�һ��CategoryEdit.vue�ļ���Ȼ�����·�ɡ�
·��������Ҫע�⣬�Ҳ�Ŀɱ䶯��ҳ��Ӧ����ΪHome�������·�ɡ�
������CategoryEdit���ҳ������ݾͻ���ʾ������֮ǰ�����`<router-view>`��λ�á�

![](https://user-gold-cdn.xitu.io/2019/9/11/16d1e1d6b28b89ef?w=506&h=177&f=png&s=14487)

���ˣ����������������������"http://localhost:8080/#/categories/create", CategoryEditҳ��ͻ���ʾ�����ˡ������ҳ�����������ﲻ�����ˡ������õ�element-ui�������

����ƪ�����ޣ�������ҳ��������Ҳ����ϸһһ�����ˣ�����Դ���ѿ�Դ��[GitHub](https://github.com/lidaguang1989/myblog)��

���յ���Ŀҳ��ṹ��������������

![](https://user-gold-cdn.xitu.io/2019/9/11/16d1e20b2c2f77dc?w=1356&h=691&f=png&s=50656)

���ֳ������֣�����������¹����û�����

����ҳ����ʹ�õĽӿڣ����ڽ�������server���ֽ��ܡ�

### ��˷���
�ⲿ�ֲ���[nodejs](https://nodejs.org/en/docs/) + [mongodb](https://docs.mongodb.com/)ʵ�֡�

#### ��Ŀ����
1. �����ڸ�Ŀ¼����adminͬ����Ŀ¼���½��ļ���server��
2. �½�һ��package.json�ļ�������ʹ�����������ʼ��һ��
    ```
    npm init
    ```
    ȫ��ѡ��Ĭ�ϼ��ɡ�
3. ������װ�������Ҫ���õ�����������
```
    "cors": "^2.8.5",       // �����������
    "express": "^4.17.1",   // ��˿��
    "mongoose": "^5.6.12",  // ���ݿ�
    "nodemon": "^1.19.2",   // ���ļ��������Զ�������˷���
```
4. ����������װ����½�һ��index.js�ļ���
```
const express = require('express')
const cors = require('cors')
const app = express()

// �������
app.use(cors())
app.use(express.json())

app.listen('3000', async(req, res) => {
  console.log("http://localhost:3000")
})
```
5. ͨ����������Ϳ���������˷����ˣ�
```
    nodemon start index.js
```

#### ·�ɶ���
�½�һ��router�ļ��У�Ȼ���½�admin�ļ�����Ϊadmin�˵Ľӿڣ�ƽ�������ٽ�һ��web�ļ�����Ϊweb�˵Ľӿڡ���admin�ļ������½�index.js�ļ�
```
module.exports = app => {
  const express = require('express')
  const router = express.Router()

  // ��ȡ��Դ
  router.get('/getData', async (req, res) => {
    res.send("hello world")
  })
  
  app.use('/admin/api/rest', router)
}
```
ע�����ﵼ������һ���������������и��ô����ǿ��Դ��ݲ����������������Ǵ�����app��Ϊ������

�ڸ�Ŀ¼��index.js�ļ�����Ҫ����һ�£�
```
require('./routers/admin/index')(app) // ֱ��ִ�к���������app��Ϊ����
```

���������������"http://localhost:3000/admin/api/rest/getData" ʱ���ῴ��"hello wrold"��

#### �������ݿ�
�������½�һ���ļ���db��Ȼ���½�db.js�ļ�:
```
module.exports = app => {
  const mongoose = require('mongoose')

  mongoose.connect('mongodb://localhost:27017/myblog', {
    useNewUrlParser: true
  })
}
```
mongodb��װ���Ĭ�ϻ���27017�˿�������myblog�����Ǹ����ݿ��������    



Ȼ����index.js�ļ�����Ҫ����db.js��
```
require('./db/db')(app) 
```

#### ����ģ��
�½�models�ļ��У����ļ������½�Category.js��Ϊ�����ģ�͡�
```
const mongoose = require('mongoose')

const schema = new mongoose.Schema({
  title: {type: String}
})

module.exports = mongoose.model('Category', schema)
```
��ʱֻ����һ���������� "title"

#### ���ݲ�ѯ
��routers/admin/index.js��ͨ�����´���Ϳ��Բ�ѯcategories���е����ݡ�
```
  // ��ȡ�����б�
  router.get('/categories', async (req, res) => {
    const res = await Category.find()
    res.send(res)
  })
```

��������������� "http://localhost:3000/admin/api/rest/categories" ���ɵõ�categories������ݡ�

���ˣ�ͨ�����ϵĽ��ܣ�����Ӧ���ܹ�ʵ��һЩ�򵥵���ɾ�Ĳ������

#### �м��
�ڿ����Ĺ����У�����һ��������һ�����⡣

ǰ���ᵽ�����admin��Ҫ��������ģ�飺����������¹����û�����

ÿһ��ģ�鶼���漰��ɾ�Ĳ�������������Ϊÿһ��ģ�鶼����һ���Լ�����ɾ�Ĳ�ӿڣ��Ʊػ�����ܶ��ظ����룬��������Ƿ���Ƚ϶��������ظ������������ء�����������Կ����Զ���һ���м����

�����½�һ���ļ���middleware��Ȼ���½�resource.js�ļ������ǿ��԰�ÿ�����඼���Ϊ��Դ����ͳһ����Դ������ɾ�Ĳ������Ψһ�Ĳ�ͬ����Դ���ơ�
```
module.exports = options => {
  return async (req, res, next) => {
    const inflection = require('inflection')
    const modelName = inflection.classify(req.params.resource)
    req.Model = require(`../models/${modelName}`)
  
    next()
  }
}
```
�����õ���inflection�⣬��Ҫ�Ȱ�װһ�£�Ȼ����inflection.classify�Ѵ���Ĳ���תΪ������ʽ����Ϊģ�͵����ơ�

Ȼ��routers/admin.index.js��Ϊ���·�ʽ
```
  // ��ȡ��Դ
  router.get('/', async (req, res) => {
    const data = await req.Model.find()
    res.send(data)
  })

  app.use('/admin/api/rest/:resource', resourceMiddleware(), router)
```

���ˣ�����ƪ�����ޣ�������һЩ���ݾ��ݲ������ˣ���ϸ������Բο�[GitHub](https://github.com/lidaguang1989/myblog)��

### ����ǰ��չʾ��web��
#### ��Ŀ����
�ⲿ�ֺ�admin��࣬�½�web��Ŀ����Ҫ����router��������Ҫelement-ui��������Բ������ĺ�˹���ϵͳ����Ŀ�������ܡ�

#### ����ѡ��
���ⲿ������ֱ�Ӵ�[Jekyll Themes](http://jekyllthemes.org/)�������ѡȡ��һ��������ʱ��û��ô�࣬�ټ������Լ������棬����͵����������������[ԭ���� Liberxue](https://github.com/Liberxue/liberxue.github.io)��

#### ������ͳ��
������ͳ�������õ���һ����ѵĿ�Դ��[������](http://busuanzi.ibruce.info/)���ǳ���������ʹ������Ҳ�ܼ򵥡�

#### ��ҳ��

![](https://user-gold-cdn.xitu.io/2019/9/11/16d1e6fdbe57bddf?w=1366&h=1465&f=png&s=121842)

### ��β
���ˣ���ʱ���Ƚ�����ô��ɣ����кܶ����ݾͲ�һһչ���ˡ������������ʿ������ԡ�

���ڱ�����ǰ�˳�������������ǰ���ˡ����Ҳ�ǸոսӴ����ã���������ǰ�˲��ֽ��ܵĿ��ܻ���һЩ����Ժ�˻��Щ���������Щ����ĵط���ӭָ����

## Դ���Ѿ���Դ��[GitHub](https://github.com/lidaguang1989/myblog), ��������Ŷ��Լ�����Щ������ϣ���ܸ���[Star](https://github.com/lidaguang1989/myblog)��