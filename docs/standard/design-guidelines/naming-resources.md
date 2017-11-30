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
ms.openlocfilehash: 89782b00799bfaac97780b0ffdee62c89fdfbe49
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="naming-resources"></a>Attribution d'un nom à des ressources
Étant donné que les ressources localisables peuvent être référencés via certains objets comme s’ils étaient des propriétés, les instructions d’affectation de noms pour les ressources sont semblables aux instructions de la propriété.  
  
 **✓ FAIRE** utilisent la casse Pascal dans les clés de ressources.  
  
 **✓ FAIRE** fournir descriptif au lieu d’identificateurs courts.  
  
 **X ne sont pas** utiliser des mots clés de langage spécifique langage CLR principal.  
  
 **✓ FAIRE** utiliser uniquement des caractères alphanumériques et des traits de soulignement dans les noms des ressources.  
  
 **✓ FAIRE** utilisent la convention d’affectation de noms suivante pour les ressources de message d’exception.  
  
 L’identificateur de ressource doit être le nom de type d’exception plus un identificateur court de l’exception :  
  
 `ArgumentExceptionIllegalCharacters`  
 `ArgumentExceptionInvalidName`  
 `ArgumentExceptionFileNameIsMalformed`  
  
 *Portions © 2005, 2009 Microsoft Corporation. Tous droits réservés.*  
  
 *Réimprimées avec l’autorisation de Pearson éducation, Inc. à partir de [règles de conception d’infrastructure : Conventions, idiomes et des modèles pour les bibliothèques .NET réutilisable, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série de développement Microsoft Windows.*  
  
## <a name="see-also"></a>Voir aussi  
 [Règles de conception de .NET Framework](../../../docs/standard/design-guidelines/index.md)  
 [Affectation de noms](../../../docs/standard/design-guidelines/naming-guidelines.md)
