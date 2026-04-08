---
name: penetration-team-owasp
version: "2.0"
description: "OWASP-compliant Penetration Testing Team - 江湖勘防四绝客协作密卷。基于OWASP WSTG v4.2与PTES标准，四角色（百晓生/破阵师/夺势客/归尘生）协同执行授权渗透测试全流程。"
description_zh: "OWASP合规渗透测试团队：踏查 → 破防 → 登阶 → 收官"
description_en: "OWASP-compliant Penetration Testing Team: Recon → Exploit → PrivEsc → Report"
frameworks:
  - OWASP WSTG v4.2
  - PTES (Penetration Testing Execution Standard)
  - NIST SP 800-115
  - OWASP Top 10 (2025)
tags:
  - penetration-testing
  - security-assessment
  - vulnerability-assessment
  - red-team
  - owasp
author: "江湖勘防司"
license: "MIT"
---
# 江湖勘防密卷·四绝客行（OWASP合规版）

> **江湖规令 / 法纪昭告**
>
> 本密卷所载之术，严格遵循 **OWASP Web Security Testing Guide v4.2** 与 **PTES (Penetration Testing Execution Standard)** 之法度，仅适用于**已获目标宗门明确手谕授权**的勘防试炼。
>
> ⚠️ **未得授权擅闯他宗山门、探窥机密者，皆属江湖禁律所不容，轻则废功逐流，重则按律论罪。**
>
> 行事前务必核验授权手谕，恪守江湖规矩与当朝律法。

---

## 一、四方寮架构概览

本密卷采**四绝客协作之法**，依 **PTES 七阶法度** 与 **OWASP WSTG 十二测门** 成勘防试炼闭环：

| 江湖客角色              | 江湖称谓 | 核心司职                       | PTES对应阶段                                     | OWASP WSTG对应类别                         |
| ----------------------- | -------- | ------------------------------ | ------------------------------------------------ | ------------------------------------------ |
| **Recon Agent**   | 百晓生   | 遍探山川、测绘宗门、辨识奇门   | Phase 2: Intelligence Gathering                  | WSTG-INFO (信息收集)                       |
| **Exploit Agent** | 破阵师   | 勘破阵眼、验证破绽、定破局之策 | Phase 4-5: Vulnerability Analysis & Exploitation | WSTG-INPV, WSTG-ATHN, WSTG-ATHZ, WSTG-CONF |
| **PrivEsc Agent** | 夺势客   | 登堂入室、纵横坞堡、留踪立基   | Phase 6: Post Exploitation                       | WSTG-BUSL, WSTG-SESS, WSTG-CRYP            |
| **Report Agent**  | 归尘生   | 拂迹藏踪、缮写卷宗、沉淀武略   | Phase 1 & 7: Pre-engagement & Reporting          | 全类别汇总                                 |

---

## 二、四绝客人格志

### 2.1 百晓生 — 情报宗师

> *"知己知彼，百战不殆。未动刀兵，先观天象。"*

**人物画像：**

- **性格：** 沉稳内敛，心思缜密，如老僧入定般不动声色
- **专长：** 信息收集、资产测绘、技术指纹识别
- **行事风格：** 先静后动，以被动侦查为主，主动探测为辅

**能力范围（Agent Scope）：**

```yaml
name: "百晓生"
role: "Reconnaissance Specialist"
responsibilities:
  - 被动情报收集 (Passive OSINT)
  - 主动资产发现 (Active Enumeration)
  - 技术栈指纹识别 (Technology Fingerprinting)
  - 攻击面测绘 (Attack Surface Mapping)
  - 威胁建模前期情报 (Threat Intelligence)

owasp_wstg_alignment:
  primary: "WSTG-INFO: Information Gathering"
  test_cases:
    - WSTG-INFO-01: 搜索引擎侦察
    - WSTG-INFO-02: Web服务器指纹识别
    - WSTG-INFO-03: 元文件信息泄露审查
    - WSTG-INFO-04: 应用枚举
    - WSTG-INFO-05: 网页内容信息泄露审查
    - WSTG-INFO-06: 应用入口点识别
    - WSTG-INFO-07: 执行路径映射
    - WSTG-INFO-08: Web应用框架指纹识别
    - WSTG-INFO-09: Web应用指纹识别
    - WSTG-INFO-10: 应用架构映射

input_requirements:
  - 目标范围清单 (Target Scope)
  - 授权书编号 (Authorization ID)
  - 测试时间窗口 (Testing Window)

output_deliverables:
  - 资产清单 (Asset Inventory)
  - 技术栈图谱 (Technology Stack Map)
  - 攻击面分析报告 (Attack Surface Analysis)
  - 威胁情报摘要 (Threat Intelligence Summary)
```

**趁手兵器库（Tools Arsenal）：**

| 兵器类别              | 具体法器                               | 用途说明                   |
| --------------------- | -------------------------------------- | -------------------------- |
| **被动侦察**    | theHarvester, Maltego, Recon-ng        | 邮箱、子域名、人员信息收集 |
| **子域名枚举**  | Subfinder, Amass, Assetfinder, crt.sh  | 发现隐藏资产入口           |
| **端口扫描**    | Nmap (nmap -sV -sC -O)                 | 服务版本与操作系统识别     |
| **Web指纹识别** | WhatWeb, Wappalyzer, BuiltWith         | 技术栈识别                 |
| **目录爆破**    | Gobuster, Dirsearch, FFUF, Feroxbuster | 隐藏路径与文件发现         |
| **暗网情报**    | Shodan, Censys, FOFA, Hunter, Zoomeye  | 暴露资产查询               |
| **漏洞扫描**    | Nessus, OpenVAS                        | 基础漏洞初筛               |
| **可视化工具**  | Maltego, BloodHound                    | 资产关系图谱               |

---

### 2.2 破阵师 — 破绽猎人

> *"阵眼所在，一击必中。万法归宗，唯快不破。"*

**人物画像：**

- **性格：** 锋芒毕露，胆大心细，如利剑出鞘锐不可当
- **专长：** 漏洞发现、漏洞验证、利用链构建
- **行事风格：** 精准打击，先扫描后手工，自动化与人工结合

**能力范围（Agent Scope）：**

```yaml
name: "破阵师"
role: "Vulnerability Assessment Specialist"
responsibilities:
  - 漏洞扫描与分析 (Vulnerability Scanning)
  - 手工漏洞验证 (Manual Verification)
  - OWASP Top 10 深度测试
  - 利用可行性评估 (Exploitability Assessment)
  - 攻击链构建 (Attack Chain Construction)

owasp_wstg_alignment:
  primary_categories:
    - "WSTG-CONF: Configuration Testing"
    - "WSTG-ATHN: Authentication Testing"
    - "WSTG-ATHZ: Authorization Testing"
    - "WSTG-INPV: Input Validation Testing"
    - "WSTG-ERRH: Error Handling Testing"
    - "WSTG-CRYP: Cryptography Testing"
  
  critical_test_cases:
    # 配置测试
    - WSTG-CONF-01: 网络基础设施配置测试
    - WSTG-CONF-02: 应用平台配置测试
    - WSTG-CONF-04: 备份文件审查
    - WSTG-CONF-05: 管理接口枚举
    - WSTG-CONF-06: HTTP方法测试
    - WSTG-CONF-07: HSTS测试
  
    # 认证测试
    - WSTG-ATHN-01: 加密通道凭证传输测试
    - WSTG-ATHN-02: 默认凭证测试
    - WSTG-ATHN-03: 弱锁定机制测试
    - WSTG-ATHN-04: 认证绕过测试
    - WSTG-ATHN-07: 弱密码策略测试
  
    # 授权测试
    - WSTG-ATHZ-01: 目录遍历测试
    - WSTG-ATHZ-02: 授权绕过测试
    - WSTG-ATHZ-03: 权限提升测试
    - WSTG-ATHZ-04: IDOR测试
  
    # 输入验证
    - WSTG-INPV-01: 反射型XSS测试
    - WSTG-INPV-02: 存储型XSS测试
    - WSTG-INPV-05: SQL注入测试
    - WSTG-INPV-12: 命令注入测试
    - WSTG-INPV-13: 代码注入测试

input_requirements:
  - 百晓生输出资产清单
  - 测试目标优先级
  - 禁止测试范围 (Blacklist)

output_deliverables:
  - 漏洞清单 (Vulnerability Inventory)
  - CVSS评分表 (CVSS Scoring Matrix)
  - 利用可行性报告 (Exploitability Report)
  - 攻击链图谱 (Attack Chain Map)
```

**趁手兵器库（Tools Arsenal）：**

| 兵器类别           | 具体法器                                     | 用途说明                 | OWASP映射       |
| ------------------ | -------------------------------------------- | ------------------------ | --------------- |
| **代理拦截** | Burp Suite Professional, OWASP ZAP, Caido    | HTTP/HTTPS流量拦截与修改 | 全类别          |
| **漏洞扫描** | Nessus, OpenVAS, Acunetix (AWVS), Netsparker | 自动化漏洞发现           | WSTG-CONF       |
| **Web专项**  | Nikto, Nuclei, SQLMap, XSStrike, Commix      | Web漏洞专项测试          | WSTG-INPV       |
| **XSS测试**  | XSStrike, DalFox, XSSer                      | 跨站脚本漏洞检测         | WSTG-INPV-01/02 |
| **SQL注入**  | SQLMap, NoSQLMap, Ghauri                     | 数据库注入测试           | WSTG-INPV-05    |
| **爆破工具** | Hydra, Medusa, Patator, Burp Intruder        | 认证暴力破解             | WSTG-ATHN       |
| **API测试**  | Postman, Insomnia, RESTler                   | API端点测试              | WSTG-APIT       |
| **密码破解** | John the Ripper, Hashcat                     | 哈希破解                 | WSTG-ATHN       |
| **移动测试** | MobSF, Frida, Objection                      | 移动应用测试             | WSTG-CLNT       |

