---
title: "#<a name=\"region-c-reference\"></a>region (référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '#region'
dev_langs:
- CSharp
helpviewer_keywords:
- '#region directive [C#]'
ms.assetid: 672c87d1-9771-4f64-ab3f-0ad3d4ffb2b4
caps.latest.revision: 12
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: f7685d23bc1d40a0d0b6c9ac9a644019e1186eb7
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="region-c-reference"></a><span data-ttu-id="7e00e-102">#region (référence C#)</span><span class="sxs-lookup"><span data-stu-id="7e00e-102">#region (C# Reference)</span></span>
<span data-ttu-id="7e00e-103">`#region` vous permet de spécifier un bloc de code que vous pouvez développer ou réduire quand vous utilisez la fonctionnalité [Mode Plan](/visualstudio/ide/outlining) de l’éditeur de code Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="7e00e-103">`#region` lets you specify a block of code that you can expand or collapse when using the [outlining](/visualstudio/ide/outlining) feature of the Visual Studio Code Editor.</span></span> <span data-ttu-id="7e00e-104">Dans les fichiers de code volumineux, il peut être pratique de réduire ou masquer une ou plusieurs régions pour vous concentrer sur la partie du fichier sur laquelle vous êtes en train de travailler.</span><span class="sxs-lookup"><span data-stu-id="7e00e-104">In longer code files, it is convenient to be able to collapse or hide one or more regions so that you can focus on the part of the file that you are currently working on.</span></span> <span data-ttu-id="7e00e-105">L’exemple suivant montre comment définir une région :</span><span class="sxs-lookup"><span data-stu-id="7e00e-105">The following example shows how to define a region:</span></span>  
  
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
  
## <a name="remarks"></a><span data-ttu-id="7e00e-106">Remarques</span><span class="sxs-lookup"><span data-stu-id="7e00e-106">Remarks</span></span>  
 <span data-ttu-id="7e00e-107">Un bloc `#region` doit se terminer par une directive [#endregion](../../../csharp/language-reference/preprocessor-directives/preprocessor-endregion.md).</span><span class="sxs-lookup"><span data-stu-id="7e00e-107">A `#region` block must be terminated with a [#endregion](../../../csharp/language-reference/preprocessor-directives/preprocessor-endregion.md) directive.</span></span>  
  
 <span data-ttu-id="7e00e-108">Un bloc `#region` ne peut pas chevaucher un bloc [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md).</span><span class="sxs-lookup"><span data-stu-id="7e00e-108">A `#region` block cannot overlap with a [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) block.</span></span> <span data-ttu-id="7e00e-109">Toutefois, un bloc `#region` peut être imbriqué dans un bloc `#if` et, inversement, un bloc `#if` peut être imbriqué dans un bloc `#region`.</span><span class="sxs-lookup"><span data-stu-id="7e00e-109">However, a `#region` block can be nested in a `#if` block, and a `#if` block can be nested in a `#region` block.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e00e-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7e00e-110">See Also</span></span>  
 <span data-ttu-id="7e00e-111">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="7e00e-111">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="7e00e-112">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="7e00e-112">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="7e00e-113">Directives de préprocesseur C#</span><span class="sxs-lookup"><span data-stu-id="7e00e-113">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)

