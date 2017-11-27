---
title: Conception de classes abstraites
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- type design guidelines, abstract classes
- abstract classes, design guidelines
- class library design guidelines [.NET Framework], classes
- classes [.NET Framework], abstract
- classes [.NET Framework], design guidelines
- type design guidelines, classes
ms.assetid: d3646e6d-5c1f-4922-8fb0-ec5effb30d60
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d7b680c3377cbfa40734a57f9408d9487dbf3769
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="abstract-class-design"></a><span data-ttu-id="bf48a-102">Conception de classes abstraites</span><span class="sxs-lookup"><span data-stu-id="bf48a-102">Abstract Class Design</span></span>
<span data-ttu-id="bf48a-103">**X ne sont pas** définir des constructeurs internes publiques ou protégées dans les types abstraits.</span><span class="sxs-lookup"><span data-stu-id="bf48a-103">**X DO NOT** define public or protected internal constructors in abstract types.</span></span>  
  
 <span data-ttu-id="bf48a-104">Les constructeurs doivent être publics uniquement si les utilisateurs doivent créer des instances du type.</span><span class="sxs-lookup"><span data-stu-id="bf48a-104">Constructors should be public only if users will need to create instances of the type.</span></span> <span data-ttu-id="bf48a-105">Étant donné que vous ne peut pas créer des instances d’un type abstrait, un type abstrait avec un constructeur public s’est correctement conçu et trompeur pour les utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="bf48a-105">Because you cannot create instances of an abstract type, an abstract type with a public constructor is incorrectly designed and misleading to the users.</span></span>  
  
 <span data-ttu-id="bf48a-106">**✓ FAIRE** définir un document protégé ou un constructeur interne dans les classes abstraites.</span><span class="sxs-lookup"><span data-stu-id="bf48a-106">**✓ DO** define a protected or an internal constructor in abstract classes.</span></span>  
  
 <span data-ttu-id="bf48a-107">Un constructeur protégé est plus courant et il permet simplement de la classe de base pour sa propre initialisation lorsque des sous-types sont créés.</span><span class="sxs-lookup"><span data-stu-id="bf48a-107">A protected constructor is more common and simply allows the base class to do its own initialization when subtypes are created.</span></span>  
  
 <span data-ttu-id="bf48a-108">Un constructeur interne peut être utilisé pour limiter les implémentations concrètes de la classe abstraite à l’assembly de définition de la classe.</span><span class="sxs-lookup"><span data-stu-id="bf48a-108">An internal constructor can be used to limit concrete implementations of the abstract class to the assembly defining the class.</span></span>  
  
 <span data-ttu-id="bf48a-109">**✓ FAIRE** fournir au moins un type concret qui hérite de chaque classe abstraite qui vous sont fournis.</span><span class="sxs-lookup"><span data-stu-id="bf48a-109">**✓ DO** provide at least one concrete type that inherits from each abstract class that you ship.</span></span>  
  
 <span data-ttu-id="bf48a-110">Effectuant cette vous aide à la validation de la conception de la classe abstraite.</span><span class="sxs-lookup"><span data-stu-id="bf48a-110">Doing this helps to validate the design of the abstract class.</span></span> <span data-ttu-id="bf48a-111">Par exemple, <xref:System.IO.FileStream?displayProperty=nameWithType> est une implémentation de la <xref:System.IO.Stream?displayProperty=nameWithType> classe abstraite.</span><span class="sxs-lookup"><span data-stu-id="bf48a-111">For example,  <xref:System.IO.FileStream?displayProperty=nameWithType> is an implementation of the <xref:System.IO.Stream?displayProperty=nameWithType> abstract class.</span></span>  
  
 <span data-ttu-id="bf48a-112">*Portions © 2005, 2009 Microsoft Corporation. Tous droits réservés.*</span><span class="sxs-lookup"><span data-stu-id="bf48a-112">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="bf48a-113">*Réimprimées avec l’autorisation de Pearson éducation, Inc. à partir de [règles de conception d’infrastructure : Conventions, idiomes et des modèles pour les bibliothèques .NET réutilisable, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série de développement Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="bf48a-113">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf48a-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bf48a-114">See Also</span></span>  
 [<span data-ttu-id="bf48a-115">Règles de conception de type</span><span class="sxs-lookup"><span data-stu-id="bf48a-115">Type Design Guidelines</span></span>](../../../docs/standard/design-guidelines/type.md)  
 [<span data-ttu-id="bf48a-116">Règles de conception de .NET Framework</span><span class="sxs-lookup"><span data-stu-id="bf48a-116">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