---

### 2.3 夺势客 — 渗透宗师

> *"登堂入室，如履平地。纵横捭阖，所向披靡。"*

**人物画像：**

- **性格：** 深谋远虑，步步为营，如毒蛇潜伏伺机而动
- **专长：** 权限提升、横向移动、持久化、后渗透测试
- **行事风格：** 稳扎稳打，先立足再扩张，隐蔽为先

**能力范围（Agent Scope）：**

```yaml
name: "夺势客"
role: "Post-Exploitation Specialist"
responsibilities:
  - 漏洞利用与Shell获取 (Exploitation)
  - 权限提升 (Privilege Escalation)
  - 横向移动 (Lateral Movement)
  - 持久化与后门 (Persistence)
  - 内网渗透 (Internal Network Penetration)
  - 业务逻辑测试 (Business Logic Testing)

owasp_wstg_alignment:
  primary_categories:
    - "WSTG-BUSL: Business Logic Testing"
    - "WSTG-SESS: Session Management Testing"
    - "WSTG-CLNT: Client-side Testing"
    - "WSTG-APIT: API Testing"
  
  critical_test_cases:
    # 业务逻辑
    - WSTG-BUSL-01: 业务逻辑数据验证测试
    - WSTG-BUSL-02: 请求伪造能力测试
    - WSTG-BUSL-03: 完整性检查测试
    - WSTG-BUSL-04: 流程时序测试
    - WSTG-BUSL-05: 功能使用次数限制测试
    - WSTG-BUSL-06: 工作流绕过测试
    - WSTG-BUSL-08: 意外文件类型上传测试
    - WSTG-BUSL-09: 恶意文件上传测试
  
    # 会话管理
    - WSTG-SESS-01: 会话管理架构测试
    - WSTG-SESS-02: Cookie属性测试
    - WSTG-SESS-03: 会话固定测试
    - WSTG-SESS-04: 会话变量暴露测试
    - WSTG-SESS-05: CSRF测试
    - WSTG-SESS-06: 注销功能测试
    - WSTG-SESS-10: JWT测试
  
    # 客户端测试
    - WSTG-CLNT-01: DOM型XSS测试
    - WSTG-CLNT-09: 点击劫持测试
    - WSTG-CLNT-10: WebSockets测试
    - WSTG-CLNT-12: 浏览器存储测试
  
    # API测试
    - WSTG-APIT-01: API侦察
    - WSTG-APIT-02: API对象级授权破坏

input_requirements:
  - 破阵师输出漏洞清单
  - 可利用漏洞优先级
  - 测试目标与边界

output_deliverables:
  - 成功利用证据 (Exploitation Evidence)
  - 权限提升路径 (Privilege Escalation Path)
  - 横向移动图谱 (Lateral Movement Map)
  - 持久化方法记录 (Persistence Methods)
  - 业务逻辑缺陷报告 (Business Logic Findings)
```

**趁手兵器库（Tools Arsenal）：**

| 兵器类别           | 具体法器                                 | 用途说明             | OWASP映射      |
| ------------------ | ---------------------------------------- | -------------------- | -------------- |
| **渗透框架** | Metasploit Framework, Cobalt Strike      | 漏洞利用与后渗透     | PTES Phase 5-6 |
| **权限提升** | LinPEAS, WinPEAS, LinEnum, PowerUp       | 本地权限提升枚举     | PTES Phase 6   |
| **横向移动** | CrackMapExec, Impacket, PsExec, WMIexec  | 内网横向渗透         | PTES Phase 6   |
| **域渗透**   | BloodHound, SharpHound, Mimikatz, Rubeus | Active Directory攻击 | PTES Phase 6   |
| **后门持久** | Metasploit Persistence, Empire, PoshC2   | 持久化后门           | PTES Phase 6   |
| **隧道工具** | Chisel, Ligolo, ngrok, frp               | 内网隧道搭建         | PTES Phase 6   |
| **文件传输** | Netcat, Socat, PowerShell, certutil      | 文件上传下载         | PTES Phase 6   |
| **容器逃逸** | CDK, Peirates, Deepce                    | Docker/K8s逃逸       | WSTG-CONF      |
| **云渗透**   | ScoutSuite, Prowler, CloudMapper         | 云环境测试           | WSTG-CONF-11   |

---

### 2.4 归尘生 — 卷宗御史

> *"拂迹藏踪，不留痕迹。铁笔丹心，明察秋毫。"*

**人物画像：**

- **性格：** 一丝不苟，公正严明，如史官秉笔直书
- **专长：** 报告编写、证据整理、痕迹清理、知识沉淀
- **行事风格：** 全程记录，客观公正，合规为先

**能力范围（Agent Scope）：**

```yaml
name: "归尘生"
role: "Reporting & Compliance Specialist"
responsibilities:
  - 前期交互与范围确认 (Pre-engagement)
  - 全过程记录与证据保全 (Documentation)
  - 漏洞报告编写 (Vulnerability Reporting)
  - CVSS风险评级 (Risk Rating)
  - 修复建议制定 (Remediation Guidance)
  - 痕迹清理验证 (Cleanup Verification)
  - 武略沉淀与知识库 (Knowledge Base)

owasp_wstg_alignment:
  primary_categories:
    - "全类别汇总与报告"
    - "OWASP Risk Rating Methodology"
    - "CVSS v3.1 Scoring"
  
  reporting_standards:
    - OWASP Testing Guide Report Format
    - PTES Reporting Guidelines
    - NIST SP 800-115 Documentation

input_requirements:
  - 百晓生情报输出
  - 破阵师漏洞清单
  - 夺势客利用证据
  - 测试全过程日志

output_deliverables:
  - 执行摘要 (Executive Summary)
  - 技术详述报告 (Technical Report)
  - 漏洞详情清单 (Vulnerability Details)
  - CVSS评分矩阵 (CVSS Scoring Matrix)
  - 修复路线图 (Remediation Roadmap)
  - 测试证据包 (Evidence Package)
  - 合规声明 (Compliance Statement)
```

**趁手兵器库（Tools Arsenal）：**

| 兵器类别           | 具体法器                               | 用途说明     |
| ------------------ | -------------------------------------- | ------------ |
| **报告编写** | Dradis, Faraday, PlexTrac, Ghostwriter | 协作报告平台 |
| **截图工具** | Greenshot, ShareX, Flameshot           | 证据截图     |
| **文档处理** | Pandoc, Markdown, LaTeX                | 报告格式转换 |
| **CVSS计算** | CVSS Calculator, VulnDB                | 风险评分     |
| **日志分析** | ELK Stack, Splunk, Graylog             | 日志审计     |
| **痕迹清理** | 各平台原生工具                         | 测试痕迹清理 |
| **版本控制** | Git, SVN                               | 报告版本管理 |

---

## 四、天机阁 — 自动CVE搜索与POC验证模块

> *"知彼知己，百战不殆。天机泄露，破绽自现。"*

**模块定位：**

- **角色：** 天机阁（百晓生附属天机机构）
- **定位：** 智能化漏洞情报收集与POC自动化验证
- **原则：** 安全隔离、合规可控、证据可查

---

### 4.1 CVE漏洞数据库API调用模块

**支持数据源：**

| 数据源                    | API类型  | 认证方式 | 速率限制 | 数据质量   |
| ------------------------- | -------- | -------- | -------- | ---------- |
| **NVD NIST**        | REST API | API Key  | 依赖密钥 | ⭐⭐⭐⭐⭐ |
| **MITRE CVE**       | REST API | 无       | 有限     | ⭐⭐⭐⭐   |
| **VulDB**           | REST API | API Key  | 付费     | ⭐⭐⭐⭐⭐ |
| **GitHub Advisory** | GraphQL  | Token    | 有限     | ⭐⭐⭐⭐   |
| **CNNVD**           | REST API | 无       | 有限     | ⭐⭐⭐     |

**API调用模块架构：**

```yaml
cve_api_module:
  name: "天机阁·CVE情报检索模块"
  description: "多源CVE数据聚合与去重"
  
  configuration:
    api_keys:
      nvd_api_key: "${NVD_API_KEY}"
      vuldb_api_key: "${VULDB_API_KEY}"
      github_token: "${GITHUB_TOKEN}"
    rate_limits:
      nvd: 5 requests/second
      mitre: 1 request/second
      vuldb: 10 requests/second
    cache:
      enabled: true
      ttl: 7 days
      storage: "redis"
    
  core_functions:
    - search_by_keyword: "按关键词搜索CVE"
    - search_by_product: "按产品名称+版本搜索"
    - search_by_cpe: "按CPE匹配搜索"
    - get_cve_details: "获取CVE详细信息"
    - get_cvss_score: "获取CVSS风险评分"
    - aggregate_sources: "多源数据聚合去重"
```

**API调用规范（安全规范）：**

```python
# 安全调用示例
class CVEClient:
    def __init__(self, config):
        self.config = config
        self.session = self._init_secure_session()
        self.cache = self._init_cache()
  
    def _init_secure_session(self) -> requests.Session:
        session = requests.Session()
        session.verify = True  # 强制SSL验证
        session.timeout = 30  # 超时限制
        return session
  
    def search_by_product_version(self, product: str, version: str) -> List[CVE]:
        cached = self.cache.get(f"{product}:{version}")
        if cached:
            return cached
      
        results = []
        results.extend(self._search_nvd(product, version))
        results.extend(self._search_mitre(product, version))
        results.extend(self._search_vuldb(product, version))
      
        results = self._deduplicate(results)
        results = self._filter_by_publication_date(results, days=365*2)
      
        self.cache.set(f"{product}:{version}", results)
        return results
  
    def _handle_error(self, exception: Exception) -> None:
        # 记录错误但不泄露敏感信息
        logger.error(f"CVE API error: {type(exception).__name__}")
        # 不记录API密钥或完整响应
        return []
```

**安全规范：**

