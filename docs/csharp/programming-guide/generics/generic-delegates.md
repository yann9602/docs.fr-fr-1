---
title: "Délégués génériques (guide de programmation C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- generics [C#], delegates
- delegates [C#], generic
ms.assetid: bdea509c-44c1-4309-aaa9-15c7aee009df
caps.latest.revision: 16
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
ms.openlocfilehash: be067e2a2e2a192da8ccc92b60af81f0999c449a
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="generic-delegates-c-programming-guide"></a><span data-ttu-id="aac77-102">Délégués génériques (guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="aac77-102">Generic Delegates (C# Programming Guide)</span></span>
<span data-ttu-id="aac77-103">Un [délégué](../../../csharp/language-reference/keywords/delegate.md) peut définir ses propres paramètres de type.</span><span class="sxs-lookup"><span data-stu-id="aac77-103">A [delegate](../../../csharp/language-reference/keywords/delegate.md) can define its own type parameters.</span></span> <span data-ttu-id="aac77-104">Le code qui référence le délégué générique peut spécifier l’argument de type pour créer un type construit fermé, comme lors de l’instanciation d’une classe générique ou d’un appel d’une méthode générique, ainsi que l’illustre l’exemple ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="aac77-104">Code that references the generic delegate can specify the type argument to create a closed constructed type, just like when instantiating a generic class or calling a generic method, as shown in the following example:</span></span>  
  
 <span data-ttu-id="aac77-105">[!code-cs[csProgGuideGenerics#36](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-delegates_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="aac77-105">[!code-cs[csProgGuideGenerics#36](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-delegates_1.cs)]</span></span>  
  
 <span data-ttu-id="aac77-106">Le langage C# version 2.0 propose une nouvelle fonctionnalité appelée conversion de groupe de méthodes, qui s’applique aussi bien aux types concrets qu’aux types délégués génériques et vous permet d’écrire la ligne précédente avec la syntaxe simplifiée suivante :</span><span class="sxs-lookup"><span data-stu-id="aac77-106">C# version 2.0 has a new feature called method group conversion, which applies to concrete as well as generic delegate types, and enables you to write the previous line with this simplified syntax:</span></span>  
  
 <span data-ttu-id="aac77-107">[!code-cs[csProgGuideGenerics#37](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-delegates_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="aac77-107">[!code-cs[csProgGuideGenerics#37](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-delegates_2.cs)]</span></span>  
  
 <span data-ttu-id="aac77-108">Les délégués définis dans une classe générique peuvent utiliser les paramètres de type de classe générique, à l’instar des méthodes de classe.</span><span class="sxs-lookup"><span data-stu-id="aac77-108">Delegates defined within a generic class can use the generic class type parameters in the same way that class methods do.</span></span>  
  
 <span data-ttu-id="aac77-109">[!code-cs[csProgGuideGenerics#38](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-delegates_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="aac77-109">[!code-cs[csProgGuideGenerics#38](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-delegates_3.cs)]</span></span>  
  
 <span data-ttu-id="aac77-110">Le code qui référence le délégué doit spécifier l’argument de type de la classe conteneur, comme suit :</span><span class="sxs-lookup"><span data-stu-id="aac77-110">Code that references the delegate must specify the type argument of the containing class, as follows:</span></span>  
  
 <span data-ttu-id="aac77-111">[!code-cs[csProgGuideGenerics#39](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-delegates_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="aac77-111">[!code-cs[csProgGuideGenerics#39](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-delegates_4.cs)]</span></span>  
  
 <span data-ttu-id="aac77-112">Les délégués génériques sont particulièrement utiles pour définir des événements basés sur le modèle de design type parce que l’argument de l’expéditeur peut être fortement typé et il n’est plus nécessaire d’en effectuer un cast vers et depuis <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="aac77-112">Generic delegates are especially useful in defining events based on the typical design pattern because the sender argument can be strongly typed and no longer has to be cast to and from <xref:System.Object>.</span></span>  
  
 <span data-ttu-id="aac77-113">[!code-cs[csProgGuideGenerics#40](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-delegates_5.cs)]</span><span class="sxs-lookup"><span data-stu-id="aac77-113">[!code-cs[csProgGuideGenerics#40](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-delegates_5.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aac77-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="aac77-114">See Also</span></span>  
 <span data-ttu-id="aac77-115"><xref:System.Collections.Generic></span><span class="sxs-lookup"><span data-stu-id="aac77-115"><xref:System.Collections.Generic></span></span>   
 <span data-ttu-id="aac77-116">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="aac77-116">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="aac77-117">[Introduction aux génériques](../../../csharp/programming-guide/generics/introduction-to-generics.md) </span><span class="sxs-lookup"><span data-stu-id="aac77-117">[Introduction to Generics](../../../csharp/programming-guide/generics/introduction-to-generics.md) </span></span>  
 <span data-ttu-id="aac77-118">[Méthodes génériques](../../../csharp/programming-guide/generics/generic-methods.md) </span><span class="sxs-lookup"><span data-stu-id="aac77-118">[Generic Methods](../../../csharp/programming-guide/generics/generic-methods.md) </span></span>  
 <span data-ttu-id="aac77-119">[Classes génériques](../../../csharp/programming-guide/generics/generic-classes.md) </span><span class="sxs-lookup"><span data-stu-id="aac77-119">[Generic Classes](../../../csharp/programming-guide/generics/generic-classes.md) </span></span>  
 <span data-ttu-id="aac77-120">[Interfaces génériques](../../../csharp/programming-guide/generics/generic-interfaces.md) </span><span class="sxs-lookup"><span data-stu-id="aac77-120">[Generic Interfaces](../../../csharp/programming-guide/generics/generic-interfaces.md) </span></span>  
 <span data-ttu-id="aac77-121">[Délégués](../../../csharp/programming-guide/delegates/index.md) </span><span class="sxs-lookup"><span data-stu-id="aac77-121">[Delegates](../../../csharp/programming-guide/delegates/index.md) </span></span>  
 [<span data-ttu-id="aac77-122">Génériques</span><span class="sxs-lookup"><span data-stu-id="aac77-122">Generics</span></span>](~/docs/standard/generics/index.md)

