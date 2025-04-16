# Termux-Python
网络安全实战 30 天练习计划


第一步：先下载字体（只做一次）
在 Termux 执行以下命令：

mkdir -p ~/.fonts

cd ~/.fonts

wget https://github.com/adobe-fonts/source-han-sans/releases/download/2.004R/SourceHanSansSC-Regular.otf


第二步：保存以下代码为 termux_30days_cn.py
nano termux_30days_cn.py

复制下面代码进去（按住屏幕选择“粘贴”）：

from fpdf import FPDF

# 30 天任务列表

tasks = [
   
    ("Day 1", "安装 Python + Termux 设置：熟悉环境，完成 Termux 的更新、Python 安装和基本命令学习。"),
    
    ("Day 2", "IP 地理位置查询工具：使用 requests 模块和公共 API 查询 IP 地址地理信息。"),
    
    ("Day 3", "URL 可用性检测器：检测网址是否可访问，理解 HTTP 状态码。"),
    
    ("Day 4", "自动化网页打开器：模拟自动打开网页的功能，可用于流量测试或网页监控。"),
    
    ("Day 5", "子域名发现器：利用子域名字典爆破目标域名常见子域。"),
    
    ("Day 6", "简易端口扫描器：使用 socket 模块扫描常见端口。"),
    
    ("Day 7", "MAC 地址提取器：学习正则表达式，提取文本中的 MAC 地址格式。"),
    
    ("Day 8", "DNS 记录获取工具：获取目标域名的 A、MX 等记录。"),
    
    ("Day 9", "网站标题抓取器：使用 BeautifulSoup 抓取网页标题和简要信息。"),
    
    ("Day 10", "网站指纹识别（简版）：识别页面中常见技术特征如 jQuery、WordPress。"),
    
    ("Day 11", "nmap 扫描器：调用 nmap 工具扫描目标主机端口。"),
    
    ("Day 12", "HTML 报告生成器：将扫描结果输出为 HTML 文件。"),
    
    ("Day 13", "GitHub 信息抓取器：爬取 GitHub 用户、项目等数据，掌握 requests + bs4 用法。"),
    
    ("Day 14", "代理检测工具：使用第三方 API 检测当前 IP 是否为代理。"),
    
    ("Day 15", "Whois 查询工具：调用 whois 模块或 API 获取域名注册信息。"),
    
    ("Day 16", "参数注入检测器：构造基础的 SQLi 探测逻辑，尝试添加 ' 检查返回结果。"),
    
    ("Day 17", "表单识别器：获取网页中 form 表单结构，为爆破或自动登录做准备。"),
    
    ("Day 18", "Web 目录扫描器：尝试访问常见路径，发现隐藏接口或后台页面。"),

    ("Day 19", "HTTP 抓包器：拦截并打印 HTTP 请求响应头和内容。"),
    
    ("Day 20", "文件上传绕过测试器：模拟文件名后缀绕过、MIME 类型修改。"),
    
    ("Day 21", "Flask 靶场搭建：自己写一个有漏洞的小网站练习攻击与防御。"),
    
    ("Day 22", "XSS 自动测试器：构造脚本自动注入 XSS payload 并检测响应。"),
    
    ("Day 23", "sqlmap 调用器：自动执行 sqlmap 脚本并导出结果。"),
    
    ("Day 24", "WiFi 扫描器：扫描当前环境下的 WiFi 及信号强度（需支持硬件）。"),
    
    ("Day 25", "字典生成器：结合用户信息生成爆破用字典。"),
    
    ("Day 26", "SSH 爆破器：使用 paramiko 模块进行授权测试的 SSH 爆破。"),
    
    ("Day 27", "信息收集一体化脚本：整合 DNS、whois、nmap、网站标题抓取功能。"),
    
    ("Day 28", "漏洞检测流程脚本：加入扫描 + 报告功能，接近实际测试流程。"),
    
    ("Day 29", "红队攻击流程模拟：从信息收集到漏洞利用，模拟真实一次测试。"),
    
    ("Day 30", "总结 + 发布项目：整理你的成果，上传 GitHub，写文档当作作品集。"),
]

class PDF(FPDF):
    def header(self):
        self.set_font("SHS", "", 14)
        self.cell(0, 10, "Termux + Python 网络安全实战 30 天练习计划", ln=True, align="C")
        self.ln(5)

    def chapter(self, title, body):
        self.set_font("SHS", "B", 12)
        self.cell(0, 10, title, ln=True)
        self.set_font("SHS", "", 11)
        self.multi_cell(0, 10, body)
        self.ln()

pdf = PDF()
pdf.add_font("SHS", "", "/data/data/com.termux/files/home/.fonts/SourceHanSansSC-Regular.otf", uni=True)
pdf.set_font("SHS", "", 11)
pdf.add_page()

for title, body in tasks:
    pdf.chapter(title, body)

pdf.output("termux_30day_plan_cn.pdf")


第三步：运行脚本生成 PDF

python termux_30days_cn.py

完成后，你会得到一个名为 termux_30day_plan_cn.pdf 的中文 PDF，支持手机直接打开！
