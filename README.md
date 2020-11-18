### manifests

visdk repo manager manifests

#### How to match SSH for gitee/github download permissions

https://gitee.com/help/articles/4229#article-header0

+ 在 ~/.ssh 目录下新建一个config文件，添加如下内容:
    Host和HostName填写git服务器的域名;
    IdentityFile指定私钥的路径;
```
    Host gitee.com
    HostName gitee.com
    PreferredAuthentications publickey
    IdentityFile ~/.ssh/gitee_id_rsa

    Host github.com
    HostName github.com
    PreferredAuthentications publickey
    IdentityFile ~/.ssh/github_id_rsa
```
+ 用ssh命令分别测试
```
    $ ssh -T git@gitee.com
    $ ssh -T git@github.com
```

#### How auto store gitee/github private password to pull

https://blog.csdn.net/pengwupeng2008/article/details/107975766

##### 方法1

+ 在~/目录下面新增 .gitconfig 文件
```
    [user]
        email = 978935078@qq.com
        name = Vicent1992
    [credential]
        helper=store
```
+ 执行pull 第一次登入输入用户名，密码

+ 查看~/根目录下，会发现生成了一个 .git-credentials 文件

+ 再一次拉取代码，则不用再输入用户名和密码了

##### 方法2

+ 命令行方式：
```
    1. git config --global credential.helper store
    2. git config --global user.email "你的邮箱"
    3. git config --global user.name "你的github用户名"
    4. git pull
    5. 输入你的用户名、密码，成功后，系统将把你的用户名、密码全局保存
```

#### github pull visdk
```
curl https://mirrors.tuna.tsinghua.edu.cn/git/git-repo -o repo
chmod +x repo
./repo init -u git@github.com:Vicent1992/manifests.git -m github_visdk.xml \
            --repo-url=https://gerrit-googlesource.lug.ustc.edu.cn/git-repo
```

#### gitee pull visdk
```
curl https://mirrors.tuna.tsinghua.edu.cn/git/git-repo -o repo
chmod +x repo
./repo init  -u git@gitee.com:Vicent1992/manifests.git -m gitee_visdk.xml \
             --repo-url=https://gerrit-googlesource.lug.ustc.edu.cn/git-repo
```