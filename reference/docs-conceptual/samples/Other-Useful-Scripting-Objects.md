---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 其他有用的脚本对象
ms.assetid: 4d781196-720b-4ccc-90d2-c570e5e719f5
ms.openlocfilehash: ff494f375c0d43d83b2a067dbe4f2ab35a90d564
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: zh-CN
ms.lasthandoff: 12/14/2018
ms.locfileid: "53400369"
---
# <a name="other-useful-scripting-objects"></a><span data-ttu-id="8abed-103">其他有用的脚本对象</span><span class="sxs-lookup"><span data-stu-id="8abed-103">Other Useful Scripting Objects</span></span>

<span data-ttu-id="8abed-104">以下对象提供 Windows PowerShell ISE 中的其他脚本编写功能。</span><span class="sxs-lookup"><span data-stu-id="8abed-104">The following objects provide additional scripting functionality in Windows PowerShell ISE.</span></span> <span data-ttu-id="8abed-105">它们不属于 **$psISE** 层次结构。</span><span class="sxs-lookup"><span data-stu-id="8abed-105">They are not part of the **$psISE** hierarchy.</span></span>

## <a name="useful-scripting-objects"></a><span data-ttu-id="8abed-106">有用的脚本对象</span><span class="sxs-lookup"><span data-stu-id="8abed-106">Useful Scripting objects</span></span>

### <a name="psunsupportedconsoleapplications"></a><span data-ttu-id="8abed-107">$psUnsupportedConsoleApplications</span><span class="sxs-lookup"><span data-stu-id="8abed-107">$psUnsupportedConsoleApplications</span></span>

<span data-ttu-id="8abed-108">在 Windows PowerShell ISE 如何与控制台应用程序交互方面存在一些限制。</span><span class="sxs-lookup"><span data-stu-id="8abed-108">There are some limitations on how Windows PowerShell ISE interacts with console applications.</span></span> <span data-ttu-id="8abed-109">需要用户干预的命令或自动化脚本可能无法像从 Windows PowerShell 控制台那样工作。</span><span class="sxs-lookup"><span data-stu-id="8abed-109">A command or an automation script that requires user intervention might not work the way it works from the Windows PowerShell console.</span></span> <span data-ttu-id="8abed-110">你可能想阻止这些命令或脚本在 Windows PowerShell ISE 命令窗格中运行。</span><span class="sxs-lookup"><span data-stu-id="8abed-110">You might want to block these commands or scripts from running in the Windows PowerShell ISE Command pane.</span></span> <span data-ttu-id="8abed-111">**$PsUnsupportedConsoleApplications** 对象保留此类命令的列表。</span><span class="sxs-lookup"><span data-stu-id="8abed-111">The **$psUnsupportedConsoleApplications** object keeps a list of such commands.</span></span> <span data-ttu-id="8abed-112">如果你尝试运行此列表中的命令，你将收到它们不受支持的消息。</span><span class="sxs-lookup"><span data-stu-id="8abed-112">If you try to run the commands in this list, you get a message that they are not supported.</span></span> <span data-ttu-id="8abed-113">下面的脚本将向该列表添加一个条目。</span><span class="sxs-lookup"><span data-stu-id="8abed-113">The following script adds an entry to the list.</span></span>

```powershell
# List the unsupported commands
$psUnsupportedConsoleApplications

# Add a command to this list
$psUnsupportedConsoleApplications.Add('Mycommand')

# Show the augmented list of commands
$psUnsupportedConsoleApplications
```

### <a name="pslocalhelp"></a><span data-ttu-id="8abed-114">$psLocalHelp</span><span class="sxs-lookup"><span data-stu-id="8abed-114">$psLocalHelp</span></span>

<span data-ttu-id="8abed-115">这是维护帮助主题和本地已编译的 HTML 帮助文件中和其关联链接之间的上下文相关映射的字典对象。</span><span class="sxs-lookup"><span data-stu-id="8abed-115">This is a dictionary object that maintains a context-sensitive mapping between Help topics and their associated links in the local compiled HTML Help file.</span></span> <span data-ttu-id="8abed-116">它用于查找有关某个特定主题的本地帮助。</span><span class="sxs-lookup"><span data-stu-id="8abed-116">It is used to locate the local Help for a particular topic.</span></span> <span data-ttu-id="8abed-117">你可以添加或删除此列表中的主题。</span><span class="sxs-lookup"><span data-stu-id="8abed-117">You can add or delete topics from this list.</span></span> <span data-ttu-id="8abed-118">下面的代码示例显示了 `$psLocalHelp` 中包含的一些示例键值对。</span><span class="sxs-lookup"><span data-stu-id="8abed-118">The following code example shows some example key-value pairs that are contained in `$psLocalHelp`.</span></span>

```powershell
# See the local help map
$psLocalHelp | Format-List
```

```output
Key   : Add-Computer
Value : WindowsPowerShellHelp.chm::/html/093f660c-b8d5-43cf-aa0c-54e5e54e76f9.htm

Key   : Add-Content
Value : WindowsPowerShellHelp.chm::/html/0c836a1b-f389-4e9a-9325-0f415686d194.htm
```

<span data-ttu-id="8abed-119">下面的脚本将向该列表添加一个条目。</span><span class="sxs-lookup"><span data-stu-id="8abed-119">The following script adds an entry to the list.</span></span>

```powershell
$psLocalHelp.Add("get-myNoun", "c:\MyFolder\MyHelpChm.chm::/html/0198854a-1298-57ae-aa0c-87b5e5a84712.htm")
```

### <a name="psonlinehelp"></a><span data-ttu-id="8abed-120">$psOnlineHelp</span><span class="sxs-lookup"><span data-stu-id="8abed-120">$psOnlineHelp</span></span>

<span data-ttu-id="8abed-121">这是维护帮助主题的主题标题和其关联外部 URL 之间的上下文相关映射的字典对象。</span><span class="sxs-lookup"><span data-stu-id="8abed-121">This is a dictionary object that maintains a context-sensitive mapping between topic titles of Help topics and their associated external URLs.</span></span> <span data-ttu-id="8abed-122">它用于查找 Web 上有关某个特定主题的帮助。</span><span class="sxs-lookup"><span data-stu-id="8abed-122">It is used to locate the Help for a particular topic on the web.</span></span> <span data-ttu-id="8abed-123">你可以添加或删除此列表中的主题。</span><span class="sxs-lookup"><span data-stu-id="8abed-123">You can add or delete topics from this list.</span></span>

```powershell
$psOnlineHelp | Format-List
```

```output
Key   : Add-Computer
Value : http://go.microsoft.com/fwlink/p/?LinkID=135194

Key   : Add-Content
Value : http://go.microsoft.com/fwlink/p/?LinkID=113278
```

<span data-ttu-id="8abed-124">下面的脚本将向该列表添加一个条目。</span><span class="sxs-lookup"><span data-stu-id="8abed-124">The following script adds an entry to the list.</span></span>

```powershell
$psOnlineHelp.Add("get-myNoun", "http://www.mydomain.com/MyNoun.html")
```

## <a name="see-also"></a><span data-ttu-id="8abed-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8abed-125">See Also</span></span>

[<span data-ttu-id="8abed-126">Windows PowerShell ISE 脚本对象模型的用途</span><span class="sxs-lookup"><span data-stu-id="8abed-126">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](../components/ise/object-model/Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)