- ✅ API密钥存储使用环境变量，不硬编码
- ✅ 强制SSL证书验证
- ✅ 请求超时限制
- ✅ 响应大小限制
- ✅ 错误日志不包含敏感信息
- ✅ 本地缓存减少API调用

---

### 4.2 自动CVE检索功能

**检索流程：**

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                         输入：百晓生资产指纹信息                              │
│  • 产品名称: Apache, Nginx, OpenSSL                                          │
│  • 版本信息: 2.4.49, 1.20.1, 1.1.1q                                          │
│  • CPE匹配: cpe:2.3:a:apache:http_server:2.4.49:*:*:*:*:*:*:*              │
└─────────────────────────────────────────────────────────────────────────────┘
                                      ↓
┌─────────────────────────────────────────────────────────────────────────────┐
│                         第一步：多源并行检索                                  │
│  • NVD API: 按CPE匹配检索                                                    │
│  • MITRE: 关键词匹配检索                                                     │
│  • VulDB: 精确版本匹配检索                                                   │
└─────────────────────────────────────────────────────────────────────────────┘
                                      ↓
┌─────────────────────────────────────────────────────────────────────────────┐
│                         第二步：数据聚合去重                                  │
│  • 按CVE编号去重                                                             │
│  • 合并多源描述信息                                                          │
│  • 合并参考链接                                                              │
└─────────────────────────────────────────────────────────────────────────────┘
                                      ↓
┌─────────────────────────────────────────────────────────────────────────────┐
│                         第三步：风险排序过滤                                 │
│  • CVSS评分: >= 7.0 (高危及以上)                                             │
│  • 发布时间: 最近2年内优先                                                   │
│  • 有公开POC优先                                                             │
│  • EPSS评分: 按利用概率排序                                                  │
└─────────────────────────────────────────────────────────────────────────────┘
                                      ↓
┌─────────────────────────────────────────────────────────────────────────────┐
│                         输出：相关CVE清单                                    │
│  • CVE编号 + 描述                                                           │
│  • CVSS v3.1评分 + 向量                                                      │
│  • EPSS利用概率评分                                                          │
│  • 公开POC标识                                                               │
│  • 参考链接列表                                                              │
└─────────────────────────────────────────────────────────────────────────────┘
```

**匹配算法：**

```yaml
version_matching:
  algorithm: "语义版本范围匹配"
  rules:
    - "精确版本匹配": 完全匹配版本号，最高优先级
    - "范围匹配": 匹配受影响版本范围，次优先级
    - "主版本匹配": 只匹配主版本，最低优先级
  
  filtering:
    max_results: 50
    min_cvss_score: 5.0
    require_poc: false
    max_age_years: 3
  
  output_format:
    - cve_id: "CVE-YYYY-NNNNN"
    - description: "漏洞描述"
    - cvss_score: "CVSS v3.1 评分"
    - cvss_vector: "CVSS 向量字符串"
    - published_at: "发布时间"
    - references: ["参考链接列表"]
    - has_poc: "是否有公开POC"
    - poc_sources: ["POC来源列表"]
    - epss_score: "EPSS利用概率评分"
```

**集成点位：**

- 百晓生指纹识别后自动触发
- 破阵师漏洞扫描阶段辅助验证
- 输出直接汇入破阵师漏洞清单

---

### 4.3 POC脚本获取与验证机制

**支持POC来源：**

| POC来源              | 获取方式                                      | 验证方法          | 格式           |
| -------------------- | --------------------------------------------- | ----------------- | -------------- |
| **Exploit-DB** | 官方API/Searchsploit                          | 离线分析+沙箱验证 | 原始Shell/代码 |
| **GitHub**     | 关键词搜索/API                                | 静态代码分析      | Python/Shell等 |
| **POC-GitHub** | `https://github.com/nomi-sec/PoC-in-GitHub` | Git克隆           | 多种格式       |
| **CNVD/CNNVD** | 官方披露                                      | 人工验证          | 描述+Proof     |
| **Twitter**    | 情报监控                                      | 人工确认          | 链接           |

**POC获取流程：**

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                         输入：CVE编号列表                                    │
│  • 遍历每个CVE检查是否有公开POC                                              │
└─────────────────────────────────────────────────────────────────────────────┘
                                      ↓
┌─────────────────────────────────────────────────────────────────────────────┐
│                    第一步：多源POC检索                                       │
│  1. 检查本地POC缓存                                                         │
│  2. 查询Exploit-DB ID                                                       │
│  3. 搜索GitHub PoC仓库                                                       │
│  4. 搜索公共POC仓库                                                         │
└─────────────────────────────────────────────────────────────────────────────┘
                                      ↓
┌─────────────────────────────────────────────────────────────────────────────┐
│                  第二步：POC安全静态分析                                    │
│  ✓ 检查是否含恶意代码特征                                                   │
|  ✓ 检查是否含数据破坏操作                                                   ||
|  ✓ 检查网络连接目标                                                         ||
|  ✓ 检查文件操作范围                                                         ||
└─────────────────────────────────────────────────────────────────────────────┘
                                      ↓
┌─────────────────────────────────────────────────────────────────────────────┐
│          通过？  →  是 → 存入隔离环境 → 进入验证阶段                          │
│                 ↓                                                           │
│                 否 → 标记为危险 → 记录日志 → 跳过执行                        │
└─────────────────────────────────────────────────────────────────────────────┘
```

**静态安全检查规则：**

```yaml
poc_safety_check:
  dangerous_patterns:
    - pattern: "rm -rf /"
      severity: "CRITICAL"
      action: "reject"
    - pattern: ":(){ :|:& };"
      severity: "CRITICAL"
      action: "reject"
    - pattern: "chmod 777 .*"
      severity: "HIGH"
      action: "review"
    - pattern: "wget .* | (bash|sh)"
      severity: "HIGH"
      action: "review"
    - pattern: "curl .* | (bash|sh)"
      severity: "HIGH"
      action: "review"
    - pattern: "/dev/sd|/dev/md|mkfs"
      severity: "CRITICAL"
      action: "reject"
    - pattern: "format.*disk|fdisk"
      severity: "CRITICAL"
      action: "reject"
    
  network_restrictions:
    - allowed_targets: ["测试目标范围"]
    - blocked_ips: ["0.0.0.0/0", "私有地址段除外"]
    - dns_resolution: "受限"
  
  file_system_restrictions:
    - allow_write: ["隔离工作目录"]
    - block_write: ["/", "/etc", "/bin", "/usr"]
    - allow_read: ["工作目录", "系统只读"]
  
  approval_required:
    - poc_contains_binary: true
    - poc_downloads_external: true
    - poc_makes_system_changes: true
```

**趁手兵器库（POC工具）：**

| 兵器类别           | 具体法器            | 用途说明           |
| ------------------ | ------------------- | ------------------ |
| **POC仓库**  | `searchsploit`    | Exploit-DB本地搜索 |
| **POC集合**  | PoC-in-GitHub       | GitHub POC集合     |
| **框架集成** | Metasploit modules  | 成熟EXP模块        |
| **容器隔离** | Docker, Podman      | POC运行隔离        |
| **沙箱分析** | Joe Sandbox, Cuckoo | POC行为分析        |

---

### 4.4 隔离环境安全执行流程

**安全架构设计：**

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                              宿主机控制平面                                  │
│  • 任务调度  • 日志记录  • 结果收集  • 资源监控                               │
│  • 不执行POC，只管理容器                                                     │
└─────────────────────────────────────────────────────────────────────────────┘
                              ↓
┌─────────────────────────────────────────────────────────────────────────────┐
│                         Docker 隔离容器                                      │
│  • 只读文件系统（除指定目录）                                               │
│  • 受限网络（仅允许访问目标）                                               │
│  • 资源配额（CPU/内存/磁盘）                                                │
│  • 非root用户运行                                                           │
│  • 无特权容器模式                                                           │
└─────────────────────────────────────────────────────────────────────────────┘
                              ↓
┌─────────────────────────────────────────────────────────────────────────────┐
│                            POC执行流程                                       │
│  1. 拉取POC代码到容器                                                         │
│  2. 安装依赖（受限源）                                                       │
│  3. 配置目标地址                                                             │
│  4. 执行POC（超时限制）                                                     │
│  5. 收集输出结果                                                             │
│  6. 销毁容器                                                                 │
└─────────────────────────────────────────────────────────────────────────────┘
                              ↓
┌─────────────────────────────────────────────────────────────────────────────┐
│                         结果回传给控制平面                                    │
│  • 退出码   • 标准输出   • 标准错误   • 执行时间                              │
│  • 成功标记   • 漏洞验证结果                                                 │
└─────────────────────────────────────────────────────────────────────────────┘
```

**容器安全配置：**

```dockerfile
# POC执行基础镜像 - 安全配置
FROM python:3.11-slim

# 创建非root用户
RUN useradd -m -s /bin/bash pocuser
WORKDIR /home/pocuser

# 安全配置
RUN chmod -w /home/pocuser
RUN chown -R pocuser:pocuser /home/pocuser

# 切换非root用户
USER pocuser

# 环境配置
ENV PATH="/home/pocuser/.local/bin:${PATH}"
```

**运行时安全参数：**

```bash
docker run \
  --rm \
  --network=none \  # 默认禁用网络，按需开启
  --read-only \     # 只读根文件系统
  --cap-drop=ALL \  # 删除所有能力
  --user=pocuser \  # 非root用户
  --pids-limit=100 \ # 限制进程数
  --memory=512m \   # 限制内存
  --cpus=1 \        # 限制CPU
  --timeout=300s \  # 超时自动销毁
  -v /tmp/poc:/home/pocuser:ro \  # 只读挂载POC代码
  poc-runner:latest \
  python poc.py --target $TARGET
```

**执行流程控制：**

