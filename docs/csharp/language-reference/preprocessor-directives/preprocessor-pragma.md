---
title: "#<a name=\"pragma-c-reference\"></a>pragma (informations de référence sur C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '#pragma'
dev_langs:
- CSharp
helpviewer_keywords:
- '#pragma directive [C#]'
ms.assetid: 5b7944cd-d402-46a1-ad8f-feffb2d83673
caps.latest.revision: 18
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
ms.openlocfilehash: e03fc387b105c1dee3b7fed93263ad8ef22d5934
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="pragma-c-reference"></a><span data-ttu-id="2434b-102">#pragma (informations de référence sur C#)</span><span class="sxs-lookup"><span data-stu-id="2434b-102">#pragma (C# Reference)</span></span>
<span data-ttu-id="2434b-103">La directive `#pragma` fournit au compilateur des instructions spéciales pour la compilation du fichier dans lequel elle apparaît.</span><span class="sxs-lookup"><span data-stu-id="2434b-103">`#pragma` gives the compiler special instructions for the compilation of the file in which it appears.</span></span> <span data-ttu-id="2434b-104">Les instructions doivent être prises en charge par le compilateur.</span><span class="sxs-lookup"><span data-stu-id="2434b-104">The instructions must be supported by the compiler.</span></span> <span data-ttu-id="2434b-105">En d’autres termes, vous ne pouvez pas utiliser `#pragma` pour créer des instructions de prétraitement personnalisées.</span><span class="sxs-lookup"><span data-stu-id="2434b-105">In other words, you cannot use `#pragma` to create custom preprocessing instructions.</span></span> <span data-ttu-id="2434b-106">Le compilateur Microsoft C# prend en charge les deux instructions `#pragma` suivantes :</span><span class="sxs-lookup"><span data-stu-id="2434b-106">The Microsoft C# compiler supports the following two `#pragma` instructions:</span></span>  
  
 [<span data-ttu-id="2434b-107">#pragma warning</span><span class="sxs-lookup"><span data-stu-id="2434b-107">#pragma warning</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md)  
  
 [<span data-ttu-id="2434b-108">#pragma checksum</span><span class="sxs-lookup"><span data-stu-id="2434b-108">#pragma checksum</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-checksum.md)  
  
## <a name="syntax"></a><span data-ttu-id="2434b-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2434b-109">Syntax</span></span>  
  
```csharp
#pragma pragma-name pragma-arguments  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2434b-110">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2434b-110">Parameters</span></span>  
 `pragma-name`  
 <span data-ttu-id="2434b-111">Nom d’une directive pragma reconnue.</span><span class="sxs-lookup"><span data-stu-id="2434b-111">The name of a recognized pragma.</span></span>  
  
 `pragma-arguments`  
 <span data-ttu-id="2434b-112">Arguments propres à la directive pragma.</span><span class="sxs-lookup"><span data-stu-id="2434b-112">Pragma-specific arguments.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2434b-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2434b-113">See Also</span></span>  
 <span data-ttu-id="2434b-114">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="2434b-114">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="2434b-115">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="2434b-115">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="2434b-116">[Directives de préprocesseur C#](../../../csharp/language-reference/preprocessor-directives/index.md) </span><span class="sxs-lookup"><span data-stu-id="2434b-116">[C# Preprocessor Directives](../../../csharp/language-reference/preprocessor-directives/index.md) </span></span>  
 <span data-ttu-id="2434b-117">[#pragma warning](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md) </span><span class="sxs-lookup"><span data-stu-id="2434b-117">[#pragma warning](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md) </span></span>  
 [<span data-ttu-id="2434b-118">#pragma checksum</span><span class="sxs-lookup"><span data-stu-id="2434b-118">#pragma checksum</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-checksum.md)

