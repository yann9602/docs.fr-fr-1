---
title: "Types référence (référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- cs.referencetypes
dev_langs:
- CSharp
helpviewer_keywords:
- reference types [C#]
- C# language, reference types
- types [C#], reference types
ms.assetid: 801cf030-6e2d-4a0d-9daf-1431b0c31f47
caps.latest.revision: 15
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
ms.openlocfilehash: ed7b9c8ed4aa1136c09049c8ffd6c68beeeb2a48
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="reference-types-c-reference"></a><span data-ttu-id="ff3f0-102">Types référence (référence C#)</span><span class="sxs-lookup"><span data-stu-id="ff3f0-102">Reference Types (C# Reference)</span></span>
<span data-ttu-id="ff3f0-103">Il existe deux genres de types en C# : les types référence et les types valeur.</span><span class="sxs-lookup"><span data-stu-id="ff3f0-103">There are two kinds of types in C#: reference types and value types.</span></span> <span data-ttu-id="ff3f0-104">Les variables des types référence font référence à leurs données (objets), tandis que les variables des types valeur contiennent directement leurs données.</span><span class="sxs-lookup"><span data-stu-id="ff3f0-104">Variables of reference types store references to their data (objects), while variables of value types directly contain their data.</span></span> <span data-ttu-id="ff3f0-105">Avec les types référence, deux variables peuvent faire référence au même objet ; par conséquent, les opérations sur une variable peuvent affecter le même objet référencé par l'autre variable.</span><span class="sxs-lookup"><span data-stu-id="ff3f0-105">With reference types, two variables can reference the same object; therefore, operations on one variable can affect the object referenced by the other variable.</span></span> <span data-ttu-id="ff3f0-106">Avec les types valeur, chaque variable possède sa propre copie des données, et les opérations sur une variable ne peuvent absolument pas affecter l’autre (sauf pour les variables de paramètre ref et out ; consultez [ref](../../../csharp/language-reference/keywords/ref.md) et [out, modificateur de paramètre](../../../csharp/language-reference/keywords/out-parameter-modifier.md)).</span><span class="sxs-lookup"><span data-stu-id="ff3f0-106">With value types, each variable has its own copy of the data, and it is not possible for operations on one variable to affect the other (except in the case of ref and out parameter variables, see [ref](../../../csharp/language-reference/keywords/ref.md) and [out parameter modifier](../../../csharp/language-reference/keywords/out-parameter-modifier.md)).</span></span>  
  
 <span data-ttu-id="ff3f0-107">Les mots clés suivants sont utilisés pour déclarer des types référence :</span><span class="sxs-lookup"><span data-stu-id="ff3f0-107">The following keywords are used to declare reference types:</span></span>  
  
-   [<span data-ttu-id="ff3f0-108">class</span><span class="sxs-lookup"><span data-stu-id="ff3f0-108">class</span></span>](../../../csharp/language-reference/keywords/class.md)  
  
-   [<span data-ttu-id="ff3f0-109">interface</span><span class="sxs-lookup"><span data-stu-id="ff3f0-109">interface</span></span>](../../../csharp/language-reference/keywords/interface.md)  
  
-   [<span data-ttu-id="ff3f0-110">delegate</span><span class="sxs-lookup"><span data-stu-id="ff3f0-110">delegate</span></span>](../../../csharp/language-reference/keywords/delegate.md)  
  
 <span data-ttu-id="ff3f0-111">C# fournit également les types référence intégrés suivants :</span><span class="sxs-lookup"><span data-stu-id="ff3f0-111">C# also provides the following built-in reference types:</span></span>  
  
-   [<span data-ttu-id="ff3f0-112">dynamic</span><span class="sxs-lookup"><span data-stu-id="ff3f0-112">dynamic</span></span>](../../../csharp/language-reference/keywords/dynamic.md)  
  
-   [<span data-ttu-id="ff3f0-113">object</span><span class="sxs-lookup"><span data-stu-id="ff3f0-113">object</span></span>](../../../csharp/language-reference/keywords/object.md)  
  
-   [<span data-ttu-id="ff3f0-114">string</span><span class="sxs-lookup"><span data-stu-id="ff3f0-114">string</span></span>](../../../csharp/language-reference/keywords/string.md)  
  
## <a name="see-also"></a><span data-ttu-id="ff3f0-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ff3f0-115">See Also</span></span>  
 <span data-ttu-id="ff3f0-116">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="ff3f0-116">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="ff3f0-117">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="ff3f0-117">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="ff3f0-118">[Mots clés C#](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="ff3f0-118">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="ff3f0-119">[Types](../../../csharp/language-reference/keywords/types.md) </span><span class="sxs-lookup"><span data-stu-id="ff3f0-119">[Types](../../../csharp/language-reference/keywords/types.md) </span></span>  
 [<span data-ttu-id="ff3f0-120">Types valeur</span><span class="sxs-lookup"><span data-stu-id="ff3f0-120">Value Types</span></span>](../../../csharp/language-reference/keywords/value-types.md)