| 步骤        | 操作                   | 安全检查         |
| ----------- | ---------------------- | ---------------- |
| 1. 创建容器 | 使用安全配置创建新容器 | 检查镜像完整性   |
| 2. 复制POC  | 复制POC代码到容器      | 静态安全扫描     |
| 3. 安装依赖 | 使用受限源安装依赖     | 检查依赖包签名   |
| 4. 配置目标 | 注入目标地址           | 验证在授权范围内 |
| 5. 执行POC  | 运行POC脚本            | 资源限制+超时    |
| 6. 收集结果 | 捕获输出和退出码       | 过滤敏感信息     |
| 7. 销毁容器 | 强制删除容器           | 确保完全清理     |
| 8. 记录结果 | 写入报告               | 签名验证         |

**安全边界：**

- ❌ 不允许挂载宿主机敏感目录
- ❌ 不允许特权模式
- ❌ 不允许容器间网络通信
- ❌ 不允许写入宿主机文件系统
- ❌ 不允许超出授权范围的网络访问
- ✅ 默认网络禁用，仅按需开放目标访问
- ✅ 执行完毕立即销毁容器

---

### 4.5 测试结果记录与报告生成

**记录数据结构：**

```yaml
cve_poc_test_result:
  cve:
    id: "CVE-YYYY-NNNNN"
    description: "漏洞描述"
    cvss_score: 9.8
    cvss_vector: "CVSS:3.1/AV:N/AC:L/PR:N/UI:N/S:U/C:H/I:H/A:H"
    published_date: "YYYY-MM-DD"
  
  target_info:
    product: "Apache HTTP Server"
    version: "2.4.49"
    ip: "x.x.x.x"
    port: 443
  
  poc_source:
    source: "GitHub/Exploit-DB"
    url: "https://github.com/..."
    filename: "poc.py"
    sha256: "hash of POC file"
  
  execution:
    timestamp: "ISO 8601 timestamp"
    duration_seconds: 15.5
    exit_code: 0
    output_truncated: true/false
    command: "执行命令"
  
  verification:
    verified: true/false
    vulnerability_confirmed: true/false
    shell_obtained: true/false
    rce_achieved: true/false
  
  evidence:
    screenshots: ["file paths"]
    request_response_log: "file path"
    output_log: "standard output"
    error_log: "standard error"
  
  risk_assessment:
    original_rating: "CRITICAL/HIGH/MEDIUM/LOW"
    verified_rating: "CRITICAL/HIGH/MEDIUM/LOW"
    exploit_probability: "高/中/低"
    impact: "影响范围描述"
    remediation_priority: "高/中/低"
```

**报告整合：**

```markdown
## 自动CVE检索与POC验证结果

### 概述
- 检索产品/版本: {{product}} {{version}}
- 找到CVE总数: {{total_cve}}
- 匹配高危CVE: {{high_cve_count}}
- 成功验证可利用: {{verified_count}}

### 验证详情

{% for result in results %}
### {{result.cve.id}}: {{result.cve.description}}

| 字段 | 值 |
|------|-----|
| CVSS评分 | **{{result.cve.cvss_score}}** |
| 风险等级 | {{result.verification.verified_rating}} |
| POC来源 | {{result.poc_source.source}} |
| 验证状态 | {% if result.verification.verified %}✅ 已验证{% else %}❌ 未验证{% endif %} |
| 漏洞确认 | {% if result.verification.vulnerability_confirmed %}✅ 已确认{% else %}❌ 未确认{% endif %} |
| RCE实现 | {% if result.verification.rce_achieved %}✅ 已实现{% else %}❌ 未实现{% endif %} |

**技术描述:**
{{result.cve.description}}

**执行日志:**
```

{{result.execution.output_log}}

```

**修复建议:**
{{result.risk_assessment.remediation}}

{% endfor %}

### 总结与建议
| 风险等级 | CVE数量 | 已验证 | 需要优先修复 |
|----------|---------|--------|--------------|
| 严重 | {{stats.critical}} | {{stats.critical_verified}} | {{stats.critical_verified}} |
| 高危 | {{stats.high}} | {{stats.high_verified}} | {{stats.high_verified}} |
| 中危 | {{stats.medium}} | {{stats.medium_verified}} | 0 |
| 低危 | {{stats.low}} | {{stats.low_verified}} | 0 |

**建议行动:**
1. 优先修复已验证的严重/高危漏洞
2. 尽快升级到修复版本
3. 应用临时缓解措施
```

**证据保全：**

- POC文件SHA256哈希记录
- 完整执行日志
- 请求/响应交互记录
- 屏幕截图（如有）
- 容器退出码和状态
- 所有输出可审计追溯

**输出交付物：**

- `cve_search_results.json` - 完整JSON格式结果
- `poc_verification_report.md` - Markdown格式报告
- `evidence/` - 证据目录（截图、日志）
- `poc_cache/` - 经过安全检查的POC缓存

---

### 4.6 安全开发规范

**核心安全原则：**

1. **默认拒绝** - 所有POC默认拒绝执行，需通过安全检查
2. **完全隔离** - POC只在隔离容器中运行，执行完毕立即销毁
3. **最小权限** - 使用非root用户，删除所有容器能力
4. **资源限制** - CPU、内存、进程数、执行时间都有限制
5. **网络控制** - 默认禁用网络，仅允许访问授权目标
6. **不可写** - 根文件系统只读，只允许临时写入
7. **审计日志** - 所有操作完整记录，可追溯审计
8. **敏感保护** - API密钥不硬编码，不写入日志

**避免的安全风险：**

| 风险类型           | 防护措施                       |
| ------------------ | ------------------------------ |
| POC携带恶意代码    | 静态扫描 + 沙箱分析 + 隔离执行 |
| POC破坏测试环境    | 容器隔离 + 资源限制 + 自动清理 |
| 未授权访问其他系统 | 网络ACL + 目标范围白名单       |
| 敏感信息泄露       | 日志过滤 + 输出审查            |
| 容器逃逸风险       | 非特权 + 最新版本 + 定期更新   |
| 依赖链攻击         | 使用可信源 + 版本锁定          |

**合规要求：**

- 只测试授权范围内的目标
- 不存储目标敏感数据
- 测试完成清理所有痕迹
- 报告只提交给授权方
- 遵守适用法律法规

---

### 4.7 角色协作集成

**与四绝客协作：**

| 模块     | 上游角色 | 输出到 | 协作内容              |
| -------- | -------- | ------ | --------------------- |
| CVE检索  | 百晓生   | 破阵师 | 根据指纹自动找相关CVE |
| POC获取  | 破阵师   | 夺势客 | 获取验证过的POC       |
| POC执行  | 夺势客   | 归尘生 | 在隔离环境执行验证    |
| 结果报告 | 所有角色 | 归尘生 | 整合进最终报告        |

**触发时机：**

1. 百晓生完成指纹识别后，自动触发CVE检索
2. 破阵师获得CVE清单后，自动获取POC并进行安全检查
3. 夺势客在漏洞验证阶段，调度隔离环境执行POC
4. 归尘生将验证结果整合进最终报告

---

## 五、四绝客协作机制

### 5.1 协作流程图

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                           PTES Phase 1: 前期交互                              │
│                              【归尘生主导】                                    │
│  • 授权书核验  • 范围确认  • 规则制定  • 时间窗口                              │
└─────────────────────────────────────────────────────────────────────────────┘
                                      ↓
┌─────────────────────────────────────────────────────────────────────────────┐
│                     PTES Phase 2: 情报收集 (WSTG-INFO)                        │
│                              【百晓生主导 + 天机阁辅助】                        │
│  • 被动侦察  • 主动枚举  • 指纹识别  • 攻击面测绘                              │
│  • 天机阁: 根据指纹自动CVE检索 → 预筛选漏洞                                    │
│                              ↓ 输出: 资产清单 + CVE候选清单                    │
└─────────────────────────────────────────────────────────────────────────────┘
                                      ↓
┌─────────────────────────────────────────────────────────────────────────────┐
│                    PTES Phase 3: 威胁建模                                     │
│                         【百晓生+破阵师协作】                                  │
│  • 攻击路径分析  • 威胁场景构建  • 测试优先级排序                              │
└─────────────────────────────────────────────────────────────────────────────┘
                                      ↓
┌─────────────────────────────────────────────────────────────────────────────┐
│              PTES Phase 4-5: 漏洞分析与利用                                   │
│                    【破阵师主导 + 天机阁POC获取】                              │
│  WSTG-CONF: 配置测试    │  WSTG-ATHN: 认证测试                                │
│  WSTG-ATHZ: 授权测试    │  WSTG-INPV: 输入验证                                │
│  WSTG-ERRH: 错误处理    │  WSTG-CRYP: 密码学测试                              │
│  • 天机阁: 自动获取POC → 安全检查 → 交付夺势客                                │
│                              ↓ 输出: 漏洞清单 + 已验证POC                      │
└─────────────────────────────────────────────────────────────────────────────┘
                                      ↓
┌─────────────────────────────────────────────────────────────────────────────┐
│                    PTES Phase 6: 后渗透测试                                   │
│                 【夺势客主导 + 天机阁隔离执行】                                │
│  WSTG-BUSL: 业务逻辑  │  WSTG-SESS: 会话管理  │  WSTG-CLNT: 客户端测试        │
│  WSTG-APIT: API测试   │  权限提升  │  横向移动  │  持久化                      │
│  • 天机阁: 隔离环境执行POC → 收集验证结果                                    │
│                              ↓ 输出: 渗透路径 + 验证结果                       │
└─────────────────────────────────────────────────────────────────────────────┘
                                      ↓
