---
title: "Attribution d'un nom à des ressources"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- names [.NET Framework], localized resources
- localization, naming guidelines
- resource names
- global applications, naming guidelines
- international applications, naming guidelines
ms.assetid: 8b0e97f3-7877-44fd-bc76-e05d36d5d79c
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 0387d820cc660bdf6cbafb9d76bbf0184c111881
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/23/2017
---
# <a name="naming-resources"></a><span data-ttu-id="8a55d-102">Attribution d'un nom à des ressources</span><span class="sxs-lookup"><span data-stu-id="8a55d-102">Naming Resources</span></span>
<span data-ttu-id="8a55d-103">Étant donné que les ressources localisables peuvent être référencés via certains objets comme s’ils étaient des propriétés, les instructions d’affectation de noms pour les ressources sont semblables aux instructions de la propriété.</span><span class="sxs-lookup"><span data-stu-id="8a55d-103">Because localizable resources can be referenced via certain objects as if they were properties, the naming guidelines for resources are similar to property guidelines.</span></span>  
  
 <span data-ttu-id="8a55d-104">**✓ FAIRE** utilisent la casse Pascal dans les clés de ressources.</span><span class="sxs-lookup"><span data-stu-id="8a55d-104">**✓ DO** use PascalCasing in resource keys.</span></span>  
  
 <span data-ttu-id="8a55d-105">**✓ FAIRE** fournir descriptif au lieu d’identificateurs courts.</span><span class="sxs-lookup"><span data-stu-id="8a55d-105">**✓ DO** provide descriptive rather than short identifiers.</span></span>  
  
 <span data-ttu-id="8a55d-106">**X ne sont pas** utiliser des mots clés de langage spécifique langage CLR principal.</span><span class="sxs-lookup"><span data-stu-id="8a55d-106">**X DO NOT** use language-specific keywords of the main CLR languages.</span></span>  
  
 <span data-ttu-id="8a55d-107">**✓ FAIRE** utiliser uniquement des caractères alphanumériques et des traits de soulignement dans les noms des ressources.</span><span class="sxs-lookup"><span data-stu-id="8a55d-107">**✓ DO** use only alphanumeric characters and underscores in naming resources.</span></span>  
  
 <span data-ttu-id="8a55d-108">**✓ FAIRE** utilisent la convention d’affectation de noms suivante pour les ressources de message d’exception.</span><span class="sxs-lookup"><span data-stu-id="8a55d-108">**✓ DO** use the following naming convention for exception message resources.</span></span>  
  
 <span data-ttu-id="8a55d-109">L’identificateur de ressource doit être le nom de type d’exception plus un identificateur court de l’exception :</span><span class="sxs-lookup"><span data-stu-id="8a55d-109">The resource identifier should be the exception type name plus a short identifier of the exception:</span></span>  
  
 `ArgumentExceptionIllegalCharacters`  
 `ArgumentExceptionInvalidName`  
 `ArgumentExceptionFileNameIsMalformed`  
  
 <span data-ttu-id="8a55d-110">*Portions © 2005, 2009 Microsoft Corporation. Tous droits réservés.*</span><span class="sxs-lookup"><span data-stu-id="8a55d-110">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="8a55d-111">*Réimprimées avec l’autorisation de Pearson éducation, Inc. à partir de [règles de conception d’infrastructure : Conventions, idiomes et des modèles pour les bibliothèques .NET réutilisable, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série de développement Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="8a55d-111">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a55d-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8a55d-112">See Also</span></span>  
 [<span data-ttu-id="8a55d-113">Règles de conception de .NET Framework</span><span class="sxs-lookup"><span data-stu-id="8a55d-113">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="8a55d-114">Directives de nommage</span><span class="sxs-lookup"><span data-stu-id="8a55d-114">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)
