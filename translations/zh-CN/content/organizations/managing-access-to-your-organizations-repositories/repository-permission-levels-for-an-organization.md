---
title: 组织的仓库权限级别
intro: 您可以通过细化权限级别自定义组织中每个仓库的权限，从而为每个用户提供所需的功能和任务权限。
miniTocMaxHeadingLevel: 3
redirect_from:
  - /articles/repository-permission-levels-for-an-organization-early-access-program/
  - /articles/repository-permission-levels-for-an-organization
  - /github/setting-up-and-managing-organizations-and-teams/repository-permission-levels-for-an-organization
versions:
  fpt: '*'
  ghes: '*'
  ghae: '*'
topics:
  - Organizations
  - Teams
shortTitle: 仓库权限
permissions: People with admin permissions can manage individual and team access to an organization-owned repository.
---

## 组织所拥有仓库的权限级别

您可以为组织成员、外部协作者和人员团队提供对组织仓库不同级别的权限。 每个权限级别都会逐步增加对仓库内容和设置的权限。 选择最适合每个人或团队在项目中的角色的权限级别，而不是提供超过其需求的项目权限。

组织仓库从低到高的权限级别分别为：
- **读取**：建议授予要查看或讨论项目的非代码参与者
- **分类**：建议授予需要主动管理议题和拉取请求的参与者，无写入权限
- **写入**：建议授予积极向项目推送的参与者
- **维护**：建议授予需要管理仓库的项目管理者，没有执行敏感或破坏性操作的权限
- **管理员**：建议授予需要完全项目权限的人员，包括执行敏感和破坏性操作，例如管理安全性或删除仓库