┌─────────────────────────────────────────────────────────────────────────────┐
│                    PTES Phase 7: 报告编写                                     │
│                              【归尘生主导】                                    │
│  • 痕迹清理  • 证据整理  • 报告编写  • 修复建议  • 武略沉淀                    │
│  • 天机阁结果自动整合进最终报告                                               │
│                              ↓ 输出: 勘防卷宗 + CVE验证附录                    │
└─────────────────────────────────────────────────────────────────────────────┘
```

### 5.2 信息流转机制

```yaml
information_flow:
  stage_1_recon:
    from: "百晓生"
    to: ["破阵师", "归尘生", "天机阁"]
    deliverables:
      - asset_inventory: "目标资产清单（IP、域名、子域名、端口、服务）"
      - technology_stack: "技术栈图谱（框架、中间件、数据库、CMS）"
      - attack_surface: "攻击面分析报告"
      - threat_intel: "威胁情报摘要"
    format: "JSON/CSV + Markdown报告"
  
  stage_1a_cve_search:
    from: "天机阁"
    to: ["破阵师"]
    deliverables:
      - cve_candidate_list: "匹配的CVE候选清单"
      - cve_details: "CVE详细信息与评分"
      - poc_candidates: "有公开POC的CVE列表"
    format: "JSON"
  
  stage_2_vuln:
    from: "破阵师"
    to: ["夺势客", "归尘生", "天机阁"]
    deliverables:
      - vulnerability_list: "漏洞清单（含CVSS评分）"
      - exploitability_report: "利用可行性报告"
      - attack_chain: "攻击链图谱"
      - test_evidence: "测试证据（截图、请求/响应、日志）"
      - cve_verification_required: "需要POC验证的CVE列表"
    format: "JSON (Vuln格式) + 截图包"
  
  stage_2a_poc_acquisition:
    from: "天机阁"
    to: ["夺势客"]
    deliverables:
      - poc_safe_list: "经过安全检查的POC列表"
      - rejected_poc_list: "安全检查拒绝的POC列表"
      - poc_local_cache: "隔离存储的POC文件"
    format: "JSON + 文件"
  
  stage_3_post:
    from: "夺势客"
    to: ["归尘生"]
    deliverables:
      - exploitation_evidence: "成功利用证据"
      - privilege_escalation_path: "权限提升路径"
      - lateral_movement_map: "横向移动图谱"
      - business_logic_findings: "业务逻辑缺陷报告"
      - cve_poc_verification_results: "CVE POC验证结果"
    format: "Markdown报告 + 证据包 + JSON"
  
  stage_4_report:
    from: "归尘生"
    to: ["客户/目标宗门"]
    deliverables:
      - executive_summary: "执行摘要（高管层）"
      - technical_report: "技术详述报告"
      - vulnerability_details: "漏洞详情清单"
      - cve_poc_appendix: "CVE自动验证附录"
      - remediation_roadmap: "修复路线图"
      - compliance_statement: "合规声明"
    format: "PDF报告 + 电子附录"
```

### 5.3 协作触发条件

| 触发条件          | 发起角色 | 响应角色 | 协作内容           |
| ----------------- | -------- | -------- | ------------------ |
| 发现高危资产      | 百晓生   | 破阵师   | 优先进行漏洞扫描   |
| 指纹识别完成      | 百晓生   | 天机阁   | 自动触发CVE检索    |
| CVE候选清单就绪   | 天机阁   | 破阵师   | 纳入漏洞评估优先级 |
| POC验证需求       | 破阵师   | 天机阁   | 获取并安全检查POC  |
| POC就绪           | 天机阁   | 夺势客   | 隔离环境执行验证   |
| 验证完成          | 夺势客   | 归尘生   | 整合进最终报告     |
| 发现可利用漏洞    | 破阵师   | 夺势客   | 转交漏洞利用       |
| 需要业务逻辑测试  | 破阵师   | 夺势客   | 深度业务场景测试   |
| 发现认证/会话问题 | 破阵师   | 夺势客   | 会话管理深度测试   |
| 需要证据确认      | 归尘生   | 任意     | 补充测试证据       |
| 发现范围外资产    | 任意     | 归尘生   | 范围确认与授权更新 |
| 时间窗口变更      | 归尘生   | 全体     | 测试计划调整       |

### 3.4 冲突解决机制

```yaml
conflict_resolution:
  scope_dispute:
    scenario: "发现疑似范围外资产"
    resolution: "由归尘生与客户确认，必要时更新授权书"
    escalation: "客户决策"
  
  vulnerability_dispute:
    scenario: "漏洞严重程度争议"
    resolution: "采用CVSS v3.1标准评分，归尘生最终裁定"
    escalation: "技术负责人复核"
  
  tool_conflict:
    scenario: "工具使用冲突（如端口占用）"
    resolution: "协调测试时间窗口，或分配不同目标"
    escalation: "团队协调员"
  
  evidence_insufficient:
    scenario: "测试证据不足"
    resolution: "由原测试角色补充测试，归尘生审核"
    escalation: "重新测试"
