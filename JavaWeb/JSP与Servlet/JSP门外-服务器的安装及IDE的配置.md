## Java环境搭建
JDK TomCat MyEclipse

## TomCat安装
1. 解析web项目，作为JSP/Servlet容器  
2. 下载压缩包，环境配置  
3. TomCat服务器目录结构  
`/bin` 控制TomCat的二进制命令文件  
`/conf` 配置文件  
`/lib`  存放服务器相关jar包  
`/logs`  存放日志文件  
`/temp` 存放临时缓存文件  
`/webapps`  当发布Web应用时，默认会将Web应用的文件发布到此目录  
`/work`  将JSP生成的Servlet存放于此，删除并不影响使用  
 
### 样例 
/在webapps中新建项目目录 ——>新建编写index.jsp ——>新建WEB-INF目录 ——>测试  

0. WEB-INF：安全目录，只有服务器端可见
1. 创建web.xml配置文档  项目部署文件，配置了项目的信息
2. 新建clsses文件夹存放字节码文件  
3. lib文件夹存放相关jar包

## MyEclipse配置


* 更改默认JRE
  * window ——> Preferenc ——>Java ——>Installed JRES  
* 更改TomCat默认JDK
  * preference ——> MyEclipse ——> Server ——> TomCat ——> 更改JDK默认

## 更改文件默认编码
1. 打开MyEclipse，windows——>Preferences打开"首选项"对话框。
    * 左侧导航，导航中找到general——>Workspace。
    * 右侧窗口Text file encoding，选择Other，改变为UTF-8，
2. 打开MyEclipse，windows——>Preferences打开"首选项"对话框。
    * 左侧导航，导航到general——>Content Types，
    * 右侧Context Types窗口，点开Text树中每一颗子项，并在中输入"UTF-8"，点“update ”更新。
    * 其它的如：Java properties File、javascript等已经由Eclipse缺省指定分别为ISO8859-1，UTF-8。
    * 如开发中确需改变编码格式则可以在此指定。
3. window——>preference——>MyEclipse——>Files and Editors，
    * 将每个子项的"Encoding"改为"ISO 10645/Unicode（UTF-8）"，点Apply

## 新建web项目
* New web Project并选择相应服务器 项目下目录分别是
* Src                 存放源程序文件
* WebRoot             项目的根目录，在Eclipse下为WebContent
    * META-INF        项目描述的相关文件
    * WEB-INF         web项目的信息目录，同上在服务器/webapps中创建等同效果
* 启动服务器才能查看项目页面

## 修改虚拟路径
* 右键项目 ——> Properties ——> MyEclipse ——> web ——> 修改web Context root ——>重新部署服务器
* 此时可用新的路径名称访问项目，原因在于TomCat服务器中项目文件夹已被更名
