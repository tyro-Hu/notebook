# 🧩 Python `os` 模块速查笔记

`os` 模块是 Python 的标准库之一，用于与操作系统进行交互。它支持文件与目录操作、路径管理、环境变量访问、系统命令执行等功能。

------

## 📘 一、基础导入

```python
import os
```

------

## 📁 二、文件与目录操作

| 功能             | 方法                                         | 示例                   |
| ---------------- | -------------------------------------------- | ---------------------- |
| 获取当前工作目录 | `os.getcwd()`                                | `print(os.getcwd())`   |
| 切换工作目录     | `os.chdir(path)`                             | `os.chdir("C:/Users")` |
| 列出目录内容     | `os.listdir(path)`                           | `os.listdir(".")`      |
| 创建目录         | `os.mkdir("dir")` / `os.makedirs("a/b/c")`   | 创建单层/多层目录      |
| 删除目录         | `os.rmdir("dir")` / `os.removedirs("a/b/c")` | 删除单层/多层空目录    |
| 删除文件         | `os.remove("file.txt")`                      | 删除文件               |
| 重命名           | `os.rename("old.txt", "new.txt")`            | 文件/目录重命名        |

------

## 🧭 三、路径操作（`os.path`）

| 功能                      | 方法                                           | 示例                |
| ------------------------- | ---------------------------------------------- | ------------------- |
| 拼接路径                  | `os.path.join(a, b)`                           | `"folder/file.txt"` |
| 获取绝对路径              | `os.path.abspath(path)`                        | 绝对路径            |
| 判断是否存在              | `os.path.exists(path)`                         | True / False        |
| 判断文件或目录            | `os.path.isfile(path)` / `os.path.isdir(path)` |                     |
| 拆分路径（目录 + 文件名） | `os.path.split(path)`                          | `('/a/b', 'c.txt')` |
| 拆分扩展名                | `os.path.splitext(path)`                       | `('c', '.txt')`     |
| 获取文件名                | `os.path.basename(path)`                       | `'c.txt'`           |
| 获取目录名                | `os.path.dirname(path)`                        | `'/a/b'`            |

------

## ⚙️ 四、环境变量操作

| 功能         | 方法                             | 示例         |
| ------------ | -------------------------------- | ------------ |
| 获取环境变量 | `os.getenv("PATH")`              | 获取 PATH    |
| 设置环境变量 | `os.environ["MY_VAR"] = "Hello"` | 临时生效     |
| 查看所有变量 | `os.environ`                     | 返回字典对象 |

------

## 💻 五、系统命令执行

| 方法                        | 说明                       | 示例                         |
| --------------------------- | -------------------------- | ---------------------------- |
| `os.system(cmd)`            | 执行系统命令（返回状态码） | `os.system("dir")`           |
| `subprocess.getoutput(cmd)` | 推荐，更安全并返回输出     | `subprocess.getoutput("ls")` |

------

## 🧮 六、系统与进程信息

| 功能             | 方法                          | 示例                                      |
| ---------------- | ----------------------------- | ----------------------------------------- |
| 获取操作系统类型 | `os.name`                     | `'nt'` (Windows), `'posix'` (Linux/macOS) |
| 获取详细系统信息 | `os.uname()`                  | 仅 Linux/macOS                            |
| 获取当前进程号   | `os.getpid()`                 |                                           |
| 修改文件权限     | `os.chmod("file.txt", 0o777)` | 类 Unix 系统使用                          |

------

## 🧠 七、综合示例：批量重命名文件

```python
import os

folder = "./images"
for filename in os.listdir(folder):
    old_path = os.path.join(folder, filename)
    new_path = os.path.join(folder, "img_" + filename)
    os.rename(old_path, new_path)

print("重命名完成！")
```

------

## ✅ 八、常用命令速查表

| 类别     | 常用函数                            | 功能说明           |
| -------- | ----------------------------------- | ------------------ |
| 路径     | `getcwd()` / `chdir()`              | 获取或切换工作目录 |
| 目录     | `mkdir()` / `rmdir()`               | 创建/删除目录      |
| 文件     | `remove()` / `rename()`             | 删除或重命名文件   |
| 判断     | `exists()` / `isfile()` / `isdir()` | 路径存在性判断     |
| 环境变量 | `getenv()` / `environ`              | 获取/设置环境变量  |
| 系统命令 | `system()` / `subprocess`           | 执行命令行         |
| 系统信息 | `os.name` / `os.getpid()`           | 系统及进程信息     |

------

📌 **小贴士**

- 对路径操作推荐使用 `os.path.join()`，避免跨平台分隔符问题。
- 删除、重命名操作要谨慎，可先打印路径确认。
- 若使用 Python 3.4+，也可考虑使用更现代的 [`pathlib`](https://docs.python.org/3/library/pathlib.html) 模块。

