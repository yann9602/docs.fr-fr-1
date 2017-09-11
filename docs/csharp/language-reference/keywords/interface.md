---
title: "interface (référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- interface_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- interface keyword [C#]
ms.assetid: 7da38e81-4f99-4bc5-b07d-c986b687eeba
caps.latest.revision: 29
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
ms.openlocfilehash: 126e674a2c56f04f54f35a011c24ebf0f713ee8d
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="interface-c-reference"></a><span data-ttu-id="04c56-102">interface (référence C#)</span><span class="sxs-lookup"><span data-stu-id="04c56-102">interface (C# Reference)</span></span>
<span data-ttu-id="04c56-103">Une interface contient uniquement des signatures de [méthodes](../../../csharp/programming-guide/classes-and-structs/methods.md), de [propriétés](../../../csharp/programming-guide/classes-and-structs/properties.md), d’[événements](../../../csharp/programming-guide/events/index.md) ou d’[indexeurs](../../../csharp/programming-guide/indexers/index.md).</span><span class="sxs-lookup"><span data-stu-id="04c56-103">An interface contains only the signatures of [methods](../../../csharp/programming-guide/classes-and-structs/methods.md), [properties](../../../csharp/programming-guide/classes-and-structs/properties.md), [events](../../../csharp/programming-guide/events/index.md) or [indexers](../../../csharp/programming-guide/indexers/index.md).</span></span> <span data-ttu-id="04c56-104">Une classe ou un struct qui implémente l’interface doit implémenter les membres de l’interface qui sont spécifiés dans la définition de l’interface.</span><span class="sxs-lookup"><span data-stu-id="04c56-104">A class or struct that implements the interface must implement the members of the interface that are specified in the interface definition.</span></span> <span data-ttu-id="04c56-105">Dans l’exemple suivant, la classe `ImplementationClass` doit implémenter une méthode nommée `SampleMethod` qui n’a aucun paramètre et qui retourne `void`.</span><span class="sxs-lookup"><span data-stu-id="04c56-105">In the following example, class `ImplementationClass` must implement a method named `SampleMethod` that has no parameters and returns `void`.</span></span>  
  
 <span data-ttu-id="04c56-106">Pour plus d’informations et d’exemples, consultez [Interfaces](../../../csharp/programming-guide/interfaces/index.md).</span><span class="sxs-lookup"><span data-stu-id="04c56-106">For more information and examples, see [Interfaces](../../../csharp/programming-guide/interfaces/index.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="04c56-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="04c56-107">Example</span></span>  
 <span data-ttu-id="04c56-108">[!code-cs[csrefKeywordsTypes#14](../../../csharp/language-reference/keywords/codesnippet/CSharp/interface_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="04c56-108">[!code-cs[csrefKeywordsTypes#14](../../../csharp/language-reference/keywords/codesnippet/CSharp/interface_1.cs)]</span></span>  
  
 <span data-ttu-id="04c56-109">Une interface peut être membre d’un espace de noms ou d’une classe, et peut contenir les signatures des membres suivants :</span><span class="sxs-lookup"><span data-stu-id="04c56-109">An interface can be a member of a namespace or a class and can contain signatures of the following members:</span></span>  
  
-   [<span data-ttu-id="04c56-110">Méthodes</span><span class="sxs-lookup"><span data-stu-id="04c56-110">Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/methods.md)  
  
-   [<span data-ttu-id="04c56-111">Propriétés</span><span class="sxs-lookup"><span data-stu-id="04c56-111">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/using-properties.md)  
  
-   [<span data-ttu-id="04c56-112">Indexeurs</span><span class="sxs-lookup"><span data-stu-id="04c56-112">Indexers</span></span>](../../../csharp/programming-guide/indexers/using-indexers.md)  
  
-   [<span data-ttu-id="04c56-113">Événements</span><span class="sxs-lookup"><span data-stu-id="04c56-113">Events</span></span>](../../../csharp/language-reference/keywords/event.md)  
  
 <span data-ttu-id="04c56-114">Une interface peut hériter d’une ou de plusieurs interfaces de base.</span><span class="sxs-lookup"><span data-stu-id="04c56-114">An interface can inherit from one or more base interfaces.</span></span>  
  
 <span data-ttu-id="04c56-115">Lorsqu’une liste de types de base contient une classe de base et des interfaces, la classe de base doit figurer en premier dans la liste.</span><span class="sxs-lookup"><span data-stu-id="04c56-115">When a base type list contains a base class and interfaces, the base class must come first in the list.</span></span>  
  
 <span data-ttu-id="04c56-116">Une classe qui implémente une interface peut implémenter explicitement les membres de cette interface.</span><span class="sxs-lookup"><span data-stu-id="04c56-116">A class that implements an interface can explicitly implement members of that interface.</span></span> <span data-ttu-id="04c56-117">Un membre implémenté explicitement n’est pas accessible via une instance de classe, mais uniquement via une instance de l’interface.</span><span class="sxs-lookup"><span data-stu-id="04c56-117">An explicitly implemented member cannot be accessed through a class instance, but only through an instance of the interface.</span></span>  
  
 <span data-ttu-id="04c56-118">Pour plus d’informations et plus d’exemples sur l’implémentation explicite des interfaces, consultez [Implémentation d’interface explicite](../../../csharp/programming-guide/interfaces/explicit-interface-implementation.md).</span><span class="sxs-lookup"><span data-stu-id="04c56-118">For more details and code examples on explicit interface implementation, see [Explicit Interface Implementation](../../../csharp/programming-guide/interfaces/explicit-interface-implementation.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="04c56-119">Exemple</span><span class="sxs-lookup"><span data-stu-id="04c56-119">Example</span></span>  
 <span data-ttu-id="04c56-120">L’exemple suivant montre une implémentation d’interface.</span><span class="sxs-lookup"><span data-stu-id="04c56-120">The following example demonstrates interface implementation.</span></span> <span data-ttu-id="04c56-121">Dans cet exemple, l’interface contient la déclaration de propriété, et la classe contient l’implémentation.</span><span class="sxs-lookup"><span data-stu-id="04c56-121">In this example, the interface contains the property declaration and the class contains the implementation.</span></span> <span data-ttu-id="04c56-122">Toutes les instances d’une classe qui implémentent `IPoint` ont les propriétés entières `x` et `y`.</span><span class="sxs-lookup"><span data-stu-id="04c56-122">Any instance of a class that implements `IPoint` has integer properties `x` and `y`.</span></span>  
  
 <span data-ttu-id="04c56-123">[!code-cs[csrefKeywordsTypes#15](../../../csharp/language-reference/keywords/codesnippet/CSharp/interface_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="04c56-123">[!code-cs[csrefKeywordsTypes#15](../../../csharp/language-reference/keywords/codesnippet/CSharp/interface_2.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="04c56-124">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="04c56-124">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="04c56-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="04c56-125">See Also</span></span>  
 <span data-ttu-id="04c56-126">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="04c56-126">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="04c56-127">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="04c56-127">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="04c56-128">[Mots clés C#](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="04c56-128">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="04c56-129">[Types référence](../../../csharp/language-reference/keywords/reference-types.md) </span><span class="sxs-lookup"><span data-stu-id="04c56-129">[Reference Types](../../../csharp/language-reference/keywords/reference-types.md) </span></span>  
 <span data-ttu-id="04c56-130">[Interfaces](../../../csharp/programming-guide/interfaces/index.md) </span><span class="sxs-lookup"><span data-stu-id="04c56-130">[Interfaces](../../../csharp/programming-guide/interfaces/index.md) </span></span>  
 <span data-ttu-id="04c56-131">[Utilisation de propriétés](../../../csharp/programming-guide/classes-and-structs/using-properties.md) </span><span class="sxs-lookup"><span data-stu-id="04c56-131">[Using Properties](../../../csharp/programming-guide/classes-and-structs/using-properties.md) </span></span>  
 <span data-ttu-id="04c56-132">[Utilisation d’indexeurs](../../../csharp/programming-guide/indexers/using-indexers.md) </span><span class="sxs-lookup"><span data-stu-id="04c56-132">[Using Indexers](../../../csharp/programming-guide/indexers/using-indexers.md) </span></span>  
 <span data-ttu-id="04c56-133">[class](../../../csharp/language-reference/keywords/class.md) </span><span class="sxs-lookup"><span data-stu-id="04c56-133">[class](../../../csharp/language-reference/keywords/class.md) </span></span>  
 <span data-ttu-id="04c56-134">[struct](../../../csharp/language-reference/keywords/struct.md) </span><span class="sxs-lookup"><span data-stu-id="04c56-134">[struct](../../../csharp/language-reference/keywords/struct.md) </span></span>  
 [<span data-ttu-id="04c56-135">Interfaces</span><span class="sxs-lookup"><span data-stu-id="04c56-135">Interfaces</span></span>](../../../csharp/programming-guide/interfaces/index.md)

