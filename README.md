# **Web Robot 程序介绍**

 **Web Robot**是一个使用**Electron框架**构建的桌面应用程序。它的主要功能是从用户提供的URL中**提取网页信息**，并**生成YML文件**以及**下载网页图标**。此外，程序还提供了一个功能来将下载的网页图标**转换为指定的图片格式**。

碍于文件大小，源码请自行下载后查看。
**源码路径**：`Web Robot\resources\app`

## 开发初衷

这个程序是我在写基于hexo主题[**hexo-theme-webstack**](https://github.com/HCLonely/hexo-theme-webstack/)的导航栏时，觉得一个一个提取网站信息好麻烦，还得一直f12,所以用chatgpt3.5写了这么一个还算能用的软件。

因为是一个使用Electron框架构建的桌面应用程序，所以软件有点大，后续也不打算搞什么特别好的优化，能用就行。当然，如果有什么好的建议，欢迎大家联系我。

### **下载地址：**

zip免安装压缩包：https://www.123pan.com/s/8DHrVv-C5dxh.html
7z免安装压缩包：https://www.123pan.com/s/8DHrVv-W5dxh.html

## **程序功能**

### 1、**网页信息提取功能**：

   - 用户在应用程序界面中输入一个URL，请确保url是一个**有效**的链接。
   - 程序使用axios和cheerio库从该URL获取网页内容。
   - 从网页内容中提取**网页标题(title)**、**网页图标(icon)**、**链接(url)**和**描述信息(description)**。
   - 如果网页信息，即**yml文件获取失败**，会**自动使用默认浏览器打开网页**。

### **2、YML文件生成功能**：

   - 使用从网页中提取的信息，程序生成一个**YML文件**,**文件名为**一个实时的**时间戳**，在成功生成后**使用默认的代码编辑器自动打开文件**，并**自动打开yml文件所在目录**（暂不支持自定义下载目录）。

   - **YML文件**是一种结构化的文本文件格式，用于存储网页信息，例如标题、URL、图标链接和描述。

   - yml**文件格式**为

     ```yml
     - name: 
       url: 
       img: 
       description: 
     ```

### 3、**网页图标下载功能**：

   - 程序会尝试从网页中提取的图标链接下载网页图标，**下载失败后会继续生成yml文件（如果可以获取到的话）**，**并且使用默认浏览器打开原网页**。
   - 如果图标链接是**有效的且图标格式被程序支持**（如'.jpg', '.jpeg', '.png', '.gif', '.bmp', '.webp', '.ico','.svg'），程序会下载图标文件保存在本地。

### 4、**SVG图标显示功能**：

   - 如果网页图标是SVG格式，程序会直接将SVG代码传递给渲染进程，并在用户界面中显示。

### 5、**网页图标转换功能**：

   - 用户可以在界面中输入要转换的图片格式（png, jpg, jpeg, webp）。
   - 程序使用sharp库将下载的网页图标转换为指定的图片格式，并保存在本地。

### 6、**文件自动删除功能：**

   - **60s自动删除文件**：软件中设定了**yml文件和原始icon图**在下载后**60s自动删除**的功能；而**转换过格式后的icon图**，则在**两分钟后删除**，所以请在倒计时之前保存好相关文件。（暂不支持自定义删除时间的功能）
   - **关闭软件时自动删除**：在关闭软件时，会自动清空`WebRobot\resources\app\files`这个文件夹中的所有文件，这个文件夹也是默认的yml文件、icon图标的默认文件夹，所以请在关闭之前保存好相关文件。（暂不支持自定义下载路径）


## **界面操作**

- 用户在应用程序界面中输入一个URL，并点击"开始"按钮来触发网页信息提取功能。
- 如果网页图标下载成功，程序会在界面中显示图标下载的信息和路径。**默认路径为**：`WebRobot\resources\app\files`
- 用户可以输入一个要转换的图片格式（确保输入软件支持的格式），并点击"转换图片格式"按钮来触发图标转换功能。
- 转换后的图标文件路径和转换成功的信息将在界面中显示。

## **注意事项**

- 如果提取的网页图标链接无效或格式不被支持，程序会显示错误信息，并在点击"开始"按钮后重新尝试提取网页信息。
- 程序会在生成YML文件和转换图标后，自动使用默认程序打开生成的yml文件，并在一定时间后删除这些文件。

## **总结**

Web Robot是一个简单实用的桌面应用程序，可以从用户提供的URL中提取网页信息，并提供了生成YML文件和转换网页图标的功能。它为用户提供了一种方便的方式来保存网页信息和处理网页图标。该程序使用Electron框架，结合Node.js和前端技术，实现了强大的功能，同时提供了友好的用户界面。

