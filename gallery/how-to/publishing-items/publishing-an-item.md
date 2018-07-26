---
ms.date: 06/12/2017
contributor: JKeithB
keywords: 库,powershell,cmdlet,psgallery
title: 创建和发布项
ms.openlocfilehash: 7c2a2be6986bf65c168d7c3960366fac4ee31301
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/16/2018
ms.locfileid: "34189527"
---
# <a name="creating-and-publishing-an-item"></a><span data-ttu-id="f8403-103">创建和发布项</span><span class="sxs-lookup"><span data-stu-id="f8403-103">Creating and publishing an item</span></span>

<span data-ttu-id="f8403-104">在 PowerShell 库中，可以发布稳定的 PowerShell 模块、脚本和 DSC 资源，并与更广泛的 PowerShell 用户社区共享它们。</span><span class="sxs-lookup"><span data-stu-id="f8403-104">The PowerShell Gallery is the place to publish and share stable PowerShell modules, scripts, and DSC resources with the broader PowerShell user community.</span></span>

<span data-ttu-id="f8403-105">本文介绍了有关如何准备脚本或模块，并将其发布到 PowerShell 库的机制和重要步骤。</span><span class="sxs-lookup"><span data-stu-id="f8403-105">This article covers the mechanics and important steps for preparing a script or module, and publishing it to the PowerShell Gallery.</span></span>
<span data-ttu-id="f8403-106">强烈建议查看[发布指南](https://msdn.microsoft.com/en-us/powershell/gallery/psgallery/psgallery-PublishingGuidelines)，了解如何确保发布的项将为更广泛的 PowerShell 库用户所接受。</span><span class="sxs-lookup"><span data-stu-id="f8403-106">We strongly encourage that you review the [Publishing Guidelines](https://msdn.microsoft.com/en-us/powershell/gallery/psgallery/psgallery-PublishingGuidelines) to understand how to ensure that the items you publish will be more widely accepted by PowerShell Gallery users.</span></span>

<span data-ttu-id="f8403-107">若要将项发布到 PowerShell 库，至少必须符合以下要求：</span><span class="sxs-lookup"><span data-stu-id="f8403-107">The minimum requirements to publish an item to the PowerShell Gallery are:</span></span>

- <span data-ttu-id="f8403-108">拥有 PowerShell 库帐户及其关联的 API 密钥</span><span class="sxs-lookup"><span data-stu-id="f8403-108">Have a PowerShell Gallery account, and the API Key associated with it</span></span>
- <span data-ttu-id="f8403-109">确保项中包含相应的元数据</span><span class="sxs-lookup"><span data-stu-id="f8403-109">Ensure Required Metadata is in your item</span></span>
- <span data-ttu-id="f8403-110">使用预验证工具确保项可供发布</span><span class="sxs-lookup"><span data-stu-id="f8403-110">Use the pre-validation tools to ensure your item is ready to publish</span></span>
- <span data-ttu-id="f8403-111">使用 Publish-Module 和 Publish-Script 命令将项发布到 PowerShell 库</span><span class="sxs-lookup"><span data-stu-id="f8403-111">Publish the item to the PowerShell Gallery using the Publish-Module and Publish-Script commands</span></span>
- <span data-ttu-id="f8403-112">解决与项相关的问题或疑问</span><span class="sxs-lookup"><span data-stu-id="f8403-112">Responding to questions or concerns about your item</span></span>

<span data-ttu-id="f8403-113">PowerShell 库接受 PowerShell 模块和 PowerShell 脚本。</span><span class="sxs-lookup"><span data-stu-id="f8403-113">The PowerShell Gallery accepts PowerShell modules and PowerShell scripts.</span></span>
<span data-ttu-id="f8403-114">我们所指的 PowerShell 脚本是一个文件，并不属于较大模块。</span><span class="sxs-lookup"><span data-stu-id="f8403-114">When we refer to scripts, we mean a PowerShell script that is a single file, and not part of a larger module.</span></span>

## <a name="powershell-gallery-account-and-api-key"></a><span data-ttu-id="f8403-115">PowerShell 库帐户和 API 密钥</span><span class="sxs-lookup"><span data-stu-id="f8403-115">PowerShell Gallery Account and API Key</span></span>

<span data-ttu-id="f8403-116">请参阅[创建 PowerShell 库帐户](https://msdn.microsoft.com/en-us/powershell/gallery/psgallery/psgallery_creating_an_account)，了解如何设置 PowerShell 库帐户。</span><span class="sxs-lookup"><span data-stu-id="f8403-116">See [Creating a PowerShell Gallery Account](https://msdn.microsoft.com/en-us/powershell/gallery/psgallery/psgallery_creating_an_account) for how to set up your PowerShell Gallery account.</span></span>

<span data-ttu-id="f8403-117">创建帐户后，便可以获取发布项所需的 API 密钥。</span><span class="sxs-lookup"><span data-stu-id="f8403-117">Once you have created an account, you can get the API Key needed to publish an item.</span></span>
<span data-ttu-id="f8403-118">使用此帐户登录后，用户名将显示在 PowerShell 库页面（而不是注册页）的顶部。</span><span class="sxs-lookup"><span data-stu-id="f8403-118">After you sign in with the account, your username will be displayed at the top of the PowerShell Gallery pages instead of Register.</span></span>
<span data-ttu-id="f8403-119">单击用户名将转到“我的帐户”页，可以在其中找到 API 密钥。</span><span class="sxs-lookup"><span data-stu-id="f8403-119">Clicking on your username will take you to the My Account page, where you will find the API Key.</span></span>

<span data-ttu-id="f8403-120">请注意，必须安全处理 API 密钥，就像处理登录名和密码一样。</span><span class="sxs-lookup"><span data-stu-id="f8403-120">Note: The API Key must be treated as securely as your login and password.</span></span>
<span data-ttu-id="f8403-121">使用此密钥，你或其他任何人可以更新你在 PowerShell 库中拥有的全部项。</span><span class="sxs-lookup"><span data-stu-id="f8403-121">With this key you, or anyone else, can update any item you own in the PowerShell Gallery.</span></span>
<span data-ttu-id="f8403-122">建议定期更新此密钥，具体方法为使用“我的帐户”页上的“重置密钥”。</span><span class="sxs-lookup"><span data-stu-id="f8403-122">We recommend updating the key regularly, which can be done using Reset Key on your My Account page.</span></span>

## <a name="required-metadata-for-items-published-to-the-powershell-gallery"></a><span data-ttu-id="f8403-123">发布到 PowerShell 库的项的相应元数据</span><span class="sxs-lookup"><span data-stu-id="f8403-123">Required Metadata for Items Published to the PowerShell Gallery</span></span>

<span data-ttu-id="f8403-124">PowerShell 库向库用户提供从脚本或模块清单的元数据字段中提取的信息。</span><span class="sxs-lookup"><span data-stu-id="f8403-124">The PowerShell Gallery provides information to gallery users drawn from metadata fields that are included in the script or module manifest.</span></span>
<span data-ttu-id="f8403-125">必须满足有关项清单所提供信息的一小组要求，才能创建或修改发布到 PowerShell 库中的项。</span><span class="sxs-lookup"><span data-stu-id="f8403-125">Creating or modifying items for publication to the PowerShell Gallery has a small set of requirements for information supplied in the item manifest.</span></span>
<span data-ttu-id="f8403-126">强烈建议查看[发布指南](https://msdn.microsoft.com/en-us/powershell/gallery/psgallery/psgallery-PublishingGuidelines)中的“项元数据”部分，了解如何向用户提供最实用的项信息。</span><span class="sxs-lookup"><span data-stu-id="f8403-126">We strongly encourage that you review the Item Metadata section of the [Publishing Guidelines](https://msdn.microsoft.com/en-us/powershell/gallery/psgallery/psgallery-PublishingGuidelines) to learn how to provide the best information to users with your items.</span></span>

<span data-ttu-id="f8403-127">[New-ModuleManifest](https://msdn.microsoft.com/en-us/powershell/gallery/psget/module/ModuleManifest-Reference) 和 [New-ScriptFileInfo](https://msdn.microsoft.com/en-us/powershell/gallery/psget/script/psget_new-scriptfileinfo) cmdlet 将创建清单模板，内含所有清单元素的占位符。</span><span class="sxs-lookup"><span data-stu-id="f8403-127">The [New-ModuleManifest](https://msdn.microsoft.com/en-us/powershell/gallery/psget/module/ModuleManifest-Reference) and [New-ScriptFileInfo](https://msdn.microsoft.com/en-us/powershell/gallery/psget/script/psget_new-scriptfileinfo) cmdlets will create the manifest template for you, with placeholders for all the manifest elements.</span></span>

<span data-ttu-id="f8403-128">这两个清单都包含两个对发布非常重要的部分，即主键数据和 PrivateData 的 PSData 区域。PowerShell 模块清单中的主键数据是 PrivateData 部分之外的所有数据。</span><span class="sxs-lookup"><span data-stu-id="f8403-128">Both manifests have two sections that are important for publishing, the Primary Key Data and PSData area of PrivateData The primary key data in a PowerShell module manifest is everything outside of the PrivateData section.</span></span>
<span data-ttu-id="f8403-129">主键集合已绑定到在使用的 PowerShell 版本，并且不支持未定义的主键。</span><span class="sxs-lookup"><span data-stu-id="f8403-129">The set of primary keys is tied to the version of PowerShell in use, and undefined are not supported.</span></span>
<span data-ttu-id="f8403-130">由于 PrivateData 支持添加新键，因此 PowerShell 库的专有元素位于 PSData 中。</span><span class="sxs-lookup"><span data-stu-id="f8403-130">PrivateData supports adding new keys, so the elements specific to the PowerShell Gallery are in PSData.</span></span>


<span data-ttu-id="f8403-131">对于要发布到 PowerShell 库的项，需要填写的最重要清单元素包括：</span><span class="sxs-lookup"><span data-stu-id="f8403-131">Manifest elements that are most important to fill in for item you publish to the PowerShell Gallery are:</span></span>

- <span data-ttu-id="f8403-132">脚本或模块名称 - 这些提取自脚本的 .PS1 名称或模块的 .PSD1 名称。</span><span class="sxs-lookup"><span data-stu-id="f8403-132">Script or Module Name - Those are drawn from the names of the .PS1 for a script, or the .PSD1 for a module.</span></span>
- <span data-ttu-id="f8403-133">版本 - 此为必需的主键，格式应遵循 SemVer 指南（有关详细信息，请参阅“最佳做法”）</span><span class="sxs-lookup"><span data-stu-id="f8403-133">Version - this is a required primary key, format should follow SemVer guidelines (see Best Practices for details)</span></span>
- <span data-ttu-id="f8403-134">作者 - 此为必需的主键，包含要与项相关联的名称（请参阅下面的“作者和所有者”）</span><span class="sxs-lookup"><span data-stu-id="f8403-134">Author - this is a required primary key, and contains the name to be associated with the item (see Authors and Owners, below)</span></span>
- <span data-ttu-id="f8403-135">说明 - 此为必需的主键，用于简要说明该项的用途和任何使用要求</span><span class="sxs-lookup"><span data-stu-id="f8403-135">Description - this is a required primary key, used to briefly explain what this item does and any requirements for using it</span></span>
- <span data-ttu-id="f8403-136">ProjectURI - 此为强烈建议填写的 PSData URI 字段，提供指向 Github 存储库或类似可以对项进行开发的位置的链接</span><span class="sxs-lookup"><span data-stu-id="f8403-136">ProjectURI - this is a strongly recommended URI field in PSData that provides a link to a Github repo or similar location where you do development on the item</span></span>

<span data-ttu-id="f8403-137">PowerShell 库项的作者和所有者是相关概念，并非总是一致。</span><span class="sxs-lookup"><span data-stu-id="f8403-137">Authors and Owners of PowerShell Gallery items are related concepts, but do not always match.</span></span>
<span data-ttu-id="f8403-138">项所有者是拥有 PowerShell 库帐户且有权维护项的用户。</span><span class="sxs-lookup"><span data-stu-id="f8403-138">Item Owners are users with PowerShell Gallery accounts that have permission to maintain the item.</span></span> <span data-ttu-id="f8403-139">可能有多个可以更新任意项的所有者。</span><span class="sxs-lookup"><span data-stu-id="f8403-139">There may be many Owners who can update any item.</span></span>
<span data-ttu-id="f8403-140">只能从 PowerShell 库获取所有者。如果将项从一个系统复制到另一个系统，将会丢失所有者。</span><span class="sxs-lookup"><span data-stu-id="f8403-140">The Owner is only available from the PowerShell Gallery, and is lost if the item is copied from one system to another.</span></span>
<span data-ttu-id="f8403-141">由于作者是清单数据中内置的字符串，因此始终是项的一部分。</span><span class="sxs-lookup"><span data-stu-id="f8403-141">Author is a string that is built into the manifest data, so it is always part of the item.</span></span>
<span data-ttu-id="f8403-142">对于 Microsoft 产品项，建议如下：</span><span class="sxs-lookup"><span data-stu-id="f8403-142">The recommendations for items from Microsoft products are:</span></span>

- <span data-ttu-id="f8403-143">有多个所有者，至少有一个是生产此项的团队的名称；</span><span class="sxs-lookup"><span data-stu-id="f8403-143">Have multiple owners, with at least one being the name of the team that produces the item;</span></span>
- <span data-ttu-id="f8403-144">将众所周知的团队名称（如 Azure SDK 团队）或 Microsoft Corporation 设为作者。</span><span class="sxs-lookup"><span data-stu-id="f8403-144">Have the Author be a well-known team name (such as Azure SDK Team), or Microsoft Corporation.</span></span>


## <a name="pre-validate-your-item"></a><span data-ttu-id="f8403-145">预验证项</span><span class="sxs-lookup"><span data-stu-id="f8403-145">Pre-Validate Your Item</span></span>

<span data-ttu-id="f8403-146">在将项发布到 PowerShell 库之前，需要对代码运行下面几个工具：</span><span class="sxs-lookup"><span data-stu-id="f8403-146">There are a few tools you need to run against your code before publishing your item to the PowerShell Gallery:</span></span>

- <span data-ttu-id="f8403-147">[PowerShell 脚本分析器](https://www.powershellgallery.com/packages/PSScriptAnalyzer/)（位于 PowerShell 库中）</span><span class="sxs-lookup"><span data-stu-id="f8403-147">[PowerShell Script Analyzer](https://www.powershellgallery.com/packages/PSScriptAnalyzer/), which is in the PowerShell Gallery</span></span>
- <span data-ttu-id="f8403-148">对于模块：属于 PowerShell 的 Test-ModuleManifest</span><span class="sxs-lookup"><span data-stu-id="f8403-148">For modules, Test-ModuleManifest which is part of PowerShell</span></span>
- <span data-ttu-id="f8403-149">对于脚本：PowerShell Get 随附的 Test-ScriptFileInfo</span><span class="sxs-lookup"><span data-stu-id="f8403-149">For scripts, Test-ScriptFileInfo which comes with PowerShell Get</span></span>

<span data-ttu-id="f8403-150">[PowerShell 脚本分析器](https://www.powershellgallery.com/packages/PSScriptAnalyzer/)是一款静态代码分析工具，可用于扫描代码，以确保其符合基本的 PowerShell 编码准则。</span><span class="sxs-lookup"><span data-stu-id="f8403-150">[PowerShell Script Analyzer](https://www.powershellgallery.com/packages/PSScriptAnalyzer/) is a static code analysis tool that will scan your code to ensure it meets basic PowerShell coding guidelines.</span></span> <span data-ttu-id="f8403-151">此工具可发现代码存在的常见和严重问题，应在开发过程中定期运行，这样有助于确保项可供发布。</span><span class="sxs-lookup"><span data-stu-id="f8403-151">This tool will identify common and critical issues in your code, and should be run regularly during development to help you get your item ready to publish.</span></span>
<span data-ttu-id="f8403-152">PowerShell 脚本分析器会列出标识为“错误”、“警告”和“信息”的问题。</span><span class="sxs-lookup"><span data-stu-id="f8403-152">PowerShell Script Analyzer will provide list of issues identified as Errors, Warning, and Information.</span></span>
<span data-ttu-id="f8403-153">必须先修复所有错误，然后才能将项发布到 PowerShell 库中。</span><span class="sxs-lookup"><span data-stu-id="f8403-153">All errors must be addressed before you publish to the PowerShell Gallery.</span></span> <span data-ttu-id="f8403-154">如果是警告，则需要查看，并且大多数都应予以解决。</span><span class="sxs-lookup"><span data-stu-id="f8403-154">Warnings need to be reviewed, and most should be addressed.</span></span>
<span data-ttu-id="f8403-155">每当在 PowerShell 库中发布或更新项时，都会运行 PowerShell 脚本分析器。</span><span class="sxs-lookup"><span data-stu-id="f8403-155">PowerShell Script Analyzer is run every time an item is published or updated in the PowerShell Gallery.</span></span>
<span data-ttu-id="f8403-156">库运营团队会联系项所有者来修复已发现的错误。</span><span class="sxs-lookup"><span data-stu-id="f8403-156">The Gallery Operations team will contact item owners to address errors that are found.</span></span>

<span data-ttu-id="f8403-157">如果 PowerShell 库基础结构无法读取项中的清单信息，将无法发布此项。</span><span class="sxs-lookup"><span data-stu-id="f8403-157">If the manifest information in your item cannot be read by the PowerShell Gallery infrastructure, you will not be able to publish.</span></span>
<span data-ttu-id="f8403-158">[Test-ModuleManifest](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/test-modulemanifest) 可捕获导致已安装的模块不可用的常见问题。</span><span class="sxs-lookup"><span data-stu-id="f8403-158">[Test-ModuleManifest](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/test-modulemanifest) will catch common problems that would cause the module to not be usable when it is installed.</span></span> <span data-ttu-id="f8403-159">必须先对每个模块运行此命令，然后才能将其发布到 PowerShell 库中。</span><span class="sxs-lookup"><span data-stu-id="f8403-159">It must be run for every module prior to publishing it to the PowerShell Gallery.</span></span>

<span data-ttu-id="f8403-160">同样，[Test-ScriptFileInfo](https://msdn.microsoft.com/en-us/powershell/gallery/psget/script/psget_test-scriptfileinfo) 可用于验证脚本中的元数据。必须先对与模块分开发布的每个脚本运行此命令，然后才能将其发布到 PowerShell 库中。</span><span class="sxs-lookup"><span data-stu-id="f8403-160">Likewise, [Test-ScriptFileInfo](https://msdn.microsoft.com/en-us/powershell/gallery/psget/script/psget_test-scriptfileinfo) validates the metadata in a script, and must be run on every script (published separate from a module) prior to publishing it to the Powershell Gallery.</span></span>


## <a name="publishing-items"></a><span data-ttu-id="f8403-161">发布项</span><span class="sxs-lookup"><span data-stu-id="f8403-161">Publishing Items</span></span>

<span data-ttu-id="f8403-162">必须使用 [Publish-Script](https://msdn.microsoft.com/en-us/powershell/gallery/psget/script/psget_publish-script) 或 [Publish-Module](https://msdn.microsoft.com/en-us/powershell/gallery/psget/module/psget_publish-module) 将项发布到 PowerShell 库中。</span><span class="sxs-lookup"><span data-stu-id="f8403-162">You must use the [Publish-Script](https://msdn.microsoft.com/en-us/powershell/gallery/psget/script/psget_publish-script) or [Publish-Module](https://msdn.microsoft.com/en-us/powershell/gallery/psget/module/psget_publish-module) to publish items to the PowerShell Gallery.</span></span>
<span data-ttu-id="f8403-163">这两个命令都需要</span><span class="sxs-lookup"><span data-stu-id="f8403-163">These commands both require</span></span>

- <span data-ttu-id="f8403-164">将发布的项的路径。</span><span class="sxs-lookup"><span data-stu-id="f8403-164">The path to the item you will publish.</span></span> <span data-ttu-id="f8403-165">对于模块，使用为模块指定的文件夹。</span><span class="sxs-lookup"><span data-stu-id="f8403-165">For a module, use the folder named for your module.</span></span> <span data-ttu-id="f8403-166">如果指定的文件夹包含同一模块的多个版本，必须指定 RequiredVersion。</span><span class="sxs-lookup"><span data-stu-id="f8403-166">If you specify a folder that contains multiple versions of the same module, you must specify RequiredVersion.</span></span>
- <span data-ttu-id="f8403-167">Nuget API 密钥。</span><span class="sxs-lookup"><span data-stu-id="f8403-167">A Nuget API key.</span></span> <span data-ttu-id="f8403-168">这是 PowerShell 库的“我的帐户”页面上显示的 API 密钥。</span><span class="sxs-lookup"><span data-stu-id="f8403-168">This is the API key found in the My Account page on the PowerShell Gallery.</span></span>

<span data-ttu-id="f8403-169">由于命令行中的其他大多数选项都应位于要发布的项的清单数据中，因此无需在命令中指定这些选项。</span><span class="sxs-lookup"><span data-stu-id="f8403-169">Most of the other options in the command line should be in the manifest data for the item you are publishing, so you should not need to specify them in the command.</span></span>

<span data-ttu-id="f8403-170">为了避免出错，强烈建议在发布之前尝试使用 -Whatif -Verbose 运行命令。</span><span class="sxs-lookup"><span data-stu-id="f8403-170">To avoid errors, it is strongly recommended that you try the commands using -Whatif -Verbose, before publishing.</span></span>
<span data-ttu-id="f8403-171">这将节省相当多的时间，因为每次将项发布到 PowerShell 库时，都必须更新项的清单部分中的版本号。</span><span class="sxs-lookup"><span data-stu-id="f8403-171">This will save considerable time, since every time you publish to the PowerShell Gallery, you must update the version number in the manifest section of the item.</span></span>

<span data-ttu-id="f8403-172">示例命令为：'Publish-Module -Path ".\MyModule" -RequiredVersion "0.0.1" -NugetAPIKey "GUID" -Whatif -Verbose' 'Publish-Script -Path ".\MyScriptFile.PS1" -NugetAPIKey "GUID" -Whatif -Verbose'</span><span class="sxs-lookup"><span data-stu-id="f8403-172">Examples would be: 'Publish-Module -Path ".\MyModule" -RequiredVersion "0.0.1" -NugetAPIKey "GUID" -Whatif -Verbose' 'Publish-Script -Path ".\MyScriptFile.PS1" -NugetAPIKey "GUID" -Whatif -Verbose'</span></span>

<span data-ttu-id="f8403-173">仔细检查输出，如果没有看到任何错误或警告，请重复运行命令，而不使用 -Whatif。</span><span class="sxs-lookup"><span data-stu-id="f8403-173">Review the output carefully, and if you see no errors or warnings, repeat the command without -Whatif.</span></span>

<span data-ttu-id="f8403-174">发布到 PowerShell 库的所有项都会进行病毒扫描，并会使用 PowerShell 脚本分析器进行分析。</span><span class="sxs-lookup"><span data-stu-id="f8403-174">All items that are published to the PowerShell Gallery will be scanned for viruses, and will be analyzed using the PowerShell Script Analyzer.</span></span>
<span data-ttu-id="f8403-175">此时发现的所有问题都会发回给发布者予以解决。</span><span class="sxs-lookup"><span data-stu-id="f8403-175">Any issues that arise at that time will be sent back to the publisher for resolution.</span></span>

<span data-ttu-id="f8403-176">将项发布到 PowerShell 库后，需要检查是否有项反馈。</span><span class="sxs-lookup"><span data-stu-id="f8403-176">Once you have published an item to the PowerShell Gallery, you will need to watch for feedback on your item.</span></span>

- <span data-ttu-id="f8403-177">请务必监视与发布帐户相关联的电子邮件地址。</span><span class="sxs-lookup"><span data-stu-id="f8403-177">Ensure you monitor the email address associated with the account used to publish.</span></span>
<span data-ttu-id="f8403-178">用户和 PowerShell 库运营团队会通过此帐户提供反馈，包括通过 PSSA 或防病毒扫描发现的问题。</span><span class="sxs-lookup"><span data-stu-id="f8403-178">Users, and the PowerShell Gallery Operations team will provide feedback via that account, including issues from the PSSA or antivirus scans.</span></span>
<span data-ttu-id="f8403-179">如果电子邮件帐户无效，或将严重问题报告给此帐户后很长时间都未得到解决，可以将项视为已放弃，并将从 PowerShell 库中删除项，如我们的[使用条款](https://www.powershellgallery.com/policies/Terms)所述。</span><span class="sxs-lookup"><span data-stu-id="f8403-179">If the email account is invalid, or if serious issues are reported to the account and left unresolved for a long time, items can be considered abandoned and will be removed from the PowerShell Gallery as described in our [Terms of Use](https://www.powershellgallery.com/policies/Terms).</span></span>
- <span data-ttu-id="f8403-180">建议订阅已发布的每个 PowerShell 库项的评论。</span><span class="sxs-lookup"><span data-stu-id="f8403-180">We recommend you subscribe to Comments for each PowerShell Gallery item you publish.</span></span>
<span data-ttu-id="f8403-181">这样，如果有人在 PowerShell 库中对你的项发表评论，可以收到通知。</span><span class="sxs-lookup"><span data-stu-id="f8403-181">This allows you to be notified if anyone comments on your items in the PowerShell Gallery.</span></span>
<span data-ttu-id="f8403-182">可以根据需要进行订阅，因为这需要创建 LiveFyre 帐户。</span><span class="sxs-lookup"><span data-stu-id="f8403-182">This is optional, as it requires creating an account with LiveFyre.</span></span>