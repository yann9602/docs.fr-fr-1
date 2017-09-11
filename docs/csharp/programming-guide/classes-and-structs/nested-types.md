---
title: "Types imbriqués (guide de programmation C#)"
ms.date: 2017-07-10
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- nested types [C#]
ms.assetid: f2e1b315-e3d1-48ce-977f-7bae0960ba99
caps.latest.revision: 13
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 853ec746d9be01ed63d7a229ca86e99d9f192374
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="nested-types-c-programming-guide"></a><span data-ttu-id="481cb-102">Types imbriqués (guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="481cb-102">Nested Types (C# Programming Guide)</span></span>
<span data-ttu-id="481cb-103">Un type défini dans une [classe](../../../csharp/language-reference/keywords/class.md) ou un [struct](../../../csharp/language-reference/keywords/struct.md) s’appelle un type imbriqué.</span><span class="sxs-lookup"><span data-stu-id="481cb-103">A type defined within a [class](../../../csharp/language-reference/keywords/class.md) or [struct](../../../csharp/language-reference/keywords/struct.md) is called a nested type.</span></span> <span data-ttu-id="481cb-104">Exemple :</span><span class="sxs-lookup"><span data-stu-id="481cb-104">For example:</span></span>  
  
<span data-ttu-id="481cb-105">[!code-cs[csProgGuideObjects#68](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/nested-types_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="481cb-105">[!code-cs[csProgGuideObjects#68](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/nested-types_1.cs)]</span></span>  
  
<span data-ttu-id="481cb-106">Que le type externe soit une classe ou un struct, les types imbriqués sont par défaut [private](../../../csharp/language-reference/keywords/private.md) ; ils sont accessibles uniquement à partir de leur type conteneur.</span><span class="sxs-lookup"><span data-stu-id="481cb-106">Regardless of whether the outer type is a class or a struct, nested types default to [private](../../../csharp/language-reference/keywords/private.md); they are accessible only from their containing type.</span></span> <span data-ttu-id="481cb-107">Dans l’exemple précédent, la classe `Nested` est inaccessible aux types externes.</span><span class="sxs-lookup"><span data-stu-id="481cb-107">In the previous example, the `Nested` class is inaccessible to external types.</span></span> 

<span data-ttu-id="481cb-108">Vous pouvez aussi spécifier un [modificateur d’accès](../../language-reference/keywords/access-modifiers.md) pour définir l’accessibilité d’un type imbriqué, comme ceci :</span><span class="sxs-lookup"><span data-stu-id="481cb-108">You can also specify an [access modifier](../../language-reference/keywords/access-modifiers.md) to define the accessibility of a nested type, as follows:</span></span>

- <span data-ttu-id="481cb-109">Les types imbriqués d’une **classe** peuvent être [public](../../../csharp/language-reference/keywords/public.md), [protected](../../../csharp/language-reference/keywords/protected.md), [internal](../../../csharp/language-reference/keywords/internal.md), `protected internal` ou [private](../../../csharp/language-reference/keywords/private.md).</span><span class="sxs-lookup"><span data-stu-id="481cb-109">Nested types of a **class** can be [public](../../../csharp/language-reference/keywords/public.md), [protected](../../../csharp/language-reference/keywords/protected.md), [internal](../../../csharp/language-reference/keywords/internal.md), `protected internal`, or [private](../../../csharp/language-reference/keywords/private.md).</span></span> 

   <span data-ttu-id="481cb-110">Cependant, le fait de définir une classe imbriquée `protected` ou `protected internal` à l’intérieur d’une [classe sealed](../../language-reference/keywords/sealed.md) a pour effet de générer l’avertissement de compilateur [CS0628](../../misc/cs0628.md), « nouveau membre protected déclaré dans une classe sealed ».</span><span class="sxs-lookup"><span data-stu-id="481cb-110">However, defining a `protected` or `protected internal` nested class inside a [sealed class](../../language-reference/keywords/sealed.md) generates compiler warning [CS0628](../../misc/cs0628.md), "new protected member declared in sealed class."</span></span>
  
- <span data-ttu-id="481cb-111">Les types imbriqués d’un **struct** peuvent être [public](../../../csharp/language-reference/keywords/public.md), [internal](../../../csharp/language-reference/keywords/internal.md) ou [private](../../../csharp/language-reference/keywords/private.md).</span><span class="sxs-lookup"><span data-stu-id="481cb-111">Nested types of a **struct** can be [public](../../../csharp/language-reference/keywords/public.md), [internal](../../../csharp/language-reference/keywords/internal.md), or [private](../../../csharp/language-reference/keywords/private.md).</span></span>
  
<span data-ttu-id="481cb-112">L’exemple suivant fait passer le type de la classe `Nested` à public :</span><span class="sxs-lookup"><span data-stu-id="481cb-112">The following example makes the `Nested` class public:</span></span>
  
<span data-ttu-id="481cb-113">[!code-cs[csProgGuideObjects#69](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/nested-types_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="481cb-113">[!code-cs[csProgGuideObjects#69](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/nested-types_2.cs)]</span></span>  
  
 <span data-ttu-id="481cb-114">Le type imbriqué (ou interne) peut accéder au type conteneur (ou externe).</span><span class="sxs-lookup"><span data-stu-id="481cb-114">The nested, or inner, type can access the containing, or outer, type.</span></span> <span data-ttu-id="481cb-115">Pour accéder au type conteneur, passez-le en tant qu’argument au constructeur du type imbriqué.</span><span class="sxs-lookup"><span data-stu-id="481cb-115">To access the containing type, pass it as an argument to the constructor of the nested type.</span></span> <span data-ttu-id="481cb-116">Exemple :</span><span class="sxs-lookup"><span data-stu-id="481cb-116">For example:</span></span>  
  
 <span data-ttu-id="481cb-117">[!code-cs[csProgGuideObjects#70](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/nested-types_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="481cb-117">[!code-cs[csProgGuideObjects#70](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/nested-types_3.cs)]</span></span>  
  
 <span data-ttu-id="481cb-118">Un type imbriqué a accès à tous les membres qui sont accessibles à son type conteneur.</span><span class="sxs-lookup"><span data-stu-id="481cb-118">A nested type has access to all of the members that are accessible to its containing type.</span></span> <span data-ttu-id="481cb-119">Il peut accéder aux membres privés et protégés du type conteneur, y compris à tous les membres protégés hérités.</span><span class="sxs-lookup"><span data-stu-id="481cb-119">It can access private and protected members of the containing type, including any inherited protected members.</span></span>  
  
 <span data-ttu-id="481cb-120">Dans la déclaration précédente, le nom complet de classe `Nested` est `Container.Nested`.</span><span class="sxs-lookup"><span data-stu-id="481cb-120">In the previous declaration, the full name of class `Nested` is `Container.Nested`.</span></span> <span data-ttu-id="481cb-121">Il s'agit du nom utilisé pour créer une instance de la classe imbriquée, comme suit :</span><span class="sxs-lookup"><span data-stu-id="481cb-121">This is the name used to create a new instance of the nested class, as follows:</span></span>  
  
 <span data-ttu-id="481cb-122">[!code-cs[csProgGuideObjects#71](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/nested-types_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="481cb-122">[!code-cs[csProgGuideObjects#71](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/nested-types_4.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="481cb-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="481cb-123">See Also</span></span>  
 <span data-ttu-id="481cb-124">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="481cb-124">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="481cb-125">[Classes et structs](../../../csharp/programming-guide/classes-and-structs/index.md) </span><span class="sxs-lookup"><span data-stu-id="481cb-125">[Classes and Structs](../../../csharp/programming-guide/classes-and-structs/index.md) </span></span>  
 <span data-ttu-id="481cb-126">[Modificateurs d’accès](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md) </span><span class="sxs-lookup"><span data-stu-id="481cb-126">[Access Modifiers](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md) </span></span>  
 [<span data-ttu-id="481cb-127">Constructeurs</span><span class="sxs-lookup"><span data-stu-id="481cb-127">Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/constructors.md)

