---
title: 用于视图的 CustomControl 的帧的 FirstLineIndent 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bb4e1564-3fd3-4be3-b93e-ac90480e05c0
caps.latest.revision: 6
ms.openlocfilehash: 3130ecc69f7d1568bcbd392dd24e8cdcc3382905
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363056"
---
# <a name="firstlineindent-element-for-frame-for-customcontrol-for-view-format"></a>FirstLineIndent Element for Frame for CustomControl for View (Format)

指定第一行数据向右移动的字符数。 定义自定义控件视图时，将使用此元素。

用于 CustomEntry 的 CustomControl for view （format） CustomEntries 元素的 ViewDefinitions 元素（format） View 元素（format） CustomControl 元素（format） CustomEntries 元素用于 CustomItem for CustomControl for View （Format） FirstLineIndent 元素的 CustomControlView （Format） Frame 元素的 CustomEntry

## <a name="syntax"></a>语法

```xml
<FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
```

## <a name="attributes-and-elements"></a>属性和元素

以下各节介绍 `FirstLineIndent` 元素的属性、子元素和父元素。

### <a name="attributes"></a>属性

无。

### <a name="child-elements"></a>子元素

无。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[View 的 CustomItem for CustomControl 的 Frame 元素（Format）](./frame-element-for-customitem-for-customcontrol-for-view-format.md)|定义数据的显示方式，例如，将数据向左或向右移动。|

## <a name="text-value"></a>文本值

指定要将数据的第一行移动到的字符数。

## <a name="remarks"></a>备注

如果指定此元素，则不能指定[FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)元素。

## <a name="see-also"></a>另请参阅

[用于视图的 CustomControl 的帧的 FirstLineHanging 元素（格式）](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)

[View 的 CustomItem for CustomControl 的 Frame 元素（Format）](./frame-element-for-customitem-for-customcontrol-for-view-format.md)

[编写 PowerShell 格式化文件](./writing-a-powershell-formatting-file.md)