##此项目为gin框架接口练习
#安装golang
配置环境
----------------
##创建数据库
`数据库名blog   编码为utf8_general_ci`
###在数据库下
创建表
####1，标签表
`CREATE TABLE `blog_tag` (
   `id` int(10) unsigned NOT NULL AUTO_INCREMENT,
   `name` varchar(100) DEFAULT '' COMMENT '标签名称',
   `created_on` int(10) unsigned DEFAULT '0' COMMENT '创建时间',
   `created_by` varchar(100) DEFAULT '' COMMENT '创建人',
   `modified_on` int(10) unsigned DEFAULT '0' COMMENT '修改时间',
   `modified_by` varchar(100) DEFAULT '' COMMENT '修改人',
   `state` tinyint(3) unsigned DEFAULT '1' COMMENT '状态 0为禁用、1为启用',
   PRIMARY KEY (`id`)
 ) ENGINE=InnoDB DEFAULT CHARSET=utf8 COMMENT='文章标签管理';`
 ####2,文章表
`CREATE TABLE `blog_article` (
   `id` int(10) unsigned NOT NULL AUTO_INCREMENT,
   `tag_id` int(10) unsigned DEFAULT '0' COMMENT '标签ID',
   `title` varchar(100) DEFAULT '' COMMENT '文章标题',
   `desc` varchar(255) DEFAULT '' COMMENT '简述',
   `content` text,
   `created_on` int(11) DEFAULT NULL,
   `created_by` varchar(100) DEFAULT '' COMMENT '创建人',
   `modified_on` int(10) unsigned DEFAULT '0' COMMENT '修改时间',
   `modified_by` varchar(255) DEFAULT '' COMMENT '修改人',
   `state` tinyint(3) unsigned DEFAULT '1' COMMENT '状态 0为禁用1为启用',
   PRIMARY KEY (`id`)
 ) ENGINE=InnoDB DEFAULT CHARSET=utf8 COMMENT='文章管理';`
 ####3，认证表
 `CREATE TABLE `blog_auth` (
    `id` int(10) unsigned NOT NULL AUTO_INCREMENT,
    `username` varchar(50) DEFAULT '' COMMENT '账号',
    `password` varchar(50) DEFAULT '' COMMENT '密码',
    PRIMARY KEY (`id`)
  ) ENGINE=InnoDB DEFAULT CHARSET=utf8;
  INSERT INTO `blog`.`blog_auth` (`id`, `username`, `password`) VALUES (null, 'test', 'test123456');`
  
##安装govendor
`go get -u github.com/kardianos/govendor`
##安装gin
`go get -u github.com/kardianos/govendor`
##拉取go-ini/ini的依赖包
`go get -u github.com/go-ini/ini`
##拉取com的依赖包
`go get -u github.com/Unknwon/com`
##拉取gorm的依赖包
`go get -u github.com/jinzhu/gorm`
##拉取mysql驱动的依赖包
`go get -u github.com/go-sql-driver/mysql`
##拉取validation的依赖包
`go get -u github.com/astaxie/beego/validation`



#验证功能
用Postman

`PUT：http://127.0.0.1:8000/api/v1/tags/1?name=edit1&state=0&modified_by=edit1，查看code是否返回200

DELETE：http://127.0.0.1:8000/api/v1/tags/1，查看code是否返回200

POST：http://127.0.0.1:8000/api/v1/articles?tag_id=1&title=test1&desc=test-desc&content=test-content&created_by=test-created&state=1

GET：http://127.0.0.1:8000/api/v1/articles

GET：http://127.0.0.1:8000/api/v1/articles/1

PUT：http://127.0.0.1:8000/api/v1/articles/1?tag_id=1&title=test-edit1&desc=test-desc-edit&content=test-content-edit&modified_by=test-created-edit&state=0

DELETE：http://127.0.0.1:8000/api/v1/articles/1
`
