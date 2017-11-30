---
title: "private (référence C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- private_CSharpKeyword
- private
helpviewer_keywords: private keyword [C#]
ms.assetid: 654c0bb8-e6ac-4086-bf96-7474fa6aa1c8
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d9cc8f86166888b47a758e200182d319c68ca6d4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="private-c-reference"></a><span data-ttu-id="627a5-102">private (référence C#)</span><span class="sxs-lookup"><span data-stu-id="627a5-102">private (C# Reference)</span></span>
<span data-ttu-id="627a5-103">Le mot clé `private` est un modificateur d’accès de membre.</span><span class="sxs-lookup"><span data-stu-id="627a5-103">The `private` keyword is a member access modifier.</span></span> 
   
 > <span data-ttu-id="627a5-104">Cette page traite `private` accès.</span><span class="sxs-lookup"><span data-stu-id="627a5-104">This page covers `private` access.</span></span> <span data-ttu-id="627a5-105">Le `private` le mot clé est également dans le cadre de la [ `private protected` ](./private-protected.md) modificateur d’accès.</span><span class="sxs-lookup"><span data-stu-id="627a5-105">The `private` keyword is also part of the [`private protected`](./private-protected.md) access modifier.</span></span>
  
<span data-ttu-id="627a5-106">L’accès privé est le niveau d’accès le moins permissif.</span><span class="sxs-lookup"><span data-stu-id="627a5-106">Private access is the least permissive access level.</span></span> <span data-ttu-id="627a5-107">Les membres privés sont accessibles uniquement dans le corps de la classe ou le struct dans lequel ils sont déclarés, comme dans cet exemple :</span><span class="sxs-lookup"><span data-stu-id="627a5-107">Private members are accessible only within the body of the class or the struct in which they are declared, as in this example:</span></span>  
  
```  
class Employee  
{  
    private int i;  
    double d;   // private access by default  
}  
```  

 <span data-ttu-id="627a5-108">Les types imbriqués dans le même corps peuvent également accéder à ces membres privés.</span><span class="sxs-lookup"><span data-stu-id="627a5-108">Nested types in the same body can also access those private members.</span></span>  
  
 <span data-ttu-id="627a5-109">Référencer un membre privé en dehors d'une classe ou d'un struct où il est déclaré serait à l'origine d'une erreur de compilation.</span><span class="sxs-lookup"><span data-stu-id="627a5-109">It is a compile-time error to reference a private member outside the class or the struct in which it is declared.</span></span>  
  
 <span data-ttu-id="627a5-110">Pour obtenir une comparaison de `private` et des autres modificateurs d’accès, consultez [Niveaux d’accessibilité](../../../csharp/language-reference/keywords/accessibility-levels.md) et [Modificateurs d’accès](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="627a5-110">For a comparison of `private` with the other access modifiers, see [Accessibility Levels](../../../csharp/language-reference/keywords/accessibility-levels.md) and [Access Modifiers](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="627a5-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="627a5-111">Example</span></span>  
 <span data-ttu-id="627a5-112">Dans cet exemple, la classe `Employee` contient deux membres de données privés, `name` et `salary`.</span><span class="sxs-lookup"><span data-stu-id="627a5-112">In this example, the `Employee` class contains two private data members, `name` and `salary`.</span></span> <span data-ttu-id="627a5-113">S’agissant de membres privés, ils sont accessibles uniquement par les méthodes membres.</span><span class="sxs-lookup"><span data-stu-id="627a5-113">As private members, they cannot be accessed except by member methods.</span></span> <span data-ttu-id="627a5-114">Les méthodes publiques `GetName` et `Salary` sont ajoutées pour permettre un accès contrôlé aux membres privés.</span><span class="sxs-lookup"><span data-stu-id="627a5-114">Public methods named `GetName` and `Salary` are added to allow controlled access to the private members.</span></span> <span data-ttu-id="627a5-115">Le membre `name` est accessible via une méthode publique et le membre `salary` est accessible via une propriété publique en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="627a5-115">The `name` member is accessed by way of a public method, and the `salary` member is accessed by way of a public read-only property.</span></span> <span data-ttu-id="627a5-116">(Pour plus d’informations, consultez [Propriétés](../../../csharp/programming-guide/classes-and-structs/properties.md).)</span><span class="sxs-lookup"><span data-stu-id="627a5-116">(See [Properties](../../../csharp/programming-guide/classes-and-structs/properties.md) for more information.)</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#10](../../../csharp/language-reference/keywords/codesnippet/CSharp/private_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="627a5-117">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="627a5-117">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="627a5-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="627a5-118">See Also</span></span>  
 [<span data-ttu-id="627a5-119">Référence C#</span><span class="sxs-lookup"><span data-stu-id="627a5-119">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="627a5-120">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="627a5-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="627a5-121">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="627a5-121">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="627a5-122">Modificateurs d’accès</span><span class="sxs-lookup"><span data-stu-id="627a5-122">Access Modifiers</span></span>](../../../csharp/language-reference/keywords/access-modifiers.md)  
 [<span data-ttu-id="627a5-123">Niveaux d’accessibilité</span><span class="sxs-lookup"><span data-stu-id="627a5-123">Accessibility Levels</span></span>](../../../csharp/language-reference/keywords/accessibility-levels.md)  
 [<span data-ttu-id="627a5-124">Modificateurs</span><span class="sxs-lookup"><span data-stu-id="627a5-124">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)  
 [<span data-ttu-id="627a5-125">public</span><span class="sxs-lookup"><span data-stu-id="627a5-125">public</span></span>](../../../csharp/language-reference/keywords/public.md)  
 [<span data-ttu-id="627a5-126">protected</span><span class="sxs-lookup"><span data-stu-id="627a5-126">protected</span></span>](../../../csharp/language-reference/keywords/protected.md)  
 [<span data-ttu-id="627a5-127">internal</span><span class="sxs-lookup"><span data-stu-id="627a5-127">internal</span></span>](../../../csharp/language-reference/keywords/internal.md)
