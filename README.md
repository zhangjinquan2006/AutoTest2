# AutoTest2

# 企业员工管理系统 - 自动化测试项目

## 这个项目是干嘛的？
这个项目是我自己写的一套自动化测试代码。
为了测试，我用 Flask 和 MySQL 自己搭了一个简单的“员工管理系统”网页（带管理员登录、添加员工、查看员工列表的功能）。
然后我用 Python 写代码，让程序自动去测接口、查数据库、开浏览器点网页，最后让 GitHub 自动帮我跑这些测试。

## 用了哪些工具？
- 写代码：Python
- 测接口：Requests
- 查数据：PyMySQL
- 测网页：Selenium (用 Edge 浏览器)
- 测试框架：Pytest
- 自动跑测试：GitHub Actions
- 被测网站：Flask + MySQL

## 我具体做了什么？
1. **登录拿 Token**：我先用 Python 模拟管理员登录，拿到 Token（通行证），后面添加员工时都要带着它才能操作。
2. **循环测试多组数据**：我用 Pytest 的参数化功能（数据驱动），一次性传入了“张三”、“李四”等多个员工信息，让程序自动循环去测。
3. **不仅看接口，还要查数据库**：接口返回 200（成功）不代表真存进去了。我写了 PyMySQL 代码直接去 MySQL 里查，确认“张三”是不是真的在表里，防止假成功。
4. **用浏览器自动验证网页**：我用 Selenium 控制 Edge 浏览器自动打开员工列表页面，检查网页上有没有显示刚才添加的“张三”和“李四”。
5. **让 GitHub 帮我自动跑**：我把代码传到了 GitHub。因为云端服务器没有我的本地数据库和浏览器，我加上了跳过（skip）标签和防报错处理，现在只要我提交代码，GitHub 就能自动帮我把测试跑一遍，并显示绿色的成功勾勾。

## 怎么在本地跑起来？
1. 安装工具：`pip install pytest requests pymysql selenium webdriver-manager flask`
2. 启动网站：`python emp_app.py`
3. 跑接口测试：`pytest test_emp_api.py -v`
4. 跑网页测试：`pytest test_emp_ui.py -v`
