---
title: ". , opérateur (Informations de référence sur C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- ._CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- member access operator (.) [C#]
- . operator [C#]
- dot operator (.) [C#]
ms.assetid: a1f54b52-b686-4ae5-a48e-a2a9ebd0eb7b
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
ms.openlocfilehash: fdc7c1821548509f3a3750aef2836c034f7aa53b
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="-operator-c-reference"></a><span data-ttu-id="bd892-103">.</span><span class="sxs-lookup"><span data-stu-id="bd892-103">.</span></span> <span data-ttu-id="bd892-104">, opérateur (Informations de référence sur C#)</span><span class="sxs-lookup"><span data-stu-id="bd892-104">Operator (C# Reference)</span></span>
<span data-ttu-id="bd892-105">L’opérateur point (`.`) est l’opérateur d’accès aux membres .</span><span class="sxs-lookup"><span data-stu-id="bd892-105">The dot operator (`.`) is used for member access.</span></span> <span data-ttu-id="bd892-106">L’opérateur point spécifie un membre d’un type ou d’espace de noms.</span><span class="sxs-lookup"><span data-stu-id="bd892-106">The dot operator specifies a member of a type or namespace.</span></span> <span data-ttu-id="bd892-107">Par exemple, l’opérateur point est utilisé pour accéder aux méthodes spécifiques figurant dans les bibliothèques de classes du .NET Framework :</span><span class="sxs-lookup"><span data-stu-id="bd892-107">For example, the dot operator is used to access specific methods within the .NET Framework class libraries:</span></span>  
  
 <span data-ttu-id="bd892-108">[!code-cs[csRefOperators#16](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="bd892-108">[!code-cs[csRefOperators#16](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_1.cs)]</span></span>  
  
 <span data-ttu-id="bd892-109">Par exemple, considérons la classe suivante :</span><span class="sxs-lookup"><span data-stu-id="bd892-109">For example, consider the following class:</span></span>  
  
 <span data-ttu-id="bd892-110">[!code-cs[csRefOperators#17](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="bd892-110">[!code-cs[csRefOperators#17](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_2.cs)]</span></span>  
  
 <span data-ttu-id="bd892-111">[!code-cs[csRefOperators#18](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="bd892-111">[!code-cs[csRefOperators#18](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_3.cs)]</span></span>  
  
 <span data-ttu-id="bd892-112">La variable `s` a deux membres, `a` et `b` ; pour y accéder, utilisez l’opérateur point :</span><span class="sxs-lookup"><span data-stu-id="bd892-112">The variable `s` has two members, `a` and `b`; to access them, use the dot operator:</span></span>  
  
 <span data-ttu-id="bd892-113">[!code-cs[csRefOperators#19](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="bd892-113">[!code-cs[csRefOperators#19](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_4.cs)]</span></span>  
  
 <span data-ttu-id="bd892-114">Le point est aussi utilisé pour former des noms qualifiés, c’est-à-dire des noms qui spécifient par exemple l’espace de noms ou une interface auquel ils appartiennent.</span><span class="sxs-lookup"><span data-stu-id="bd892-114">The dot is also used to form qualified names, which are names that specify the namespace or interface, for example, to which they belong.</span></span>  
  
 <span data-ttu-id="bd892-115">[!code-cs[csRefOperators#20](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_5.cs)]</span><span class="sxs-lookup"><span data-stu-id="bd892-115">[!code-cs[csRefOperators#20](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_5.cs)]</span></span>  
  
 <span data-ttu-id="bd892-116">La directive using rend la qualification de certains noms facultative :</span><span class="sxs-lookup"><span data-stu-id="bd892-116">The using directive makes some name qualification optional:</span></span>  
  
 <span data-ttu-id="bd892-117">[!code-cs[csRefOperators#21](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_6.cs)]</span><span class="sxs-lookup"><span data-stu-id="bd892-117">[!code-cs[csRefOperators#21](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_6.cs)]</span></span>  
  
 <span data-ttu-id="bd892-118">Cependant, quand un identificateur est ambigu, il doit être qualifié :</span><span class="sxs-lookup"><span data-stu-id="bd892-118">But when an identifier is ambiguous, it must be qualified:</span></span>  
  
 <span data-ttu-id="bd892-119">[!code-cs[csRefOperators#22](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_7.cs)]</span><span class="sxs-lookup"><span data-stu-id="bd892-119">[!code-cs[csRefOperators#22](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_7.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="bd892-120">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="bd892-120">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="bd892-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bd892-121">See Also</span></span>  
 <span data-ttu-id="bd892-122">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="bd892-122">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="bd892-123">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="bd892-123">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="bd892-124">Opérateurs C#</span><span class="sxs-lookup"><span data-stu-id="bd892-124">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)