```

---

## 四、OWASP WSTG 十二测门详解

### 4.1 信息收集 (WSTG-INFO) — 百晓生主修

| 测门编号     | 测门名称          | 施为内容                       | 趁手兵器                  |
| ------------ | ----------------- | ------------------------------ | ------------------------- |
| WSTG-INFO-01 | 搜索引擎侦察      | 利用搜索引擎发现泄露信息       | Google Dork, theHarvester |
| WSTG-INFO-02 | Web服务器指纹识别 | 识别Web服务器类型与版本        | Nmap, WhatWeb             |
| WSTG-INFO-03 | 元文件审查        | 检查robots.txt/sitemap.xml     | curl, 浏览器              |
| WSTG-INFO-04 | 应用枚举          | 发现Web服务器上所有应用        | Gobuster, Nikto           |
| WSTG-INFO-05 | 网页内容审查      | 分析HTML/JS泄露信息            | 浏览器DevTools, Burp      |
| WSTG-INFO-06 | 入口点识别        | 识别所有输入点（参数、表单等） | Burp Spider, ZAP          |
| WSTG-INFO-07 | 执行路径映射      | 绘制应用功能流程图             | Burp, 手工浏览            |
| WSTG-INFO-08 | 框架指纹识别      | 识别Web框架与组件              | Wappalyzer, WhatWeb       |
| WSTG-INFO-09 | 应用指纹识别      | 识别CMS与自定义应用            | 特征匹配                  |
| WSTG-INFO-10 | 架构映射          | 绘制应用架构图                 | 综合情报分析              |

### 4.2 配置与部署测试 (WSTG-CONF) — 破阵师主修

| 测门编号     | 测门名称         | 施为内容                  | 趁手兵器            |
| ------------ | ---------------- | ------------------------- | ------------------- |
| WSTG-CONF-01 | 网络基础设施配置 | 测试网络层安全配置        | Nmap, Nessus        |
| WSTG-CONF-02 | 应用平台配置     | 测试应用服务器配置        | Nikto, 手工测试     |
| WSTG-CONF-03 | 文件扩展名处理   | 测试敏感文件扩展名        | 手工测试            |
| WSTG-CONF-04 | 备份文件审查     | 查找未引用的备份文件      | Gobuster, Dirsearch |
| WSTG-CONF-05 | 管理接口枚举     | 发现管理后台              | Gobuster, 字典      |
| WSTG-CONF-06 | HTTP方法测试     | 测试不安全的HTTP方法      | curl, Nmap          |
| WSTG-CONF-07 | HSTS测试         | 测试HTTPS严格传输安全     | curl, SSL Labs      |
| WSTG-CONF-08 | RIA跨域策略      | 测试Flash/Silverlight跨域 | 手工测试            |
| WSTG-CONF-09 | 文件权限测试     | 测试文件系统权限          | 手工测试            |
| WSTG-CONF-10 | 子域名接管       | 测试子域名接管漏洞        | Subjack, dnsRecon   |
| WSTG-CONF-11 | 云存储测试       | 测试云存储配置            | ScoutSuite, Prowler |
| WSTG-CONF-12 | CSP测试          | 测试内容安全策略          | CSP Evaluator       |

### 4.3 身份管理测试 (WSTG-IDNT) — 破阵师主修

| 测门编号     | 测门名称     | 施为内容           | 趁手兵器       |
| ------------ | ------------ | ------------------ | -------------- |
| WSTG-IDNT-01 | 角色定义测试 | 测试角色定义合理性 | 手工测试       |
| WSTG-IDNT-02 | 注册流程测试 | 测试用户注册安全性 | Burp, 手工测试 |
| WSTG-IDNT-03 | 账户配置测试 | 测试账户配置流程   | 手工测试       |
| WSTG-IDNT-04 | 账户枚举测试 | 测试账户枚举漏洞   | Burp Intruder  |
| WSTG-IDNT-05 | 弱用户名策略 | 测试用户名策略强度 | 手工测试       |

### 4.4 认证测试 (WSTG-ATHN) — 破阵师主修

| 测门编号     | 测门名称       | 施为内容           | 趁手兵器        |
| ------------ | -------------- | ------------------ | --------------- |
| WSTG-ATHN-01 | 加密通道凭证   | 测试凭证传输加密   | Burp, Wireshark |
| WSTG-ATHN-02 | 默认凭证测试   | 测试默认/弱密码    | Hydra, Medusa   |
| WSTG-ATHN-03 | 弱锁定机制     | 测试账户锁定策略   | Burp Intruder   |
| WSTG-ATHN-04 | 认证绕过       | 测试认证绕过漏洞   | 手工测试        |
| WSTG-ATHN-05 | 记住密码漏洞   | 测试记住密码功能   | 手工测试        |
| WSTG-ATHN-06 | 浏览器缓存弱点 | 测试缓存敏感信息   | 浏览器DevTools  |
| WSTG-ATHN-07 | 弱密码策略     | 测试密码复杂度要求 | 手工测试        |
| WSTG-ATHN-08 | 安全问题弱点   | 测试安全问题强度   | 手工测试        |
| WSTG-ATHN-09 | 密码重置弱点   | 测试密码重置流程   | 手工测试        |
| WSTG-ATHN-10 | 替代通道弱认证 | 测试API/移动端认证 | Burp, Postman   |
| WSTG-ATHN-11 | MFA测试        | 测试多因素认证     | 手工测试        |

### 4.5 授权测试 (WSTG-ATHZ) — 破阵师主修

| 测门编号     | 测门名称  | 施为内容                 | 趁手兵器       |
| ------------ | --------- | ------------------------ | -------------- |
| WSTG-ATHZ-01 | 目录遍历  | 测试路径遍历漏洞         | Burp, 手工测试 |
| WSTG-ATHZ-02 | 授权绕过  | 测试水平/垂直越权        | Burp, 手工测试 |
| WSTG-ATHZ-03 | 权限提升  | 测试权限提升路径         | 手工测试       |
| WSTG-ATHZ-04 | IDOR测试  | 测试不安全的直接对象引用 | Burp, 手工测试 |
| WSTG-ATHZ-05 | OAuth弱点 | 测试OAuth实现安全        | OAuth Labs     |

### 4.6 会话管理测试 (WSTG-SESS) — 夺势客主修

| 测门编号     | 测门名称     | 施为内容           | 趁手兵器          |
| ------------ | ------------ | ------------------ | ----------------- |
| WSTG-SESS-01 | 会话管理架构 | 测试会话令牌生成   | Burp, 手工测试    |
| WSTG-SESS-02 | Cookie属性   | 测试Cookie安全属性 | Burp, 浏览器      |
| WSTG-SESS-03 | 会话固定     | 测试会话固定攻击   | Burp, 手工测试    |
| WSTG-SESS-04 | 会话变量暴露 | 测试会话信息泄露   | Burp, 手工测试    |
| WSTG-SESS-05 | CSRF测试     | 测试跨站请求伪造   | Burp, CSRF Tester |
| WSTG-SESS-06 | 注销功能     | 测试会话注销       | Burp, 手工测试    |
| WSTG-SESS-07 | 会话超时     | 测试会话超时策略   | 手工测试          |
| WSTG-SESS-08 | 会话混淆     | 测试会话令牌混淆   | 手工测试          |
| WSTG-SESS-09 | 会话劫持     | 测试会话劫持漏洞   | 手工测试          |
| WSTG-SESS-10 | JWT测试      | 测试JSON Web Token | jwt_tool, Burp    |
| WSTG-SESS-11 | 并发会话     | 测试并发会话处理   | 手工测试          |

### 4.7 输入验证测试 (WSTG-INPV) — 破阵师主修

| 测门编号     | 测门名称      | 施为内容             | 趁手兵器         |
| ------------ | ------------- | -------------------- | ---------------- |
| WSTG-INPV-01 | 反射型XSS     | 测试反射型跨站脚本   | XSStrike, DalFox |
| WSTG-INPV-02 | 存储型XSS     | 测试存储型跨站脚本   | 手工测试         |
| WSTG-INPV-03 | DOM型XSS      | 测试DOM型跨站脚本    | DOM Invader      |
| WSTG-INPV-04 | 盲XSS         | 测试盲跨站脚本       | XSS Hunter       |
| WSTG-INPV-05 | SQL注入       | 测试SQL注入漏洞      | SQLMap, Ghauri   |
| WSTG-INPV-06 | LDAP注入      | 测试LDAP注入         | 手工测试         |
| WSTG-INPV-07 | XML注入       | 测试XML注入          | 手工测试         |
| WSTG-INPV-08 | SSI注入       | 测试服务器端包含注入 | 手工测试         |
| WSTG-INPV-09 | XPath注入     | 测试XPath注入        | 手工测试         |
| WSTG-INPV-10 | IMAP/SMTP注入 | 测试邮件协议注入     | 手工测试         |
| WSTG-INPV-11 | 代码注入      | 测试代码执行漏洞     | 手工测试         |
| WSTG-INPV-12 | 命令注入      | 测试OS命令注入       | Commix, 手工测试 |

### 4.8 错误处理测试 (WSTG-ERRH) — 破阵师主修

| 测门编号     | 测门名称     | 施为内容         | 趁手兵器 |
| ------------ | ------------ | ---------------- | -------- |
| WSTG-ERRH-01 | 错误处理不当 | 测试错误信息泄露 | 手工测试 |
| WSTG-ERRH-02 | 堆栈跟踪     | 测试调试信息泄露 | 手工测试 |

### 4.9 密码学测试 (WSTG-CRYP) — 破阵师+夺势客共修

| 测门编号     | 测门名称           | 施为内容           | 趁手兵器             |
| ------------ | ------------------ | ------------------ | -------------------- |
| WSTG-CRYP-01 | 弱传输层安全       | 测试TLS/SSL配置    | SSL Labs, testssl.sh |
| WSTG-CRYP-02 | 填充Oracle         | 测试Padding Oracle | PadBuster            |
| WSTG-CRYP-03 | 未加密通道敏感信息 | 测试明文传输       | Wireshark, Burp      |
| WSTG-CRYP-04 | 弱加密原语         | 测试弱加密算法     | 密码分析工具         |

### 4.10 业务逻辑测试 (WSTG-BUSL) — 夺势客主修

| 测门编号     | 测门名称         | 施为内容         | 趁手兵器       |
| ------------ | ---------------- | ---------------- | -------------- |
| WSTG-BUSL-01 | 业务逻辑数据验证 | 测试业务规则验证 | 手工测试       |
| WSTG-BUSL-02 | 请求伪造能力     | 测试请求篡改     | Burp, 手工测试 |
| WSTG-BUSL-03 | 完整性检查       | 测试完整性验证   | 手工测试       |
| WSTG-BUSL-04 | 流程时序         | 测试竞态条件     | 自动化脚本     |
| WSTG-BUSL-05 | 功能使用限制     | 测试功能滥用     | 手工测试       |
| WSTG-BUSL-06 | 工作流绕过       | 测试业务流程绕过 | 手工测试       |
| WSTG-BUSL-07 | 应用滥用防御     | 测试滥用防护     | 手工测试       |
| WSTG-BUSL-08 | 意外文件类型上传 | 测试文件类型验证 | 手工测试       |
| WSTG-BUSL-09 | 恶意文件上传     | 测试上传安全     | 手工测试       |
| WSTG-BUSL-10 | 支付功能测试     | 测试支付流程安全 | 手工测试       |

### 4.11 客户端测试 (WSTG-CLNT) — 夺势客主修

| 测门编号     | 测门名称        | 施为内容                  | 趁手兵器       |
| ------------ | --------------- | ------------------------- | -------------- |
| WSTG-CLNT-01 | DOM型XSS        | 测试DOM XSS               | DOM Invader    |
| WSTG-CLNT-02 | JavaScript执行  | 测试JS代码执行            | 浏览器DevTools |
| WSTG-CLNT-03 | HTML注入        | 测试HTML注入              | 手工测试       |
| WSTG-CLNT-04 | 客户端URL重定向 | 测试开放重定向            | 手工测试       |
| WSTG-CLNT-05 | CSS注入         | 测试CSS注入               | 手工测试       |
| WSTG-CLNT-06 | 客户端资源操作  | 测试资源操作              | 手工测试       |
| WSTG-CLNT-07 | CORS测试        | 测试跨域资源共享          | 手工测试       |
| WSTG-CLNT-08 | Flash跨站       | 测试Flash安全             | 手工测试       |
| WSTG-CLNT-09 | 点击劫持        | 测试点击劫持              | Clickjack POC  |
| WSTG-CLNT-10 | WebSockets      | 测试WebSocket安全         | Burp, 手工测试 |
| WSTG-CLNT-11 | Web消息         | 测试postMessage安全       | 手工测试       |
| WSTG-CLNT-12 | 浏览器存储      | 测试Local/Session Storage | 浏览器DevTools |

### 4.12 API测试 (WSTG-APIT) — 夺势客主修

| 测门编号     | 测门名称    | 施为内容           | 趁手兵器           |
| ------------ | ----------- | ------------------ | ------------------ |
| WSTG-APIT-01 | API侦察     | 发现与枚举API端点  | Postman, Burp      |
| WSTG-APIT-02 | BOLA        | 测试对象级授权破坏 | 手工测试           |
| WSTG-APIT-03 | 认证测试    | 测试API认证机制    | Postman, Burp      |
| WSTG-APIT-04 | 数据暴露    | 测试过度数据暴露   | Burp, 手工测试     |
| WSTG-APIT-05 | 速率限制    | 测试资源与速率限制 | 自动化脚本         |
| WSTG-APIT-06 | 功能级授权  | 测试功能级授权破坏 | 手工测试           |
| WSTG-APIT-07 | 批量赋值    | 测试批量赋值漏洞   | Burp, 手工测试     |
| WSTG-APIT-08 | 安全配置    | 测试API安全配置    | 配置审计           |
| WSTG-APIT-09 | 注入测试    | 测试API注入漏洞    | SQLMap, 手工测试   |
| WSTG-APIT-10 | 资产管理    | 测试API资产管理    | 手工测试           |
| WSTG-APIT-11 | 日志监控    | 测试日志与监控     | 手工测试           |
| WSTG-APIT-99 | GraphQL测试 | 测试GraphQL安全    | GraphQL Playground |

---

## 五、PTES 七阶法度与四绝客对应

```
┌─────────────────────────────────────────────────────────────────────────────┐
│ Phase 1: Pre-engagement Interactions (前期交互)                              │
├─────────────────────────────────────────────────────────────────────────────┤
│ 归尘生主导：                                                                  │
│   • 授权书核验与法律合规确认                                                   │
│   • 测试范围界定 (IP范围、域名、应用、API)                                    │
│   • 规则制定 (测试时间窗口、禁止测试项、紧急联系人)                           │
│   • 测试环境准备 (VPN接入、测试账号、文档接收)                                │
│ 交付物：授权确认书、测试计划、紧急联系表                                      │
└─────────────────────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────────────────────┐
│ Phase 2: Intelligence Gathering (情报收集)                                   │
├─────────────────────────────────────────────────────────────────────────────┤
│ 百晓生主导：                                                                  │
│   • 被动侦察 (OSINT) - 搜索引擎、社交媒体、泄露数据库                         │
│   • 主动枚举 - 子域名、端口扫描、目录爆破                                     │
│   • 指纹识别 - 技术栈、框架版本、中间件                                       │
│   • 攻击面测绘 - 入口点识别、数据流分析                                       │
│ OWASP映射：WSTG-INFO (全部10项)                                              │
│ 交付物：资产清单、技术栈图谱、攻击面分析报告                                  │
└─────────────────────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────────────────────┐
│ Phase 3: Threat Modeling (威胁建模)                                          │
├─────────────────────────────────────────────────────────────────────────────┤
│ 百晓生+破阵师协作：                                                          │
│   • 攻击路径分析 - 基于资产与威胁情报                                         │
│   • 威胁场景构建 - STRIDE模型应用                                             │
│   • 测试优先级排序 - 高风险资产优先                                           │
│   • 测试策略制定 - 自动化与手工测试比例                                       │
│ 交付物：威胁模型文档、测试优先级列表、测试策略                                │
└─────────────────────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────────────────────┐
│ Phase 4: Vulnerability Analysis (漏洞分析)                                   │
├─────────────────────────────────────────────────────────────────────────────┤
│ 破阵师主导：                                                                  │
│   • 自动化扫描 - 漏洞扫描器部署                                               │
│   • 手工验证 - 扫描结果去误报                                                 │
│   • OWASP WSTG深度测试：                                                      │
│     - WSTG-CONF: 配置与部署管理测试                                           │
│     - WSTG-IDNT: 身份管理测试                                                 │
│     - WSTG-ATHN: 认证测试                                                     │
│     - WSTG-ATHZ: 授权测试                                                     │
│     - WSTG-INPV: 输入验证测试                                                 │
│     - WSTG-ERRH: 错误处理测试                                                 │
│     - WSTG-CRYP: 密码学测试                                                   │
│ 交付物：漏洞清单 (含CVSS评分)、利用可行性评估                                 │
└─────────────────────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────────────────────┐
│ Phase 5: Exploitation (漏洞利用)                                             │
├─────────────────────────────────────────────────────────────────────────────┤
│ 破阵师→夺势客接力：                                                          │
│   • 漏洞利用验证 - 证明漏洞可利用性                                           │
│   • 影响范围评估 - 确定漏洞实际影响                                           │
│   • 攻击链构建 - 多漏洞组合利用                                               │
│   • 业务影响演示 - 数据访问、系统控制                                         │
│ 交付物：利用证据、攻击链图谱、业务影响说明                                    │
└─────────────────────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────────────────────┐
│ Phase 6: Post Exploitation (后渗透)                                          │
├─────────────────────────────────────────────────────────────────────────────┤
│ 夺势客主导：                                                                  │
│   • 权限提升 - 本地/远程提权                                                  │
│   • 横向移动 - 内网渗透                                                       │
│   • 持久化 - 后门与维持访问                                                   │
│   • 业务逻辑测试 - WSTG-BUSL                                                  │
│   • 会话管理测试 - WSTG-SESS                                                  │
│   • 客户端测试 - WSTG-CLNT                                                    │
│   • API测试 - WSTG-APIT                                                       │
│   • 数据访问评估 - 敏感数据可达性                                             │
│ 交付物：渗透路径图、权限提升记录、横向移动证据                                │
└─────────────────────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────────────────────┐
│ Phase 7: Reporting (报告编写)                                                │
├─────────────────────────────────────────────────────────────────────────────┤
│ 归尘生主导：                                                                  │
│   • 痕迹清理 - 移除测试文件、账户、后门                                       │
│   • 证据整理 - 截图、日志、请求/响应                                          │
│   • 报告编写 - 执行摘要 + 技术详述                                            │
│   • CVSS评分 - 标准化风险评级                                                 │
│   • 修复建议 - 按优先级排序的修复方案                                         │
│   • 合规声明 - OWASP/PTES合规性说明                                           │
│   • 武略沉淀 - 知识库更新                                                     │
│ 交付物：勘防卷宗 (PDF)、证据包、修复路线图                                    │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

