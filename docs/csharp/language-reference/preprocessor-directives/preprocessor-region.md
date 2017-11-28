---
title: "#<a name=\"region-c-reference\"></a>region (référence C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: '#region'
helpviewer_keywords: '#region directive [C#]'
ms.assetid: 672c87d1-9771-4f64-ab3f-0ad3d4ffb2b4
caps.latest.revision: "12"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: cce4a8ac79c4687280e28618d8863d16cd193a3b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="region-c-reference"></a><span data-ttu-id="d14fb-102">#region (référence C#)</span><span class="sxs-lookup"><span data-stu-id="d14fb-102">#region (C# Reference)</span></span>
<span data-ttu-id="d14fb-103">`#region` vous permet de spécifier un bloc de code que vous pouvez développer ou réduire quand vous utilisez la fonctionnalité [Mode Plan](/visualstudio/ide/outlining) de l’éditeur de code Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d14fb-103">`#region` lets you specify a block of code that you can expand or collapse when using the [outlining](/visualstudio/ide/outlining) feature of the Visual Studio Code Editor.</span></span> <span data-ttu-id="d14fb-104">Dans les fichiers de code volumineux, il peut être pratique de réduire ou masquer une ou plusieurs régions pour vous concentrer sur la partie du fichier sur laquelle vous êtes en train de travailler.</span><span class="sxs-lookup"><span data-stu-id="d14fb-104">In longer code files, it is convenient to be able to collapse or hide one or more regions so that you can focus on the part of the file that you are currently working on.</span></span> <span data-ttu-id="d14fb-105">L’exemple suivant montre comment définir une région :</span><span class="sxs-lookup"><span data-stu-id="d14fb-105">The following example shows how to define a region:</span></span>  
  
```csharp
#region MyClass definition  
public class MyClass   
{  
    static void Main()   
    {  
    }  
}  
#endregion  
```  
  
## <a name="remarks"></a><span data-ttu-id="d14fb-106">Remarques</span><span class="sxs-lookup"><span data-stu-id="d14fb-106">Remarks</span></span>  
 <span data-ttu-id="d14fb-107">Un bloc `#region` doit se terminer par une directive [#endregion](../../../csharp/language-reference/preprocessor-directives/preprocessor-endregion.md).</span><span class="sxs-lookup"><span data-stu-id="d14fb-107">A `#region` block must be terminated with a [#endregion](../../../csharp/language-reference/preprocessor-directives/preprocessor-endregion.md) directive.</span></span>  
  
 <span data-ttu-id="d14fb-108">Un bloc `#region` ne peut pas chevaucher un bloc [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md).</span><span class="sxs-lookup"><span data-stu-id="d14fb-108">A `#region` block cannot overlap with a [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) block.</span></span> <span data-ttu-id="d14fb-109">Toutefois, un bloc `#region` peut être imbriqué dans un bloc `#if` et, inversement, un bloc `#if` peut être imbriqué dans un bloc `#region`.</span><span class="sxs-lookup"><span data-stu-id="d14fb-109">However, a `#region` block can be nested in a `#if` block, and a `#if` block can be nested in a `#region` block.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d14fb-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d14fb-110">See Also</span></span>  
 [<span data-ttu-id="d14fb-111">Référence C#</span><span class="sxs-lookup"><span data-stu-id="d14fb-111">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="d14fb-112">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="d14fb-112">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="d14fb-113">Directives de préprocesseur C#</span><span class="sxs-lookup"><span data-stu-id="d14fb-113">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)
