---
title: "public (référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- public
- public_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- public keyword [C#]
ms.assetid: 0ae45d16-a551-4b74-9845-57208de1328e
caps.latest.revision: 21
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
ms.openlocfilehash: ae19bf9a33a9860a8960cde5dd4402e10418a094
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="public-c-reference"></a><span data-ttu-id="1ae52-102">public (référence C#)</span><span class="sxs-lookup"><span data-stu-id="1ae52-102">public (C# Reference)</span></span>
<span data-ttu-id="1ae52-103">Le mot clé `public` est un modificateur d’accès pour les types et les membres de types.</span><span class="sxs-lookup"><span data-stu-id="1ae52-103">The `public` keyword is an access modifier for types and type members.</span></span> <span data-ttu-id="1ae52-104">L’accès public est le niveau d’accès le plus permissif.</span><span class="sxs-lookup"><span data-stu-id="1ae52-104">Public access is the most permissive access level.</span></span> <span data-ttu-id="1ae52-105">Il n’existe pas de restrictions d’accès aux membres publics, comme dans cet exemple :</span><span class="sxs-lookup"><span data-stu-id="1ae52-105">There are no restrictions on accessing public members, as in this example:</span></span>  
  
```  
class SampleClass  
{  
    public int x; // No access restrictions.  
}  
```  
  
 <span data-ttu-id="1ae52-106">Pour plus d’informations, consultez [Modificateurs d’accès](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md) et [Niveaux d’accessibilité](../../../csharp/language-reference/keywords/accessibility-levels.md).</span><span class="sxs-lookup"><span data-stu-id="1ae52-106">See [Access Modifiers](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md) and [Accessibility Levels](../../../csharp/language-reference/keywords/accessibility-levels.md) for more information.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1ae52-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="1ae52-107">Example</span></span>  
 <span data-ttu-id="1ae52-108">Dans l’exemple suivant, deux classes sont déclarées, `PointTest` et `MainClass`.</span><span class="sxs-lookup"><span data-stu-id="1ae52-108">In the following example, two classes are declared, `PointTest` and `MainClass`.</span></span> <span data-ttu-id="1ae52-109">L’accès aux membres publics `x` et `y` de `PointTest` s’effectue directement à partir de `MainClass`.</span><span class="sxs-lookup"><span data-stu-id="1ae52-109">The public members `x` and `y` of `PointTest` are accessed directly from `MainClass`.</span></span>  
  
 <span data-ttu-id="1ae52-110">[!code-cs[csrefKeywordsModifiers#13](../../../csharp/language-reference/keywords/codesnippet/CSharp/public_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="1ae52-110">[!code-cs[csrefKeywordsModifiers#13](../../../csharp/language-reference/keywords/codesnippet/CSharp/public_1.cs)]</span></span>  
  
 <span data-ttu-id="1ae52-111">Si vous remplacez le niveau d’accès `public` par [private](../../../csharp/language-reference/keywords/private.md) ou [protected](../../../csharp/language-reference/keywords/protected.md), le message d’erreur suivant s’affiche :</span><span class="sxs-lookup"><span data-stu-id="1ae52-111">If you change the `public` access level to [private](../../../csharp/language-reference/keywords/private.md) or [protected](../../../csharp/language-reference/keywords/protected.md), you will get the error message:</span></span>  
  
 <span data-ttu-id="1ae52-112">'PointTest.y' est inaccessible en raison de son niveau de protection.</span><span class="sxs-lookup"><span data-stu-id="1ae52-112">'PointTest.y' is inaccessible due to its protection level.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="1ae52-113">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="1ae52-113">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="1ae52-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1ae52-114">See Also</span></span>  
 <span data-ttu-id="1ae52-115">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="1ae52-115">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="1ae52-116">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="1ae52-116">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="1ae52-117">[Modificateurs d’accès](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md) </span><span class="sxs-lookup"><span data-stu-id="1ae52-117">[Access Modifiers](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md) </span></span>  
 <span data-ttu-id="1ae52-118">[Mots clés C#](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="1ae52-118">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="1ae52-119">[Modificateurs d’accès](../../../csharp/language-reference/keywords/access-modifiers.md) </span><span class="sxs-lookup"><span data-stu-id="1ae52-119">[Access Modifiers](../../../csharp/language-reference/keywords/access-modifiers.md) </span></span>  
 <span data-ttu-id="1ae52-120">[Niveaux d’accessibilité](../../../csharp/language-reference/keywords/accessibility-levels.md) </span><span class="sxs-lookup"><span data-stu-id="1ae52-120">[Accessibility Levels](../../../csharp/language-reference/keywords/accessibility-levels.md) </span></span>  
 <span data-ttu-id="1ae52-121">[Modificateurs](../../../csharp/language-reference/keywords/modifiers.md) </span><span class="sxs-lookup"><span data-stu-id="1ae52-121">[Modifiers](../../../csharp/language-reference/keywords/modifiers.md) </span></span>  
 <span data-ttu-id="1ae52-122">[private](../../../csharp/language-reference/keywords/private.md) </span><span class="sxs-lookup"><span data-stu-id="1ae52-122">[private](../../../csharp/language-reference/keywords/private.md) </span></span>  
 <span data-ttu-id="1ae52-123">[protected](../../../csharp/language-reference/keywords/protected.md) </span><span class="sxs-lookup"><span data-stu-id="1ae52-123">[protected](../../../csharp/language-reference/keywords/protected.md) </span></span>  
 [<span data-ttu-id="1ae52-124">internal</span><span class="sxs-lookup"><span data-stu-id="1ae52-124">internal</span></span>](../../../csharp/language-reference/keywords/internal.md)

