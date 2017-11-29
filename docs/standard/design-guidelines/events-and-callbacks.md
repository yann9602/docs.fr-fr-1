---
title: "Événements et rappels"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- events [.NET Framework], extensibility
- methods [.NET Framework], callback
- callback methods
- callbacks
ms.assetid: 48b55c60-495f-4089-9396-97f9122bba7c
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 217e9eae3540e0a20afd0888d24803285d6352b4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="events-and-callbacks"></a><span data-ttu-id="d6cac-102">Événements et rappels</span><span class="sxs-lookup"><span data-stu-id="d6cac-102">Events and Callbacks</span></span>
<span data-ttu-id="d6cac-103">Les rappels sont des points d’extensibilité qui autorisent une infrastructure rappeler dans le code de l’utilisateur via un délégué.</span><span class="sxs-lookup"><span data-stu-id="d6cac-103">Callbacks are extensibility points that allow a framework to call back into user code through a delegate.</span></span> <span data-ttu-id="d6cac-104">Ces délégués sont généralement transmis à l’infrastructure via un paramètre d’une méthode.</span><span class="sxs-lookup"><span data-stu-id="d6cac-104">These delegates are usually passed to the framework through a parameter of a method.</span></span>  
  
 <span data-ttu-id="d6cac-105">Les événements sont un cas spécial de rappels qui prend en charge la syntaxe pratique et cohérente pour fournir le délégué (un gestionnaire d’événements).</span><span class="sxs-lookup"><span data-stu-id="d6cac-105">Events are a special case of callbacks that supports convenient and consistent syntax for supplying the delegate (an event handler).</span></span> <span data-ttu-id="d6cac-106">En outre, saisie semi-automatique des instructions et les concepteurs de Visual Studio fournissent de l’aide à l’aide d’API basées sur des événements.</span><span class="sxs-lookup"><span data-stu-id="d6cac-106">In addition, Visual Studio’s statement completion and designers provide help in using event-based APIs.</span></span> <span data-ttu-id="d6cac-107">(Consultez [événement conception](../../../docs/standard/design-guidelines/event.md).)</span><span class="sxs-lookup"><span data-stu-id="d6cac-107">(See [Event Design](../../../docs/standard/design-guidelines/event.md).)</span></span>  
  
 <span data-ttu-id="d6cac-108">**✓ Envisagez** à l’aide des rappels pour permettre aux utilisateurs de fournir un code personnalisé doit être exécuté par l’infrastructure.</span><span class="sxs-lookup"><span data-stu-id="d6cac-108">**✓ CONSIDER** using callbacks to allow users to provide custom code to be executed by the framework.</span></span>  
  
 <span data-ttu-id="d6cac-109">**✓ Envisagez** à l’aide d’événements pour permettre aux utilisateurs de personnaliser le comportement d’une infrastructure sans avoir besoin pour comprendre la conception orientée objet.</span><span class="sxs-lookup"><span data-stu-id="d6cac-109">**✓ CONSIDER** using events to allow users to customize the behavior of a framework without the need for understanding object-oriented design.</span></span>  
  
 <span data-ttu-id="d6cac-110">**✓ FAIRE** de préférence des événements via des rappels ordinaires, car ils sont plus facile pour un grand nombre de développeurs et sont intégrés à la fin de l’instruction Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d6cac-110">**✓ DO** prefer events over plain callbacks, because they are more familiar to a broader range of developers and are integrated with Visual Studio statement completion.</span></span>  
  
 <span data-ttu-id="d6cac-111">**X Évitez** à l’aide de rappels dans les API sensibles aux performances.</span><span class="sxs-lookup"><span data-stu-id="d6cac-111">**X AVOID** using callbacks in performance-sensitive APIs.</span></span>  
  
 <span data-ttu-id="d6cac-112">**✓ FAIRE** utiliser la nouvelle `Func<...>`, `Action<...>`, ou `Expression<...>` types à la place des délégués personnalisés lors de la définition d’API avec des rappels.</span><span class="sxs-lookup"><span data-stu-id="d6cac-112">**✓ DO** use the new `Func<...>`, `Action<...>`, or `Expression<...>` types instead of custom delegates, when defining APIs with callbacks.</span></span>  
  
 <span data-ttu-id="d6cac-113">`Func<...>`et `Action<...>` représentent des délégués génériques.</span><span class="sxs-lookup"><span data-stu-id="d6cac-113">`Func<...>` and `Action<...>` represent generic delegates.</span></span> <span data-ttu-id="d6cac-114">`Expression<...>`représente les définitions de fonction qui peuvent être compilées et appelées par la suite lors de l’exécution, mais peut également être sérialisées et passées à des processus à distance.</span><span class="sxs-lookup"><span data-stu-id="d6cac-114">`Expression<...>` represents function definitions that can be compiled and subsequently invoked at runtime but can also be serialized and passed to remote processes.</span></span>  
  
 <span data-ttu-id="d6cac-115">**✓ FAIRE** mesurer et comprendre les implications en matière de performances de l’utilisation de `Expression<...>`, au lieu d’utiliser `Func<...>` et `Action<...>` délégués.</span><span class="sxs-lookup"><span data-stu-id="d6cac-115">**✓ DO** measure and understand performance implications of using `Expression<...>`, instead of using `Func<...>` and `Action<...>` delegates.</span></span>  
  
 <span data-ttu-id="d6cac-116">`Expression<...>`les types sont dans la plupart des cas logiquement équivalente à `Func<...>` et `Action<...>` délégués.</span><span class="sxs-lookup"><span data-stu-id="d6cac-116">`Expression<...>` types are in most cases logically equivalent to `Func<...>` and `Action<...>` delegates.</span></span> <span data-ttu-id="d6cac-117">La principale différence est que les délégués sont destinées à être utilisée dans des scénarios de processus locale. les expressions sont destinées aux cas où il est bénéfique et permet d’évaluer l’expression dans un processus distant ou un ordinateur.</span><span class="sxs-lookup"><span data-stu-id="d6cac-117">The main difference between them is that the delegates are intended to be used in local process scenarios; expressions are intended for cases where it’s beneficial and possible to evaluate the expression in a remote process or machine.</span></span>  
  
 <span data-ttu-id="d6cac-118">**✓ FAIRE** comprendre que par l’appel d’un délégué, vous exécutez du code arbitraire et qui pourraient avoir des répercussions de sécurité, d’exactitude et de compatibilité.</span><span class="sxs-lookup"><span data-stu-id="d6cac-118">**✓ DO** understand that by calling a delegate, you are executing arbitrary code and that could have security, correctness, and compatibility repercussions.</span></span>  
  
 <span data-ttu-id="d6cac-119">*Portions © 2005, 2009 Microsoft Corporation. Tous droits réservés.*</span><span class="sxs-lookup"><span data-stu-id="d6cac-119">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="d6cac-120">*Réimprimées avec l’autorisation de Pearson éducation, Inc. à partir de [règles de conception d’infrastructure : Conventions, idiomes et des modèles pour les bibliothèques .NET réutilisable, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série de développement Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="d6cac-120">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6cac-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d6cac-121">See Also</span></span>  
 [<span data-ttu-id="d6cac-122">Conception d’extensibilité</span><span class="sxs-lookup"><span data-stu-id="d6cac-122">Designing for Extensibility</span></span>](../../../docs/standard/design-guidelines/designing-for-extensibility.md)  
 [<span data-ttu-id="d6cac-123">Règles de conception de .NET Framework</span><span class="sxs-lookup"><span data-stu-id="d6cac-123">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
