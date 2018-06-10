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

### 遗留问题
1. 使用post请求新增数据的时候，会将id数值转化为字符串。应该是json-server服务器这边的问题，待解决。
