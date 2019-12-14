---
​---

title: hexo静态博客搭建及部署

date: 2019-11-13 00:25:25

categories: 

 - 部署

 - hexo

tag:

 - 部署

 - hexo 
typora-root-url: ./

​---


---



# vscode中使用deploy上传服务器

* 下载插件

  ![1576317902008](/images/1576317902008.png)

*  新建.vscode文件夹， 新建settings.json

```json
// settings.json，，json中不能写注释  这里只是为了记录
{
    "deploy": {
        "packages": [{
            "files": [
                "**/*",
            ],

            "exclude": [  //不包含的文件
                "node_modules/**",
                ".git/**",
                ".vscode/**",
                "**/node_modules/**",
            ],
            "deployOnSave": false  //不自动上传，右键某个文件或文件夹上传，服务器上检查最终确认，相当于scp
        }],
        "targets": [{
            "type": "sftp",
            "name": "AliyunServer",
            "dir": "/source/deploy/test",
            "host": "101.132.98.248",   //设置上传服务器 
            "port": 22,
            "user": "root",
            "privateKey": "C:/Users/ccb/.ssh/id_rsa"// ssh 密钥
        }],
    },
}
```

* 右键deploy上传

  ![1576318564149](/images/1576318564149.png)



# vscode使用git

- vs中的git是本地仓库的管理

- 新建项目后，还是需要使用git clone或git init（需要与远程仓库关联）进行初始化

- 新建**.gitignore**文件，设置不需要git托管的文件,如node_modules

- 文件修改后可以使用vs集成的git图形化按钮,也可以在终端使用git命令

- packagejson中的git仓库配置是程序读取时用到的，不是说就可以直接git push/pull了，如果不是git clone的仓库还是需要关联

- vs git界面

  * 侧边栏第三个按钮是git管理面板，更改==》git add==>暂存更改==》git commit(对勾)，，还有一系列下拉项，，当然直接使用命令也可以

  ![1576318419291](/images/1576318419291.png)

