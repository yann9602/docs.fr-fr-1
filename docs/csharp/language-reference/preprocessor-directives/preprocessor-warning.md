---
title: "#<a name=\"warning-c-reference\"></a>warning (informations de référence sur C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: '#warning'
helpviewer_keywords: '#warning directive [C#]'
ms.assetid: e6fb496d-bb8b-4018-baf6-5b60a0c8902b
caps.latest.revision: "9"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 8145c4a62d5179d6fa46e27186d83fc0108939d1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="warning-c-reference"></a><span data-ttu-id="88e90-102">#warning (référence C#)</span><span class="sxs-lookup"><span data-stu-id="88e90-102">#warning (C# Reference)</span></span>
<span data-ttu-id="88e90-103">`#warning` vous permet de générer un avertissement de premier niveau à partir d’un emplacement spécifique dans votre code.</span><span class="sxs-lookup"><span data-stu-id="88e90-103">`#warning` lets you generate a level one warning from a specific location in your code.</span></span> <span data-ttu-id="88e90-104">Exemple :</span><span class="sxs-lookup"><span data-stu-id="88e90-104">For example:</span></span>  
  
```csharp
#warning Deprecated code in this method.  
```  
  
## <a name="remarks"></a><span data-ttu-id="88e90-105">Remarques</span><span class="sxs-lookup"><span data-stu-id="88e90-105">Remarks</span></span>  
 <span data-ttu-id="88e90-106">`#warning` est souvent utilisé dans une directive conditionnelle.</span><span class="sxs-lookup"><span data-stu-id="88e90-106">A common use of `#warning` is in a conditional directive.</span></span> <span data-ttu-id="88e90-107">Il est aussi possible de générer une erreur définie par l’utilisateur avec [#error](../../../csharp/language-reference/preprocessor-directives/preprocessor-error.md).</span><span class="sxs-lookup"><span data-stu-id="88e90-107">It is also possible to generate a user-defined error with [#error](../../../csharp/language-reference/preprocessor-directives/preprocessor-error.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="88e90-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="88e90-108">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="88e90-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="88e90-109">See Also</span></span>  
 [<span data-ttu-id="88e90-110">Référence C#</span><span class="sxs-lookup"><span data-stu-id="88e90-110">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="88e90-111">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="88e90-111">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="88e90-112">Directives de préprocesseur C#</span><span class="sxs-lookup"><span data-stu-id="88e90-112">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)
