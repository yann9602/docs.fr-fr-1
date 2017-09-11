---
title: "#<a name=\"warning-c-reference\"></a>warning (informations de référence sur C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '#warning'
dev_langs:
- CSharp
helpviewer_keywords:
- '#warning directive [C#]'
ms.assetid: e6fb496d-bb8b-4018-baf6-5b60a0c8902b
caps.latest.revision: 9
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
ms.openlocfilehash: 8630101a90bd6d4ed2036b495b254c9475531dc0
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="warning-c-reference"></a><span data-ttu-id="62cd5-102">#warning (informations de référence sur C#)</span><span class="sxs-lookup"><span data-stu-id="62cd5-102">#warning (C# Reference)</span></span>
<span data-ttu-id="62cd5-103">`#warning` vous permet de générer un avertissement de premier niveau à partir d’un emplacement spécifique dans votre code.</span><span class="sxs-lookup"><span data-stu-id="62cd5-103">`#warning` lets you generate a level one warning from a specific location in your code.</span></span> <span data-ttu-id="62cd5-104">Exemple :</span><span class="sxs-lookup"><span data-stu-id="62cd5-104">For example:</span></span>  
  
```csharp
#warning Deprecated code in this method.  
```  
  
## <a name="remarks"></a><span data-ttu-id="62cd5-105">Remarques</span><span class="sxs-lookup"><span data-stu-id="62cd5-105">Remarks</span></span>  
 <span data-ttu-id="62cd5-106">`#warning` est souvent utilisé dans une directive conditionnelle.</span><span class="sxs-lookup"><span data-stu-id="62cd5-106">A common use of `#warning` is in a conditional directive.</span></span> <span data-ttu-id="62cd5-107">Il est aussi possible de générer une erreur définie par l’utilisateur avec [#error](../../../csharp/language-reference/preprocessor-directives/preprocessor-error.md).</span><span class="sxs-lookup"><span data-stu-id="62cd5-107">It is also possible to generate a user-defined error with [#error](../../../csharp/language-reference/preprocessor-directives/preprocessor-error.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="62cd5-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="62cd5-108">Example</span></span>  
  
```csharp
// preprocessor_warning.cs  
// CS1030 expected  
#define DEBUG  
class MainClass   
{  
    static void Main()   
    {  
#if DEBUG  
#warning DEBUG is defined  
#endif  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="62cd5-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="62cd5-109">See Also</span></span>  
 <span data-ttu-id="62cd5-110">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="62cd5-110">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="62cd5-111">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="62cd5-111">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="62cd5-112">Directives de préprocesseur C#</span><span class="sxs-lookup"><span data-stu-id="62cd5-112">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)