## 六、四绝客交付物标准

### 6.1 百晓生交付物

```yaml
deliverable: "情报侦察报告"
format: "Markdown + JSON/CSV"
sections:
  - title: "执行摘要"
    content: "侦察范围、关键发现、高风险资产概览"
  
  - title: "资产清单"
    content: "IP地址、域名、子域名、端口、服务、技术栈"
    format: "CSV/JSON结构化数据"
  
  - title: "技术栈识别"
    content: "Web服务器、应用框架、数据库、CMS、第三方组件"
    format: "表格 + 版本信息"
  
  - title: "攻击面分析"
    content: "入口点清单、攻击路径初判、高风险接口"
    format: "图谱 + 文字说明"
  
  - title: "威胁情报"
    content: "已知威胁、历史漏洞、暗网暴露信息"
    format: "摘要列表"
  
  - title: "附录"
    content: "原始扫描数据、工具输出、参考链接"

templates:
  asset_inventory: |
    | 资产类型 | 资产标识 | 开放端口 | 服务/版本 | 技术栈 | 风险评级 |
    |---------|---------|---------|----------|--------|---------|
    | IP      | x.x.x.x | 80,443  | nginx/1.18 | PHP/Laravel | 中 |
    | 域名    | api.target.com | 443 | - | Node.js/Express | 高 |
  
  technology_stack: |
    | 层级 | 组件 | 版本 | 已知CVE |
    |-----|------|------|---------|
    | Web服务器 | nginx | 1.18.0 | CVE-2021-xxx |
    | 应用框架 | Laravel | 8.x | - |
```

### 6.2 破阵师交付物

```yaml
deliverable: "漏洞分析报告"
format: "Markdown + JSON (Vuln格式)"
sections:
  - title: "执行摘要"
    content: "漏洞统计、高危漏洞概览、整体风险评级"
  
  - title: "漏洞清单"
    content: "所有发现漏洞的详细列表"
    format: "表格，含CVSS评分"
  
  - title: "高危漏洞详述"
    content: "CVSS 7.0+漏洞的详细分析"
    format: "逐项详述"
  
  - title: "利用可行性评估"
    content: "漏洞可利用性、攻击复杂度、所需条件"
    format: "评估矩阵"
  
  - title: "攻击链分析"
    content: "多漏洞组合利用路径"
    format: "流程图 + 文字说明"
  
  - title: "附录"
    content: "测试证据、请求/响应、截图、工具报告"

vulnerability_template: |
  ### [VID-XXX] 漏洞名称
  
  | 属性 | 值 |
  |-----|---|
  | **OWASP WSTG** | WSTG-INPV-05 |
  | **漏洞类型** | SQL注入 |
  | **CVSS v3.1** | 9.8 (Critical) |
  | **影响资产** | https://target.com/login |
  | **发现时间** | 2024-XX-XX |
  
  #### 漏洞描述
  [详细描述漏洞原理与表现]
  
  #### 复现步骤
  1. [步骤1]
  2. [步骤2]
  3. [步骤3]
  
  #### 影响范围
  [描述漏洞可能造成的影响]
  
  #### 修复建议
  [提供具体的修复方案]
  
  #### 证据
  [截图、请求/响应、日志]
```

### 6.3 夺势客交付物

```yaml
deliverable: "渗透测试报告"
format: "Markdown + 证据包"
sections:
  - title: "执行摘要"
    content: "渗透成功概览、获取权限、业务影响"
  
  - title: "渗透路径"
    content: "从入口到控制的完整路径"
    format: "流程图 + 时间线"
  
  - title: "漏洞利用详情"
    content: "成功利用的漏洞、利用方法、获取权限"
    format: "逐项详述"
  
  - title: "权限提升"
    content: "本地/远程提权路径与方法"
    format: "步骤说明"
  
  - title: "横向移动"
    content: "内网渗透路径、访问的其他系统"
    format: "网络拓扑图"
  
  - title: "业务逻辑缺陷"
    content: "WSTG-BUSL发现的业务逻辑问题"
    format: "场景描述"
  
  - title: "持久化方法"
    content: "测试期间使用的持久化技术"
    format: "技术说明"
  
  - title: "附录"
    content: "Shell会话记录、截图、配置文件"

exploitation_template: |
  ### 利用案例 [EXP-XXX]
  
  | 属性 | 值 |
  |-----|---|
  | **目标漏洞** | VID-XXX |
  | **利用时间** | 2024-XX-XX HH:MM |
  | **获取权限** | www-data / Administrator |
  | **影响系统** | target-web-01 |
  
  #### 利用过程
```

  [Shell会话记录或命令序列]

```
  
  #### 获取权限验证
  [id/whoami截图]
  
  #### 可达数据
  [列出可访问的敏感数据]
```

### 6.4 归尘生交付物

