# menuSystem
## 项目说明
- 用户通过后台页面添加或者删除自定义导航
- 前台页面展示用户的操作结果

## 数据结构示意：

```JavaScript
[{
    level_one:[{//一级导航
        navName:'',//导航名称，**必须字段，不可为空**
        navLink:'',//导航链接，**必须字段，不可为空**
        navId:'',//导航id，删除时的传参，**必须字段，不可为空**
        nav_level:1,//标识导航层级，1为一级导航，2为二级导航，以此类推,**必须字段，不可为空**
        level_two:[{//二级导航，如果没有则为空数组
            navName:'',
            navLink:'',
            navId:'',
            nav_level:2
            level_three:[{
                navName:'',
                navLink:'',
                navId:'',
                nav_level:3
            }]
        }]
      }]
}]
```

1. 可以有多个一级导航，同理二级导航和三级导航也可以有多个
2. 用户可以添加同级导航或者子级导航，最多添加5级，即`nav_level`最大不超过5
3. 用户删除导航时，若改导航存在子级导航，仍可删除，则同时删除该导航下的所有导航
4. 删除子导航时，需要传参父级导航id，以此为关联

#### 服务器配置

- `apache`为苹果自带，所在目录为`/etc/apache3`，在终端使用命令`cd /etc/apache2`即可进入
- 其中配置文件名为`http.conf`
- 将配置文件中的`DocumentRoot`对应的路径改成自己的路径即可。就可以访问修改路径下的文件夹下的文件了
- 终端使用命令`sudo apachectl start`启动apachae服务器
- 终端使用命令`sudo apachectl restart`重启服务器
- 更多请使用`-help`参数查看
