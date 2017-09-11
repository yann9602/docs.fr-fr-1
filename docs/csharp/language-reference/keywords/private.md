---
title: "private (référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- private_CSharpKeyword
- private
dev_langs:
- CSharp
helpviewer_keywords:
- private keyword [C#]
ms.assetid: 654c0bb8-e6ac-4086-bf96-7474fa6aa1c8
caps.latest.revision: 17
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
ms.openlocfilehash: c18fd87b12bf3f7f1a1d1ef0dfded8643308169c
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="private-c-reference"></a><span data-ttu-id="db073-102">private (référence C#)</span><span class="sxs-lookup"><span data-stu-id="db073-102">private (C# Reference)</span></span>
<span data-ttu-id="db073-103">Le mot clé `private` est un modificateur d’accès de membre.</span><span class="sxs-lookup"><span data-stu-id="db073-103">The `private` keyword is a member access modifier.</span></span> <span data-ttu-id="db073-104">L’accès privé est le niveau d’accès le moins permissif.</span><span class="sxs-lookup"><span data-stu-id="db073-104">Private access is the least permissive access level.</span></span> <span data-ttu-id="db073-105">Les membres privés sont accessibles uniquement dans le corps de la classe ou le struct dans lequel ils sont déclarés, comme dans cet exemple :</span><span class="sxs-lookup"><span data-stu-id="db073-105">Private members are accessible only within the body of the class or the struct in which they are declared, as in this example:</span></span>  
  
```  
class Employee  
{  
    private int i;  
    double d;   // private access by default  
}  
```  
  
 <span data-ttu-id="db073-106">Les types imbriqués dans le même corps peuvent également accéder à ces membres privés.</span><span class="sxs-lookup"><span data-stu-id="db073-106">Nested types in the same body can also access those private members.</span></span>  
  
 <span data-ttu-id="db073-107">Référencer un membre privé en dehors d'une classe ou d'un struct où il est déclaré serait à l'origine d'une erreur de compilation.</span><span class="sxs-lookup"><span data-stu-id="db073-107">It is a compile-time error to reference a private member outside the class or the struct in which it is declared.</span></span>  
  
 <span data-ttu-id="db073-108">Pour obtenir une comparaison de `private` et des autres modificateurs d’accès, consultez [Niveaux d’accessibilité](../../../csharp/language-reference/keywords/accessibility-levels.md) et [Modificateurs d’accès](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="db073-108">For a comparison of `private` with the other access modifiers, see [Accessibility Levels](../../../csharp/language-reference/keywords/accessibility-levels.md) and [Access Modifiers](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="db073-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="db073-109">Example</span></span>  
 <span data-ttu-id="db073-110">Dans cet exemple, la classe `Employee` contient deux membres de données privés, `name` et `salary`.</span><span class="sxs-lookup"><span data-stu-id="db073-110">In this example, the `Employee` class contains two private data members, `name` and `salary`.</span></span> <span data-ttu-id="db073-111">S’agissant de membres privés, ils sont accessibles uniquement par les méthodes membres.</span><span class="sxs-lookup"><span data-stu-id="db073-111">As private members, they cannot be accessed except by member methods.</span></span> <span data-ttu-id="db073-112">Les méthodes publiques `GetName` et `Salary` sont ajoutées pour permettre un accès contrôlé aux membres privés.</span><span class="sxs-lookup"><span data-stu-id="db073-112">Public methods named `GetName` and `Salary` are added to allow controlled access to the private members.</span></span> <span data-ttu-id="db073-113">Le membre `name` est accessible via une méthode publique et le membre `salary` est accessible via une propriété publique en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="db073-113">The `name` member is accessed by way of a public method, and the `salary` member is accessed by way of a public read-only property.</span></span> <span data-ttu-id="db073-114">(Pour plus d’informations, consultez [Propriétés](../../../csharp/programming-guide/classes-and-structs/properties.md).)</span><span class="sxs-lookup"><span data-stu-id="db073-114">(See [Properties](../../../csharp/programming-guide/classes-and-structs/properties.md) for more information.)</span></span>  
  
 <span data-ttu-id="db073-115">[!code-cs[csrefKeywordsModifiers#10](../../../csharp/language-reference/keywords/codesnippet/CSharp/private_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="db073-115">[!code-cs[csrefKeywordsModifiers#10](../../../csharp/language-reference/keywords/codesnippet/CSharp/private_1.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="db073-116">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="db073-116">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="db073-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="db073-117">See Also</span></span>  
 <span data-ttu-id="db073-118">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="db073-118">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="db073-119">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="db073-119">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="db073-120">[Mots clés C#](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="db073-120">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="db073-121">[Modificateurs d’accès](../../../csharp/language-reference/keywords/access-modifiers.md) </span><span class="sxs-lookup"><span data-stu-id="db073-121">[Access Modifiers](../../../csharp/language-reference/keywords/access-modifiers.md) </span></span>  
 <span data-ttu-id="db073-122">[Niveaux d’accessibilité](../../../csharp/language-reference/keywords/accessibility-levels.md) </span><span class="sxs-lookup"><span data-stu-id="db073-122">[Accessibility Levels](../../../csharp/language-reference/keywords/accessibility-levels.md) </span></span>  
 <span data-ttu-id="db073-123">[Modificateurs](../../../csharp/language-reference/keywords/modifiers.md) </span><span class="sxs-lookup"><span data-stu-id="db073-123">[Modifiers](../../../csharp/language-reference/keywords/modifiers.md) </span></span>  
 <span data-ttu-id="db073-124">[public](../../../csharp/language-reference/keywords/public.md) </span><span class="sxs-lookup"><span data-stu-id="db073-124">[public](../../../csharp/language-reference/keywords/public.md) </span></span>  
 <span data-ttu-id="db073-125">[protected](../../../csharp/language-reference/keywords/protected.md) </span><span class="sxs-lookup"><span data-stu-id="db073-125">[protected](../../../csharp/language-reference/keywords/protected.md) </span></span>  
 [<span data-ttu-id="db073-126">internal</span><span class="sxs-lookup"><span data-stu-id="db073-126">internal</span></span>](../../../csharp/language-reference/keywords/internal.md)