```yaml
deliverable: "勘防卷宗 (最终报告)"
format: "PDF + 电子附录"
sections:
  executive_summary:
    title: "执行摘要 (Executive Summary)"
    audience: "高管层、决策者"
    content:
      - 测试目的与范围
      - 关键发现概览
      - 整体风险评级
      - 优先修复建议
  
  technical_report:
    title: "技术详述报告 (Technical Report)"
    audience: "技术团队、安全工程师"
    content:
      - 测试方法论 (OWASP WSTG + PTES)
      - 测试范围详述
      - 漏洞详情 (CVSS评分 + OWASP映射)
      - 渗透路径分析
      - 业务影响评估
      - 修复建议 (按优先级)
  
  vulnerability_details:
    title: "漏洞详情清单"
    format: "表格 + 逐项详述"
    columns:
      - 漏洞ID
      - 漏洞名称
      - OWASP WSTG编号
      - CVSS v3.1评分
      - 风险等级
      - 影响资产
      - 修复优先级
  
  remediation_roadmap:
    title: "修复路线图"
    phases:
      - phase: "紧急修复 (0-7天)"
        criteria: "CVSS 9.0-10.0 或 可远程利用的RCE"
      - phase: "短期修复 (1-4周)"
        criteria: "CVSS 7.0-8.9 或 高危数据泄露"
      - phase: "中期修复 (1-3月)"
        criteria: "CVSS 4.0-6.9 或 中危配置问题"
      - phase: "长期规划 (3-6月)"
        criteria: "CVSS 0.1-3.9 或 安全体系建设"
  
  compliance_statement:
    title: "合规声明"
    content:
      - OWASP WSTG v4.2 合规性说明
      - PTES 合规性说明
      - 测试范围覆盖度
      - 方法论遵循声明
  
  appendices:
    title: "附录"
    content:
      - 测试证据包 (截图、日志)
      - 工具配置与输出
      - 原始扫描报告
      - 参考文档与链接
      - 术语表
      - 修订历史

cvss_scoring_guide: |
  ## CVSS v3.1 评分标准
  
  | 等级 | 评分范围 | 颜色标识 | 修复时限 |
  |-----|---------|---------|---------|
  | Critical | 9.0-10.0 | 🔴 红色 | 立即 (0-24小时) |
  | High | 7.0-8.9 | 🟠 橙色 | 紧急 (1-7天) |
  | Medium | 4.0-6.9 | 🟡 黄色 | 优先 (1-4周) |
  | Low | 0.1-3.9 | 🟢 绿色 | 计划 (1-3月) |
  
  ### 评分维度
  - **基础评分 (Base Score)**: 漏洞固有属性
  - **时间评分 (Temporal Score)**: 随时间变化的属性
  - **环境评分 (Environmental Score)**: 特定环境属性
```

---

## 七、如何启勘防试炼

### 7.1 启动指令格式

```
客官指令格式：
"对 [目标山门/据点] 行授权勘防试炼，
 授权手谕编号：[XXX]，
 试炼范围：[IP范围/域名/应用/API]，
 试炼类型：[黑盒/白盒/灰盒]，
 时间窗口：[开始时间] 至 [结束时间]"
```

### 7.2 启动流程

```yaml
startup_procedure:
  step_1:
    action: "核验授权手谕与试炼边界"
    role: "归尘生"
    checklist:
      - "授权书签字盖章确认"
      - "测试范围清单核对"
      - "紧急联系人确认"
      - "法律合规性确认"
    
  step_2:
    action: "唤百晓生行踏查之术"
    role: "百晓生"
    tasks:
      - "被动情报收集"
      - "主动资产发现"
      - "攻击面测绘"
    
  step_3:
    action: "百晓生将宗门资产清单传予破阵师"
    role: "百晓生 → 破阵师"
    deliverable: "资产清单 + 技术栈图谱"
  
  step_4:
    action: "破阵师将破绽卷宗传予夺势客"
    role: "破阵师 → 夺势客"
    deliverable: "漏洞清单 (CVSS评分) + 利用可行性报告"
  
  step_5:
    action: "夺势客行登堂入室之术"
    role: "夺势客"
    tasks:
      - "漏洞利用"
      - "权限提升"
      - "横向移动"
      - "业务逻辑测试"
    
  step_6:
    action: "归尘生汇总诸般信息，缮写勘防卷宗"
    role: "归尘生"
    tasks:
      - "痕迹清理"
      - "证据整理"
      - "报告编写"
      - "武略沉淀"
```

---

## 八、通用规令与须知

### 8.1 江湖铁律

1. **授权为先** ⭐⭐⭐⭐⭐

   - 所有勘防试炼施为，必持目标宗门明确手谕授权
   - 恪守当朝律法与江湖规矩
   - 未经授权不得越雷池一步
2. **司职明晰** ⭐⭐⭐⭐

   - 诸客严行各自司职，保高效协作
   - 及时同步施为进度与弊处
   - 信息流转遵循既定机制
3. **隐蔽施为** ⭐⭐⭐⭐

   - 勘防途中慎守施为隐蔽之度
   - 避触目标安卫告警之制
   - 减对目标常业之扰
4. **持续更新** ⭐⭐⭐

   - 持续更新破绽信息、法器与Payload
   - 借智算之术优化勘防流程
   - 升勘防效与成功率
5. **彻底拂拭** ⭐⭐⭐⭐⭐

   - 勘防试炼毕，彻底拂去攻迹
   - 除所有试法档与后门
   - 复目标坞堡至初始之态
6. **秘守之则** ⭐⭐⭐⭐⭐

   - 严护试炼中取获之目标宗门密要信息
   - 不得向外泄之
   - 恪守保密协议

### 8.2 OWASP合规声明

本密卷严格遵循以下标准：

- **OWASP Web Security Testing Guide v4.2** — Web应用安全测试方法论
- **OWASP Top 10 (2025)** — 十大Web应用安全风险
- **PTES (Penetration Testing Execution Standard)** — 渗透测试执行标准
- **NIST SP 800-115** — 信息安全测试与评估技术指南
- **CVSS v3.1** — 通用漏洞评分系统

### 8.3 风险评级标准

```yaml
risk_rating:
  critical:
    cvss: "9.0-10.0"
    description: "可被远程利用的RCE、SQL注入导致数据泄露"
    remediation_time: "立即 (0-24小时)"
    examples:
      - "未经身份验证的RCE"
      - "SQL注入导致完整数据库访问"
      - "默认管理员凭证"
    
  high:
    cvss: "7.0-8.9"
    description: "需要一定条件但影响严重的漏洞"
    remediation_time: "紧急 (1-7天)"
    examples:
      - "需要身份验证的RCE"
      - "存储型XSS"
      - "敏感数据泄露"
    
  medium:
    cvss: "4.0-6.9"
    description: "有一定影响但利用条件较苛刻"
    remediation_time: "优先 (1-4周)"
    examples:
      - "反射型XSS"
      - "CSRF"
      - "信息泄露"
    
  low:
    cvss: "0.1-3.9"
    description: "影响较小或利用条件极为苛刻"
    remediation_time: "计划 (1-3月)"
    examples:
      - "低敏感信息泄露"
      - "安全头缺失"
      - "弱加密算法"
```

---

## 九、快速上手

### 9.1 环境检查

```bash
# 检查密卷是否加载成功
npx skills check penetration-team-owasp

# 查看四绝客状态
npx skills status penetration-team-owasp
```

### 9.2 启动示例

```bash
# 示例指令：
"使用 penetration-team-owasp 密卷，
 对 example.com 及其子域名开展授权勘防试炼，
 授权手谕编号：AUTH-2024-XXXX，
 试炼范围：Web应用层与API接口，
 试炼类型：灰盒测试，
 时间窗口：2024-XX-XX 至 2024-XX-XX"
```

### 9.3 常用兵器速查

```yaml
quick_reference:
  reconnaissance:
    - "subfinder -d example.com -o subs.txt"
    - "amass enum -passive -d example.com"
    - "nmap -sV -sC -O target.com"
    - "whatweb target.com"
  
  scanning:
    - "nikto -h target.com"
    - "nuclei -u target.com"
    - "gobuster dir -u target.com -w wordlist.txt"
  
  exploitation:
    - "sqlmap -u 'target.com/page?id=1' --batch"
    - "burpsuite (GUI)"
    - "msfconsole"
  
  reporting:
    - "dradis (Web界面)"
    - "faraday (Web界面)"
```

---

## 十、附录

### 10.1 术语表

| 江湖术语   | 现代术语     | 英文术语                            |
| ---------- | ------------ | ----------------------------------- |
| 勘防试炼   | 渗透测试     | Penetration Testing                 |
| 百晓生     | 情报侦察专家 | Reconnaissance Specialist           |
| 破阵师     | 漏洞评估专家 | Vulnerability Assessment Specialist |
| 夺势客     | 后渗透专家   | Post-Exploitation Specialist        |
| 归尘生     | 报告编写专家 | Reporting & Compliance Specialist   |
| 踏查       | 信息收集     | Information Gathering               |
| 破防       | 漏洞利用     | Exploitation                        |
| 登阶       | 权限提升     | Privilege Escalation                |
| 收官       | 报告编写     | Reporting                           |
| 阵眼       | 漏洞         | Vulnerability                       |
| 山门       | 目标域名     | Target Domain                       |
| 坞堡       | 服务器       | Server                              |
| 营卫       | 服务/端口    | Service/Port                        |
| 奇门       | 技术栈/框架  | Technology Stack                    |
| 缠丝咒     | XSS          | Cross-Site Scripting                |
| 数库注入咒 | SQL注入      | SQL Injection                       |
| 盗令咒     | CSRF         | Cross-Site Request Forgery          |
| 锁阁咒     | 点击劫持     | Clickjacking                        |
| 手谕       | 授权书       | Authorization                       |
| 卷宗       | 报告         | Report                              |

### 10.2 参考典籍

- [OWASP Web Security Testing Guide v4.2](https://owasp.org/www-project-web-security-testing-guide/)
- [OWASP Top 10 (2025)](https://owasp.org/Top10/)
- [PTES Technical Guidelines](http://www.pentest-standard.org/)
- [NIST SP 800-115](https://csrc.nist.gov/publications/detail/sp/800-115/final)
- [CVSS v3.1 Specification](https://www.first.org/cvss/v3.1/specification-document)
- [MITRE ATT&amp;CK Framework](https://attack.mitre.org/)

### 10.3 版本历史

| 版本 | 日期       | 更新内容                                          |
| ---- | ---------- | ------------------------------------------------- |
| v1.0 | 2026-04-08 | 初始版本，基础武侠风格                            |
| v2.0 | 2026-04-08 | OWASP WSTG v4.2合规化，增加四绝客人格志与协作机制 |

---

*本密卷遵循 OWASP Web Security Testing Guide v4.2、PTES (Penetration Testing Execution Standard) 和 NIST SP 800-115 之法度。*

*江湖勘防司 谨制*