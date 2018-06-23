# json-server-mockjs
### 文件结构
```
 project
     |--ajax.html（使用ajax模拟数据请求）
     |--test.json（模拟的接口数据）
     |--mockData（存放使用mockjs的数据）
       |-- news.js
       |-- test.js
     |--ReadMe.md（加个说明性的文件，告诉团队成员框架需要的环境以及用法）
```
### 使用前提
1. 安装nodejs
2. 安装json-server

3. 安装mockjs
   ```
    npm install mockjs --save
   ```
### 启动服务
1. 找到需要作为接口的json数据
   ```
    json-server --watch test.json
   ```
2. 也可以启动多个文件，但是注意一个接口只能启动一个服务
   ```
    json-server --watch mockData/news.js --port 9090
   ```
   * 更多用法，参看笔记：https://github.com/ericyishi/summary/blob/master/frontEnd/nodejs/tools/json-server.md
### 使用
1. 请求posts【这个地方是指帖子posts的意思】接口下的所有数据
```
            $.ajax({
                url: 'http://localhost:9090/posts',
                dataType: 'json',
                type: 'get',
                success: (data) => {
                    console.log(data)
                },
                error: (err) => {
                    console.log(err)
                }
            })
```   
2. 请求posts接口下指定id
```
            $.ajax({
                url: 'http://localhost:9090/posts?id=2',
               dataType: 'json',
                type: 'get',
              success: (data) => {
                    console.log(data)
               },
                error: (err) => {
                    console.log(err)
               }
           })
```
3. 向posts接口下添加数据
```
             $.ajax({
                url: 'http://localhost:9090/posts',
               dataType: 'json',
                type: 'post',
                data: {
                    "id": 4,
                    "title": "i found a secret",
                   "author": "xiaoming"
                },
                success: (data) => {
                    console.log(data)
                },
                error: (err) => {
                    console.log(err)
                }
            })
```
4. 向posts接口下修改数据put方式
```
  $.ajax({
                url: 'http://localhost:9090/posts/2',//注意这里是2，而不是?id=2
                dataType: 'json',
                type: 'put',
                data: {

                    "title": "change content",
                    "authod":"lee"
                },
                success: (data) => {
                    console.log(data)
                },
                error: (err) => {
                    console.log(err)
                }
           })
```
5. 条件查询，以view排序,需要单独开启news的服务
```
            $.ajax({
                url: 'http://localhost:3000/news?_sort=views',
                dataType: 'json',
                type: 'get',
                success: (data) => {
                    console.log(data)
                },
               error: (err) => {
                    console.log(err)
                }
            })
```
### 遗留问题
1. 使用post请求新增数据的时候，会将id数值转化为字符串。应该是json-server服务器这边的问题，待解决。
