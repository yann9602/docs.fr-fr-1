---
title: Conception de classes statiques
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- type design guidelines, static classes
- class library design guidelines [.NET Framework], classes
- classes [.NET Framework], static
- static classes [.NET Framework]
- classes [.NET Framework], design guidelines
- type design guidelines, classes
ms.assetid: d67c14d8-c4dd-443f-affb-4ccae677c9b6
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 8c36bf5790d033eddb6bb7e0d910482143a9bcac
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/23/2017
---
# <a name="static-class-design"></a><span data-ttu-id="8710b-102">Conception de classes statiques</span><span class="sxs-lookup"><span data-stu-id="8710b-102">Static Class Design</span></span>
<span data-ttu-id="8710b-103">Une classe statique est définie comme une classe qui contient uniquement des membres statiques (bien entendu, outre les membres d’instance héritées <xref:System.Object?displayProperty=nameWithType> et éventuellement un constructeur privé).</span><span class="sxs-lookup"><span data-stu-id="8710b-103">A static class is defined as a class that contains only static members (of course besides the instance members inherited from <xref:System.Object?displayProperty=nameWithType> and possibly a private constructor).</span></span> <span data-ttu-id="8710b-104">Certains langages fournissent une prise en charge intégrée pour les classes static.</span><span class="sxs-lookup"><span data-stu-id="8710b-104">Some languages provide built-in support for static classes.</span></span> <span data-ttu-id="8710b-105">En c# 2.0 et versions ultérieures, lorsqu’une classe est déclarée comme étant statique, il est sealed, abstract, et aucun membre d’instance peut être substituée ou déclaré.</span><span class="sxs-lookup"><span data-stu-id="8710b-105">In C# 2.0 and later, when a class is declared to be static, it is sealed, abstract, and no instance members can be overridden or declared.</span></span>  
  
 <span data-ttu-id="8710b-106">Les classes statiques sont un compromis entre pure conception orientée objet et la simplicité.</span><span class="sxs-lookup"><span data-stu-id="8710b-106">Static classes are a compromise between pure object-oriented design and simplicity.</span></span> <span data-ttu-id="8710b-107">Ils sont couramment utilisés pour fournir des raccourcis à d’autres opérations (telles que <xref:System.IO.File?displayProperty=nameWithType>), titulaires de méthodes d’extension ou de fonctionnalités pour lequel un wrapper orienté objet est injustifié (tel que <xref:System.Environment?displayProperty=nameWithType>).</span><span class="sxs-lookup"><span data-stu-id="8710b-107">They are commonly used to provide shortcuts to other operations (such as <xref:System.IO.File?displayProperty=nameWithType>), holders of extension methods, or functionality for which a full object-oriented wrapper is unwarranted (such as <xref:System.Environment?displayProperty=nameWithType>).</span></span>  
  
 <span data-ttu-id="8710b-108">**✓ FAIRE** utilisent des classes statiques avec parcimonie.</span><span class="sxs-lookup"><span data-stu-id="8710b-108">**✓ DO** use static classes sparingly.</span></span>  
  
 <span data-ttu-id="8710b-109">Les classes static doivent être utilisés uniquement comme classes de prise en charge pour le noyau orientée objet de l’infrastructure.</span><span class="sxs-lookup"><span data-stu-id="8710b-109">Static classes should be used only as supporting classes for the object-oriented core of the framework.</span></span>  
  
 <span data-ttu-id="8710b-110">**X ne sont pas** traiter des classes statiques comme un compartiment divers.</span><span class="sxs-lookup"><span data-stu-id="8710b-110">**X DO NOT** treat static classes as a miscellaneous bucket.</span></span>  
  
 <span data-ttu-id="8710b-111">**X ne sont pas** déclarer ou substituer des membres d’instance dans les classes static.</span><span class="sxs-lookup"><span data-stu-id="8710b-111">**X DO NOT** declare or override instance members in static classes.</span></span>  
  
 <span data-ttu-id="8710b-112">**✓ FAIRE** déclarer des classes statiques comme sealed, abstract, et ajoutez un constructeur d’instance privée si votre langage de programmation ne dispose pas de prise en charge intégrée pour les classes static.</span><span class="sxs-lookup"><span data-stu-id="8710b-112">**✓ DO** declare static classes as sealed, abstract, and add a private instance constructor if your programming language does not have built-in support for static classes.</span></span>  
  
 <span data-ttu-id="8710b-113">*Portions © 2005, 2009 Microsoft Corporation. Tous droits réservés.*</span><span class="sxs-lookup"><span data-stu-id="8710b-113">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="8710b-114">*Réimprimées avec l’autorisation de Pearson éducation, Inc. à partir de [règles de conception d’infrastructure : Conventions, idiomes et des modèles pour les bibliothèques .NET réutilisable, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série de développement Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="8710b-114">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8710b-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8710b-115">See Also</span></span>  
 [<span data-ttu-id="8710b-116">Instructions pour la conception des types</span><span class="sxs-lookup"><span data-stu-id="8710b-116">Type Design Guidelines</span></span>](../../../docs/standard/design-guidelines/type.md)  
 [<span data-ttu-id="8710b-117">Règles de conception de .NET Framework</span><span class="sxs-lookup"><span data-stu-id="8710b-117">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
