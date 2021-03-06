
项目列表
=======================

说明
-----------------------
- 管理项目

1、项目列表、新增项目、批量删除项目 API
-----------------------------------------------

**请求方式：**    GET（查询） POST（新增） DELETE（批量删除）


**请求地址：**    /api/project/project/


**Content-Type：**
::
    新增数据的时候需要指定Content-Type，以下对Content-Type进行说明:

    application/x-www-form-urlencoded —— 表示通过表单方式提交
    application/json —— 表示传入数据为json格式字符串


**查询参数：**

+------------------------+------------+------------+------------------------------------------------+
|**参数**                |**数据类型**|**是否必须**|**说明**                                        |
+------------------------+------------+------------+------------------------------------------------+
| offset                 | int        | 否         | 数据起始位置                                   |
+------------------------+------------+------------+------------------------------------------------+
| limit                  | int        | 否         | 查询条数                                       |
+------------------------+------------+------------+------------------------------------------------+
| name                   | string     | 否         | 项目名称                                       |
+------------------------+------------+------------+------------------------------------------------+
| search                 | string     | 否         | 模糊查询，查询字段为name和description          |
+------------------------+------------+------------+------------------------------------------------+



**输入参数（新增）：**

+------------------------+------------+------------+------------------------------------------------+
|**参数**                |**数据类型**|**是否必须**|**说明**                                        |
+------------------------+------------+------------+------------------------------------------------+
| name                   | string     | 是         | 名称                                           |
+------------------------+------------+------------+------------------------------------------------+
| credential             | int        | 是         | 凭据                                           |
+------------------------+------------+------------+------------------------------------------------+
| description            | string     | 否         | 描述                                           |
+------------------------+------------+------------+------------------------------------------------+
| project_type           | string     | 是         | 项目类型                                       |
+------------------------+------------+------------+------------------------------------------------+
| repository_url         | string     | 是         | 项目地址                                       |
+------------------------+------------+------------+------------------------------------------------+
| branch_specifier       | string     | 是         | 分支/Tag                                       |
+------------------------+------------+------------+------------------------------------------------+
| playbook               | string     | 否         | playbook                                       |
+------------------------+------------+------------+------------------------------------------------+
| revision               | string     | 否         | Revision                                       |
+------------------------+------------+------------+------------------------------------------------+
| project_group          | string     | 是         | 项目组                                         |
+------------------------+------------+------------+------------------------------------------------+
| project_name           | string     | 是         | 项目                                           |
+------------------------+------------+------------+------------------------------------------------+


**输出参数：**

+------------------------+------------+------------+------------------------------------------------+
|**参数**                |**数据类型**|**是否必须**|**说明**                                        |
+------------------------+------------+------------+------------------------------------------------+
| id                     | int        | 是         | project id                                     |
+------------------------+------------+------------+------------------------------------------------+
| name                   | string     | 是         | 名称                                           |
+------------------------+------------+------------+------------------------------------------------+
| credential             | int        | 是         | 凭据                                           |
+------------------------+------------+------------+------------------------------------------------+
| description            | string     | 否         | 描述                                           |
+------------------------+------------+------------+------------------------------------------------+
| project_type           | string     | 是         | 项目类型                                       |
+------------------------+------------+------------+------------------------------------------------+
| repository_url         | string     | 是         | 项目地址                                       |
+------------------------+------------+------------+------------------------------------------------+
| branch_specifier       | string     | 是         | 分支/Tag                                       |
+------------------------+------------+------------+------------------------------------------------+
| playbook               | string     | 否         | playbook                                       |
+------------------------+------------+------------+------------------------------------------------+
| revision               | string     | 否         | Revision                                       |
+------------------------+------------+------------+------------------------------------------------+
| project_group          | string     | 是         | 项目组                                         |
+------------------------+------------+------------+------------------------------------------------+
| project_name           | string     | 是         | 项目                                           |
+------------------------+------------+------------+------------------------------------------------+

**批量删除参数：**

+------------------------+------------+-------------------+-------------------------------------------------+
|**参数**                |**数据类型**|**是否必须**       |**说明**                                         |
+------------------------+------------+-------------------+-------------------------------------------------+
| pk                     | string     | 与pk[]不能都为空  | 主键，多个主键用半角逗号隔开。通过http body传入 |
+------------------------+------------+-------------------+-------------------------------------------------+
| pk[]                   | array      | 与pk不能都为空    | 主键数组。通过http body传入                     |
+------------------------+------------+-------------------+-------------------------------------------------+

**排序：**

+------------------------+------------+-------------------+---------------------------------------------------+
|**参数**                |**数据类型**|**是否必须**       |**说明**                                           |
+------------------------+------------+-------------------+---------------------------------------------------+
|                        |            |                   |   一般默认按id倒叙                                |
| ordering               | string     | 否                | - ordering=id表示按id排序ordering=-id表示按id倒叙 |
|                        |            |                   | - 多个字段排序用半角逗号分隔                      |
+------------------------+------------+-------------------+---------------------------------------------------+

**GET返回数据例子：**
::

    {
        "count": 13,
        "next": null,
        "previous": null,
        "results": [
            {
                "id": 17,
                "name": "tomcat playbook",
                "credential_name": "Git Lab凭据",
                "description": "",
                "project_type": "git",
                "repository_url": "http://101.132.155.111:8090/test/tomcat.git",
                "branch_specifier": "master",
                "playbook": "",
                "credential": 20,
                "revision": "",
                "vault_credential": null,
                "cuser": 48
            },
            {
                "id": 16,
                "name": "创建指定用户",
                "credential_name": "Git Lab凭据",
                "description": "",
                "project_type": "git",
                "repository_url": "http://101.132.155.111:8090/test/user.git",
                "branch_specifier": "master",
                "playbook": "",
                "credential": 20,
                "revision": "",
                "vault_credential": null,
                "cuser": 48
                }
            ]
        }

**新增项目返回数据例子：**
::
    {
        "id": 17,
        "name": "tomcat playbook",
        "credential_name": "Git Lab凭据",
        "description": "",
        "project_type": "git",
        "repository_url": "http://101.132.155.111:8090/test/tomcat.git",
        "branch_specifier": "master",
        "playbook": "",
        "credential": 20,
        "revision": "",
        "vault_credential": null,
        "cuser": 48
    },


2、获取单个项目，修改项目、删除项目 API
-----------------------------------------------

**请求方式：**    GET（查询） PUT（修改） PATCH（修改） DELETE（删除）

**请求地址：**    /api/project/project/1/
::

    请求地址中1为项目的id


**输入/输出参数：**   见章节1中输入和输出参数说明，修改数据时输入参数均为非必须

**返回数据例子：**
::
    {
        "id": 1,
        "name": "自动化测试",
        "description": "",
        "project_type": "git",
        "repository_url": "http://101.132.155.111:8090/test/wordpress-nginx.git",
        "branch_specifier": "master",
        "playbook": "",
        "credential": null,
        "revision": "",
        "vault_credential": null,
        "cuser": 1
    }
