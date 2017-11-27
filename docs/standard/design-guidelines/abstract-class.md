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
# <a name="abstract-class-design"></a>Conception de classes abstraites
**X ne sont pas** définir des constructeurs internes publiques ou protégées dans les types abstraits.  
  
 Les constructeurs doivent être publics uniquement si les utilisateurs doivent créer des instances du type. Étant donné que vous ne peut pas créer des instances d’un type abstrait, un type abstrait avec un constructeur public s’est correctement conçu et trompeur pour les utilisateurs.  
  
 **✓ FAIRE** définir un document protégé ou un constructeur interne dans les classes abstraites.  
  
 Un constructeur protégé est plus courant et il permet simplement de la classe de base pour sa propre initialisation lorsque des sous-types sont créés.  
  
 Un constructeur interne peut être utilisé pour limiter les implémentations concrètes de la classe abstraite à l’assembly de définition de la classe.  
  
 **✓ FAIRE** fournir au moins un type concret qui hérite de chaque classe abstraite qui vous sont fournis.  
  
 Effectuant cette vous aide à la validation de la conception de la classe abstraite. Par exemple, <xref:System.IO.FileStream?displayProperty=nameWithType> est une implémentation de la <xref:System.IO.Stream?displayProperty=nameWithType> classe abstraite.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Tous droits réservés.*  
  
 *Réimprimées avec l’autorisation de Pearson éducation, Inc. à partir de [règles de conception d’infrastructure : Conventions, idiomes et des modèles pour les bibliothèques .NET réutilisable, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série de développement Microsoft Windows.*  
  
## <a name="see-also"></a>Voir aussi  
 [Règles de conception de type](../../../docs/standard/design-guidelines/type.md)  
 [Règles de conception de .NET Framework](../../../docs/standard/design-guidelines/index.md)
