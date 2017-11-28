---
title: "Paramètres de méthode (référence C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- methods [C#], parameters
- method parameters [C#]
- parameters [C#]
ms.assetid: 680e39ff-775b-48b0-9f47-4186a5bfc4a1
caps.latest.revision: "8"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 924e261cc876d2428e28ed0f490beb46b95f96e6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="method-parameters-c-reference"></a><span data-ttu-id="53d93-102">Paramètres de méthode (référence C#)</span><span class="sxs-lookup"><span data-stu-id="53d93-102">Method Parameters (C# Reference)</span></span>
<span data-ttu-id="53d93-103">Si un paramètre est déclaré pour une méthode sans [ref](../../../csharp/language-reference/keywords/ref.md) ou [out](../../../csharp/language-reference/keywords/out.md), il peut avoir une valeur associée.</span><span class="sxs-lookup"><span data-stu-id="53d93-103">If a parameter is declared for a method without [ref](../../../csharp/language-reference/keywords/ref.md) or [out](../../../csharp/language-reference/keywords/out.md), the parameter can have a value associated with it.</span></span> <span data-ttu-id="53d93-104">Cette valeur peut être modifiée dans la méthode, mais la valeur modifiée n’est pas conservée quand le contrôle repasse à la procédure appelante.</span><span class="sxs-lookup"><span data-stu-id="53d93-104">That value can be changed in the method, but the changed value will not be retained when control passes back to the calling procedure.</span></span> <span data-ttu-id="53d93-105">En utilisant un mot clé de paramètre de méthode, vous pouvez modifier ce comportement.</span><span class="sxs-lookup"><span data-stu-id="53d93-105">By using a method parameter keyword, you can change this behavior.</span></span>  
  
 <span data-ttu-id="53d93-106">Cette section décrit les mots clés que vous pouvez utiliser pour déclarer des paramètres de méthode :</span><span class="sxs-lookup"><span data-stu-id="53d93-106">This section describes the keywords you can use when declaring method parameters:</span></span>  
  
-   [<span data-ttu-id="53d93-107">params</span><span class="sxs-lookup"><span data-stu-id="53d93-107">params</span></span>](../../../csharp/language-reference/keywords/params.md)  
  
-   [<span data-ttu-id="53d93-108">ref</span><span class="sxs-lookup"><span data-stu-id="53d93-108">ref</span></span>](../../../csharp/language-reference/keywords/ref.md)  
  
-   [<span data-ttu-id="53d93-109">out</span><span class="sxs-lookup"><span data-stu-id="53d93-109">out</span></span>](../../../csharp/language-reference/keywords/out.md)  
  
## <a name="see-also"></a><span data-ttu-id="53d93-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="53d93-110">See Also</span></span>  
 [<span data-ttu-id="53d93-111">Référence C#</span><span class="sxs-lookup"><span data-stu-id="53d93-111">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="53d93-112">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="53d93-112">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="53d93-113">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="53d93-113">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)
