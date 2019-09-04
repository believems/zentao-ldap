
### 简介

这个插件是在 “[禅道开源版LDAP插件](https://github.com/TigerLau1985/ZenTao_LDAP)” 上基础进行的修正，使其可以在 禅道开源版 11.5 上正常运行

测试的 zentao 版本 https://github.com/shynome/zentao-docker , 更新的版本可能不行, 如果有 pr 修复的话会接受的

### FAQ

- 
  - 问：开启这个插件后无法登录本地账户
  - 答：本地账户需要加上 `$` 前缀来登录
- 
  - 问: 连接是 ok 但是同步了 0 位用户
  - 答: 这种情况的话, 保存设置后再点击手动同步就可以正常同步(<del>原来的版本就有的问题懒得改了</del>) 
    <br/>注意: 所有的字段都是需要填写的

### 修改原系统,关闭前端JS传值加密

```shell
vim zbox/app/zentao/module/user/js/login.js
```

```javascript

$('#loginPanel #submit').click(function()
    {
        var password = $('input:password').val().trim();
        var rand = $('input#verifyRand').val();
        // if(password.length != 32 && typeof(md5) == 'function') $('input:password').val(md5(md5(password) + rand));
        if(password.length != 32 && typeof(md5) == 'function') $('input:password').val(password);
    });


```
