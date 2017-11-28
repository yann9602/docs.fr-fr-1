---
title: "Délégués génériques (guide de programmation C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- generics [C#], delegates
- delegates [C#], generic
ms.assetid: bdea509c-44c1-4309-aaa9-15c7aee009df
caps.latest.revision: "16"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 1377723f18d6dd0e984538b530acbc7aa8d52feb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="generic-delegates-c-programming-guide"></a><span data-ttu-id="6c6aa-102">Délégués génériques (guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="6c6aa-102">Generic Delegates (C# Programming Guide)</span></span>
<span data-ttu-id="6c6aa-103">Un [délégué](../../../csharp/language-reference/keywords/delegate.md) peut définir ses propres paramètres de type.</span><span class="sxs-lookup"><span data-stu-id="6c6aa-103">A [delegate](../../../csharp/language-reference/keywords/delegate.md) can define its own type parameters.</span></span> <span data-ttu-id="6c6aa-104">Le code qui référence le délégué générique peut spécifier l’argument de type pour créer un type construit fermé, comme lors de l’instanciation d’une classe générique ou d’un appel d’une méthode générique, ainsi que l’illustre l’exemple ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="6c6aa-104">Code that references the generic delegate can specify the type argument to create a closed constructed type, just like when instantiating a generic class or calling a generic method, as shown in the following example:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#36](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-delegates_1.cs)]  
  
 <span data-ttu-id="6c6aa-105">Le langage C# version 2.0 propose une nouvelle fonctionnalité appelée conversion de groupe de méthodes, qui s’applique aussi bien aux types concrets qu’aux types délégués génériques et vous permet d’écrire la ligne précédente avec la syntaxe simplifiée suivante :</span><span class="sxs-lookup"><span data-stu-id="6c6aa-105">C# version 2.0 has a new feature called method group conversion, which applies to concrete as well as generic delegate types, and enables you to write the previous line with this simplified syntax:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#37](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-delegates_2.cs)]  
  
 <span data-ttu-id="6c6aa-106">Les délégués définis dans une classe générique peuvent utiliser les paramètres de type de classe générique, à l’instar des méthodes de classe.</span><span class="sxs-lookup"><span data-stu-id="6c6aa-106">Delegates defined within a generic class can use the generic class type parameters in the same way that class methods do.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#38](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-delegates_3.cs)]  
  
 <span data-ttu-id="6c6aa-107">Le code qui référence le délégué doit spécifier l’argument de type de la classe conteneur, comme suit :</span><span class="sxs-lookup"><span data-stu-id="6c6aa-107">Code that references the delegate must specify the type argument of the containing class, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#39](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-delegates_4.cs)]  
  
 <span data-ttu-id="6c6aa-108">Les délégués génériques sont particulièrement utiles pour définir des événements basés sur le modèle de design type parce que l’argument de l’expéditeur peut être fortement typé et il n’est plus nécessaire d’en effectuer un cast vers et depuis <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="6c6aa-108">Generic delegates are especially useful in defining events based on the typical design pattern because the sender argument can be strongly typed and no longer has to be cast to and from <xref:System.Object>.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#40](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-delegates_5.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="6c6aa-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6c6aa-109">See Also</span></span>  
 <xref:System.Collections.Generic>  
 [<span data-ttu-id="6c6aa-110">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="6c6aa-110">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="6c6aa-111">Introduction aux génériques</span><span class="sxs-lookup"><span data-stu-id="6c6aa-111">Introduction to Generics</span></span>](../../../csharp/programming-guide/generics/introduction-to-generics.md)  
 [<span data-ttu-id="6c6aa-112">Méthodes génériques</span><span class="sxs-lookup"><span data-stu-id="6c6aa-112">Generic Methods</span></span>](../../../csharp/programming-guide/generics/generic-methods.md)  
 [<span data-ttu-id="6c6aa-113">Classes génériques</span><span class="sxs-lookup"><span data-stu-id="6c6aa-113">Generic Classes</span></span>](../../../csharp/programming-guide/generics/generic-classes.md)  
 [<span data-ttu-id="6c6aa-114">Interfaces génériques</span><span class="sxs-lookup"><span data-stu-id="6c6aa-114">Generic Interfaces</span></span>](../../../csharp/programming-guide/generics/generic-interfaces.md)  
 [<span data-ttu-id="6c6aa-115">Délégués</span><span class="sxs-lookup"><span data-stu-id="6c6aa-115">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)  
 [<span data-ttu-id="6c6aa-116">Génériques</span><span class="sxs-lookup"><span data-stu-id="6c6aa-116">Generics</span></span>](~/docs/standard/generics/index.md)