组织所有者可以在访问组织的任何仓库时设置适用于组织所有成员的基本权限。 更多信息请参阅“[设置组织的基本权限](/organizations/managing-access-to-your-organizations-repositories/setting-base-permissions-for-an-organization#setting-base-permissions)”。

组织所有者还可以选择进一步限制对整个组织中某些设置和操作的权限。 有关特定设置选项的更多信息，请参阅“[管理组织设置](/articles/managing-organization-settings)”。

除了管理组织范围的设置之外，组织所有者对组织拥有的每个仓库都具有管理员权限。 更多信息请参阅“[组织的权限级别](/articles/permission-levels-for-an-organization)”。

{% warning %}

**警告：**当有人向仓库添加部署密钥时，拥有私钥的任何用户都可以读取或写入仓库（具体取决于密钥设置），即使他们后来从组织中被删除。

{% endwarning %}

## 每个权限级别的仓库权限

{% ifversion fpt %}
Some of the features listed below are limited to organizations using {% data variables.product.prodname_ghe_cloud %}. {% data reusables.enterprise.link-to-ghec-trial %}
{% endif %}

{% ifversion fpt or ghes %}
{% note %}

**注：**使用安全功能所需的仓库权限列于下面的“[安全功能的权限要求](#permission-requirements-for-security-features)”。

{% endnote %}

{% endif %}
| 仓库操作                                                                                                                                                                                                          |  读取   |  分类   |  写入   |  维护   |                       管理员                        |
|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |:-----:|:-----:|:-----:|:-----:|:------------------------------------------------:|
| 从人员或团队的已分配仓库拉取                                                                                                                                                                                                | **X** | **X** | **X** | **X** |                      **X**                       |
| 复刻人员或团队的已分配仓库                                                                                                                                                                                                 | **X** | **X** | **X** | **X** |                      **X**                       |
| 编辑和删除自己的评论                                                                                                                                                                                                    | **X** | **X** | **X** | **X** |                      **X**                       |
| 打开议题                                                                                                                                                                                                          | **X** | **X** | **X** | **X** |                      **X**                       |
| 关闭自己打开的议题                                                                                                                                                                                                     | **X** | **X** | **X** | **X** |                      **X**                       |
| 重新打开自己关闭的议题                                                                                                                                                                                                   | **X** | **X** | **X** | **X** |                      **X**                       |
| 受理议题                                                                                                                                                                                                          | **X** | **X** | **X** | **X** |                      **X**                       |
| 从团队已分配仓库的复刻发送拉取请求                                                                                                                                                                                             | **X** | **X** | **X** | **X** |                      **X**                       |
| 提交拉取请求审查                                                                                                                                                                                                      | **X** | **X** | **X** | **X** |                      **X**                       |
| 查看已发布的版本                                                                                                                                                                                                      | **X** | **X** | **X** | **X** |            **X** |{% ifversion fpt %}
| 查看 [GitHub Actions 工作流程运行](/actions/automating-your-workflow-with-github-actions/managing-a-workflow-run)                                                                                                     | **X** | **X** | **X** | **X** |                **X** 
{% endif %}
| 编辑 wiki                                                                                                                                                                                                       | **X** | **X** | **X** | **X** |            **X** |{% ifversion fpt %}
| [举报滥用或垃圾内容](/communities/maintaining-your-safety-on-github/reporting-abuse-or-spam)                                                                                                                           | **X** | **X** | **X** | **X** |                **X** 
{% endif %}
| 应用/忽略标签                                                                                                                                                                                                       |       | **X** | **X** | **X** |                      **X**                       |
| 创建、编辑、删除标签                                                                                                                                                                                                    |       |       | **X** | **X** |                      **X**                       |
| 关闭、重新打开和分配所有议题与拉取请求                                                                                                                                                                                           |       | **X** | **X** | **X** | **X** |{% ifversion fpt or ghae or ghes > 3.0 %}
| [在拉取请求上启用和禁用自动合并](/github/administering-a-repository/managing-auto-merge-for-pull-requests-in-your-repository)                                                                                                |       |       | **X** | **X** |                **X** 
{% endif %}
| 应用里程碑                                                                                                                                                                                                         |       | **X** | **X** | **X** |                      **X**                       |
| 标记[重复的议题和拉取请求](/articles/about-duplicate-issues-and-pull-requests)                                                                                                                                            |       | **X** | **X** | **X** |                      **X**                       |
| 申请[拉取请求审查](/articles/requesting-a-pull-request-review)                                                                                                                                                        |       | **X** | **X** | **X** |                      **X**                       |
| Merge a [pull request](/github/collaborating-with-pull-requests/incorporating-changes-from-a-pull-request/about-pull-request-merges)                                                                          |       |       | **X** | **X** |                      **X**                       |
| 推送到（写入）人员或团队的已分配仓库                                                                                                                                                                                            |       |       | **X** | **X** |                      **X**                       |
| 编辑和删除任何人对提交、拉取请求和议题的评论                                                                                                                                                                                        |       |       | **X** | **X** |                      **X**                       |
| [隐藏任何人的评论](/communities/moderating-comments-and-conversations/managing-disruptive-comments)                                                                                                                   |       |       | **X** | **X** |                      **X**                       |
| [锁定对话](/communities/moderating-comments-and-conversations/locking-conversations)                                                                                                                              |       |       | **X** | **X** |                      **X**                       |
| 转让议题（更多信息请参阅“[将议题转让给其他仓库](/articles/transferring-an-issue-to-another-repository)”）                                                                                                                            |       |       | **X** | **X** |                      **X**                       |
| [作为仓库的指定代码所有者](/articles/about-code-owners)                                                                                                                                                                   |       |       | **X** | **X** |                      **X**                       |
| [将拉取请求草稿标记为可供审查](/articles/changing-the-stage-of-a-pull-request)                                                                                                                                              |       |       | **X** | **X** |                      **X**                       |
| [将拉取请求转换为草稿](/articles/changing-the-stage-of-a-pull-request)                                                                                                                                                  |       |       | **X** | **X** |                      **X**                       |
| 提交影响拉取请求可合并性的审查                                                                                                                                                                                               |       |       | **X** | **X** |                      **X**                       |
| 对拉取请求[应用建议的更改](/articles/incorporating-feedback-in-your-pull-request)                                                                                                                                         |       |       | **X** | **X** |                      **X**                       |
| 创建[状态检查](/articles/about-status-checks)                                                                                                                                                                       |       |       | **X** | **X** |            **X** |{% ifversion fpt %}
| 创建、编辑、运行、重新运行和取消 [GitHub Actions 工作流程](/actions/automating-your-workflow-with-github-actions/)                                                                                                                |       |       | **X** | **X** |                **X** 
{% endif %}
| 创建和编辑发行版                                                                                                                                                                                                      |       |       | **X** | **X** |                      **X**                       |
| 查看发行版草稿                                                                                                                                                                                                       |       |       | **X** | **X** |                      **X**                       |
| 编辑仓库的说明                                                                                                                                                                                                       |       |       |       | **X** |        **X** |{% ifversion fpt or ghae %}
| [查看和安装包](/packages/publishing-and-managing-packages)                                                                                                                                                          | **X** | **X** | **X** | **X** |                      **X**                       |
| [发布包](/packages/publishing-and-managing-packages/publishing-a-package)                                                                                                                                        |       |       | **X** | **X** |                      **X**                       |
|                                                                                                                                                                                                               |       |       |       |       |                                                  |
| {% ifversion fpt or ghes > 3.0 %}[删除和恢复包](/packages/learn-github-packages/deleting-and-restoring-a-package){% elsif ghes < 3.1 or ghae %}[删除包](/packages/learn-github-packages/deleting-a-package){% endif %} |       |       |       |       |               **X** | {% endif %}
| 管理[主题](/articles/classifying-your-repository-with-topics)                                                                                                                                                     |       |       |       | **X** |                      **X**                       |
| 启用 wiki 和限制 wiki 编辑器                                                                                                                                                                                          |       |       |       | **X** |                      **X**                       |
| 启用项目板                                                                                                                                                                                                         |       |       |       | **X** |                      **X**                       |
| 配置[拉取请求合并](/articles/configuring-pull-request-merges)                                                                                                                                                         |       |       |       | **X** |                      **X**                       |
| 配置[ {% data variables.product.prodname_pages %} 的发布源](/articles/configuring-a-publishing-source-for-github-pages)                                                                                             |       |       |       | **X** |                      **X**                       |
| [推送到受保护分支](/articles/about-protected-branches)                                                                                                                                                                |       |       |       | **X** |                      **X**                       |
| [创建和编辑仓库社交卡](/articles/customizing-your-repositorys-social-media-preview)                                                                                                                                     |       |       |       | **X** |            **X** |{% ifversion fpt %}
| 限制[仓库中的交互](/communities/moderating-comments-and-conversations/limiting-interactions-in-your-repository)                                                                                                       |       |       |       | **X** |                **X** 
{% endif %}
| 删除议题（请参阅“[删除议题](/articles/deleting-an-issue)”）                                                                                                                                                                |       |       |       |       |                      **X**                       |
| 合并受保护分支上的拉取请求（即使没有批准审查）                                                                                                                                                                                       |       |       |       |       |                      **X**                       |
| [定义仓库的代码所有者](/articles/about-code-owners)                                                                                                                                                                     |       |       |       |       |                      **X**                       |
| 将仓库添加到团队（详细信息请参阅“[管理团队对组织仓库的访问](/organizations/managing-access-to-your-organizations-repositories/managing-team-access-to-an-organization-repository#giving-a-team-access-to-a-repository)”）                  |       |       |       |       |                      **X**                       |
| [管理外部协作者对仓库的权限](/articles/adding-outside-collaborators-to-repositories-in-your-organization)                                                                                                                  |       |       |       |       |                      **X**                       |
| [更改仓库的可见性](/articles/restricting-repository-visibility-changes-in-your-organization)                                                                                                                          |       |       |       |       |                      **X**                       |
| 将仓库设为模板（请参阅“[创建模板仓库](/articles/creating-a-template-repository)”）                                                                                                                                              |       |       |       |       |                      **X**                       |
| 更改仓库设置                                                                                                                                                                                                        |       |       |       |       |                      **X**                       |
| 管理团队和协作者对仓库的权限                                                                                                                                                                                                |       |       |       |       |                      **X**                       |
| 编辑仓库的默认分支                                                                                                                                                                                                     |       |       |       |       |     **X** |{% ifversion fpt or ghes > 3.0 %}
| 重命名仓库的默认分支（请参阅“[重命名分支](/github/administering-a-repository/renaming-a-branch)”）                                                                                                                                |       |       |       |       |                      **X**                       |
| 重命名仓库默认分支以外的分支（请参阅“[重命名分支](/github/administering-a-repository/renaming-a-branch)”）                                                                                                                            |       |       | **X** | **X** |                **X** 
{% endif %}
| 管理 web 挂钩和部署密钥                                                                                                                                                                                                |       |       |       |       |            **X** |{% ifversion fpt %}
| [管理私有仓库的数据使用设置](/github/understanding-how-github-uses-and-protects-your-data/managing-data-use-settings-for-your-private-repository)                                                                          |       |       |       |       |                **X** 
{% endif %}
| [管理仓库的复刻策略](/github/administering-a-repository/managing-the-forking-policy-for-your-repository)                                                                                                               |       |       |       |       |                      **X**                       |
| [将仓库转让给组织](/articles/restricting-repository-creation-in-your-organization)                                                                                                                                    |       |       |       |       |                      **X**                       |
| [删除仓库或将仓库转让到组织外部](/articles/setting-permissions-for-deleting-or-transferring-repositories)                                                                                                                    |       |       |       |       |                      **X**                       |
| [存档仓库](/articles/about-archiving-repositories)                                                                                                                                                                |       |       |       |       |            **X** |{% ifversion fpt %}
| 显示赞助按钮（请参阅“[在仓库中显示赞助按钮](/articles/displaying-a-sponsor-button-in-your-repository)”）。                                                                                                                          |       |       |       |       |                **X** 
{% endif %}
| 创建到外部资源的自动链接引用，如 JIRA 或 Zendesk（请参阅“[配置自动链接以引用外部资源](/articles/configuring-autolinks-to-reference-external-resources)”）                                                                                        |       |       |       |       |            **X** |{% ifversion fpt %}
| 在仓库中[启用 {% data variables.product.prodname_discussions %}](/github/administering-a-repository/enabling-or-disabling-github-discussions-for-a-repository)                                                      |       |       |       | **X** |                      **X**                       |
| 为 {% data variables.product.prodname_discussions %} [创建和编辑类别](/discussions/managing-discussions-for-your-community/managing-categories-for-discussions-in-your-repository)                                    |       |       |       | **X** |                      **X**                       |
| [将讨论移动到其他类别](/discussions/managing-discussions-for-your-community/managing-discussions-in-your-repository)                                                                                                    |       |       | **X** | **X** |                      **X**                       |
| [将讨论转移到](/discussions/managing-discussions-for-your-community/managing-discussions-in-your-repository)新仓库                                                                                                     |       |       | **X** | **X** |                      **X**                       |
| [管理置顶的讨论](/discussions/managing-discussions-for-your-community/managing-discussions-in-your-repository)                                                                                                       |       |       | **X** | **X** |                      **X**                       |
| [批量将议题转换为讨论](/discussions/managing-discussions-for-your-community/managing-discussions-in-your-repository)                                                                                                    |       |       | **X** | **X** |                      **X**                       |
| [锁定和解锁讨论](/discussions/managing-discussions-for-your-community/moderating-discussions)                                                                                                                        |       | **X** | **X** | **X** |                      **X**                       |
| [单独将议题转换为讨论](/discussions/managing-discussions-for-your-community/moderating-discussions)                                                                                                                     |       | **X** | **X** | **X** |                      **X**                       |
| [创建新的讨论并对现有讨论发表评论](/discussions/collaborating-with-your-community-using-discussions/participating-in-a-discussion)                                                                                            | **X** | **X** | **X** | **X** |                      **X**                       |
| [删除讨论](/discussions/managing-discussions-for-your-community/managing-discussions-in-your-repository#deleting-a-discussion)                                                                                    |       |       |       | **X** |      **X** |{% endif %}{% ifversion fpt %}
| 创建 [codespaces](/codespaces/about-codespaces)                                                                                                                                                                 |       |       | **X** | **X** |                **X** 
{% endif %}

### 安全功能的权限要求

在本节中，您可以找到一些安全功能所需的仓库权限级别，例如 {% data variables.product.prodname_advanced_security %} 功能。

| 仓库操作                                                                                                                                                                                                               |  读取   |  分类   |         写入          |         维护          |                                       管理员                                        |
|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |:-----:|:-----:|:-------------------:|:-------------------:|:--------------------------------------------------------------------------------:|
| {% ifversion fpt or ghes > 2.22 %}                                                                                                                                                                                 |       |       |                     |                     |                                                                                  |
| 接收仓库中[易受攻击的依赖项的 {% data variables.product.prodname_dependabot_alerts %}](/code-security/supply-chain-security/about-alerts-for-vulnerable-dependencies)                                                          |       |       |                     |                     |                                      **X**                                       |
| [忽略 {% data variables.product.prodname_dependabot_alerts %}](/code-security/supply-chain-security/viewing-and-updating-vulnerable-dependencies-in-your-repository)                                               |       |       |                     |                     |                                      **X**                                       |
| [指定其他人员或团队接收易受攻击依赖项的 {% data variables.product.prodname_dependabot_alerts %}](/github/administering-a-repository/managing-security-and-analysis-settings-for-your-repository#granting-access-to-security-alerts) |       |       |                     |                     |                      **X** |{% endif %}{% ifversion fpt %}
| 创建[安全通告](/code-security/security-advisories/about-github-security-advisories)                                                                                                                                      |       |       |                     |                     |           **X** |{% endif %}{% ifversion fpt or ghes > 2.22 or ghae %}
| 管理 {% data variables.product.prodname_GH_advanced_security %} 功能的访问权限（请参阅“[管理组织的安全和分析设置](/organizations/keeping-your-organization-secure/managing-security-and-analysis-settings-for-your-organization)”）        |       |       |                     |                     | **X** |{% endif %}{% ifversion fpt %}<!--Set at site-level for GHES-->
|
| 为私有仓库[启用依赖关系图](/code-security/supply-chain-security/exploring-the-dependencies-of-a-repository)                                                                                                                    |       |       |                     |                     |               **X** |{% endif %}{% ifversion fpt or ghes > 3.1 %}
| [查看依赖项审查](/code-security/supply-chain-security/about-dependency-review)                                                                                                                                            | **X** | **X** |        **X**        |        **X**        |                                **X** 
{% endif %}
| [查看拉取请求上的 {% data variables.product.prodname_code_scanning %} 警报](/github/finding-security-vulnerabilities-and-errors-in-your-code/triaging-code-scanning-alerts-in-pull-requests)                               | **X** | **X** |        **X**        |        **X**        |                                      **X**                                       |
| [列出、忽略和删除 {% data variables.product.prodname_code_scanning %} 警报](/github/finding-security-vulnerabilities-and-errors-in-your-code/managing-code-scanning-alerts-for-your-repository)                            |       |       |        **X**        |        **X**        |              **X** |{% ifversion fpt or ghes > 3.0 or ghae-next %}
| [查看仓库中的 {% data variables.product.prodname_secret_scanning %} 警报](/github/administering-a-repository/managing-alerts-from-secret-scanning)                                                                       |       |       | **X**<sup>[1]</sup> | **X**<sup>[1]</sup> |                                      **X**                                       |
| [解决、撤销或重新打开 {% data variables.product.prodname_secret_scanning %} 警报](/github/administering-a-repository/managing-alerts-from-secret-scanning)                                                                   |       |       | **X**<sup>[1]</sup> | **X**<sup>[1]</sup> |                   **X** |{% endif %}{% ifversion ghes = 3.0 %}
| [查看仓库中的 {% data variables.product.prodname_secret_scanning %} 警报](/github/administering-a-repository/managing-alerts-from-secret-scanning)                                                                       |       |       |                     |                     |                                      **X**                                       |
| [解决、撤销或重新打开 {% data variables.product.prodname_secret_scanning %} 警报](/github/administering-a-repository/managing-alerts-from-secret-scanning)                                                                   |       |       |                     |                     |               **X** |{% endif %}{% ifversion fpt or ghes > 2.22 %}
| [指定其他人员或团队接收仓库中的 {% data variables.product.prodname_secret_scanning %} 警报](/github/administering-a-repository/managing-security-and-analysis-settings-for-your-repository#granting-access-to-security-alerts)    |       |       |                     |                     |                                **X** 
{% endif %}

{% ifversion fpt or ghes > 3.0 or ghae-next %}
[1] 仓库作者和维护者只能看到他们自己提交的警报信息。
{% endif %}

## 延伸阅读

- “[管理对组织仓库的访问](/articles/managing-access-to-your-organization-s-repositories)”
- “[将外部协作者添加到组织中的仓库](/articles/adding-outside-collaborators-to-repositories-in-your-organization)”
- "[组织的项目板权限](/articles/project-board-permissions-for-an-organization)"
