---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: ISESnippet 对象
ms.assetid: 98bc8113-c3cd-4201-bdb9-9d9bdb7e266c
ms.openlocfilehash: f80080f4207cf226fb7466c4842446d08c081347
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: zh-CN
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401070"
---
# <a name="the-isesnippetobject"></a><span data-ttu-id="fd1ef-103">ISESnippet 对象</span><span class="sxs-lookup"><span data-stu-id="fd1ef-103">The ISESnippetObject</span></span>

<span data-ttu-id="fd1ef-104">**ISESnippet** 对象是 Microsoft.PowerShell.Host.ISE.ISESnippet 类的实例。</span><span class="sxs-lookup"><span data-stu-id="fd1ef-104">An **ISESnippet** object is an instance of the Microsoft.PowerShell.Host.ISE.ISESnippet class.</span></span> <span data-ttu-id="fd1ef-105">**$psISE.CurrentPowerShellTab.Snippets** 集合的成员均为 **ISESnippet** 对象的示例。</span><span class="sxs-lookup"><span data-stu-id="fd1ef-105">The members of the **$psISE.CurrentPowerShellTab.Snippets** collection are all examples of **ISESnippet** objects.</span></span> <span data-ttu-id="fd1ef-106">创建代码段的最简单方法是使用 [New-IseSnippet&#91;PSITPro5_ISE&#93;](https://technet.microsoft.com/library/0a6339a3-2683-4a8e-8929-90ad9a95c3e0) cmdlet。</span><span class="sxs-lookup"><span data-stu-id="fd1ef-106">The easiest way to create a snippet is to use the [New-IseSnippet&#91;PSITPro5_ISE&#93;](https://technet.microsoft.com/library/0a6339a3-2683-4a8e-8929-90ad9a95c3e0) cmdlet.</span></span>

## <a name="properties"></a><span data-ttu-id="fd1ef-107">“属性”</span><span class="sxs-lookup"><span data-stu-id="fd1ef-107">Properties</span></span>

### <a name="author"></a><span data-ttu-id="fd1ef-108">作者</span><span class="sxs-lookup"><span data-stu-id="fd1ef-108">Author</span></span>

<span data-ttu-id="fd1ef-109">在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。</span><span class="sxs-lookup"><span data-stu-id="fd1ef-109">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="fd1ef-110">只读属性，可获取代码段作者的姓名。</span><span class="sxs-lookup"><span data-stu-id="fd1ef-110">The read-only property that gets the name of the author of the snippet.</span></span>

```powershell
# Get the author of the first snippet item
$psISE.CurrentPowerShellTab.Snippets.Item(0).Author
```

### <a name="codefragment"></a><span data-ttu-id="fd1ef-111">CodeFragment</span><span class="sxs-lookup"><span data-stu-id="fd1ef-111">CodeFragment</span></span>

<span data-ttu-id="fd1ef-112">在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。</span><span class="sxs-lookup"><span data-stu-id="fd1ef-112">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="fd1ef-113">只读属性，可获取要插入到编辑器中的代码片段。</span><span class="sxs-lookup"><span data-stu-id="fd1ef-113">The read-only property that gets the code fragment to be inserted into the editor.</span></span>

```powershell
# Get the code fragment associated with the first snippet item.
$psISE.CurrentPowerShellTab.Snippets.Item(0).CodeFragment
```

### <a name="shortcut"></a><span data-ttu-id="fd1ef-114">快捷方式</span><span class="sxs-lookup"><span data-stu-id="fd1ef-114">Shortcut</span></span>

<span data-ttu-id="fd1ef-115">在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。</span><span class="sxs-lookup"><span data-stu-id="fd1ef-115">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="fd1ef-116">只读属性，可获取菜单项的 Windows 键盘快捷方式。</span><span class="sxs-lookup"><span data-stu-id="fd1ef-116">The read-only property that gets the Windows keyboard shortcut for the menu item.</span></span>

```powershell
# Get the shortcut for the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Shortcut
```

## <a name="see-also"></a><span data-ttu-id="fd1ef-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fd1ef-117">See Also</span></span>

- [<span data-ttu-id="fd1ef-118">ISESnippetCollection 对象</span><span class="sxs-lookup"><span data-stu-id="fd1ef-118">The ISESnippetCollection Object</span></span>](The-ISESnippetCollection-Object.md)
- [<span data-ttu-id="fd1ef-119">Windows PowerShell ISE 脚本对象模型的用途</span><span class="sxs-lookup"><span data-stu-id="fd1ef-119">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](purpose-of-the-windows-powershell-ise-scripting-object-model.md)
- [<span data-ttu-id="fd1ef-120">ISE 对象模型层次结构</span><span class="sxs-lookup"><span data-stu-id="fd1ef-120">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)