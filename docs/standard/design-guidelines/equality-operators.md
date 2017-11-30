---
title: "Opérateurs d'égalité"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- class library design guidelines [.NET Framework], Equals method
- class library design guidelines [.NET Framework], equality operator
- equality operator (==) [.NET Framework]
- Equals method
- == operator (equality) [.NET Framework]
ms.assetid: bc496a91-fefb-4ce0-ab4c-61f09964119a
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 55c0505f5a06dfc87897fa59e9d6083cbd63c8ee
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="equality-operators"></a>Opérateurs d'égalité
Cette section présente la surcharge d’opérateurs d’égalité et fait référence à `operator==` et `operator!=` en tant qu’opérateurs d’égalité.  
  
 **X ne sont pas** un des opérateurs d’égalité et pas dans l’autre surcharge.  
  
 **✓ FAIRE** vous assurer que <xref:System.Object.Equals%2A?displayProperty=nameWithType> et les opérateurs d’égalité ont exactement la même sémantique et des caractéristiques similaires.  
  
 Cela signifie souvent que `Object.Equals` doit être remplacée lorsque les opérateurs d’égalité sont surchargés.  
  
 **X Évitez** lever des exceptions à partir des opérateurs d’égalité.  
  
 Par exemple, retourner false si l’un des arguments est null au lieu de lever `NullReferenceException`.  
  
## <a name="equality-operators-on-value-types"></a>Opérateurs d’égalité sur les Types valeur  
 **✓ FAIRE** surcharger les opérateurs d’égalité sur les types valeur, si l’égalité est explicite.  
  
 Dans la plupart des langages de programmation, il n’existe aucune implémentation par défaut de `operator==` pour les types valeur.  
  
## <a name="equality-operators-on-reference-types"></a>Opérateurs d’égalité sur les Types référence  
 **X Évitez** la surcharge des opérateurs d’égalité sur les types référence mutables.  
  
 Pour de nombreuses langues d’opérateurs d’égalité intégrés pour les types référence. Les opérateurs intégrés implémentent généralement l’égalité de référence et de nombreux développeurs sont surpris lorsque le comportement par défaut est modifié à l’égalité des valeurs.  
  
 Ce problème est atténué pour les types référence immuable parce que l’immuabilité rend plus difficile à remarquer la différence entre l’égalité des références et l’égalité des valeurs.  
  
 **X Évitez** surcharge des opérateurs d’égalité sur les types référence si l’implémentation est beaucoup plus lente que celui de l’égalité des références.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Tous droits réservés.*  
  
 *Réimprimées avec l’autorisation de Pearson éducation, Inc. à partir de [règles de conception d’infrastructure : Conventions, idiomes et des modèles pour les bibliothèques .NET réutilisable, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série de développement Microsoft Windows.*  
  
## <a name="see-also"></a>Voir aussi  
 [Règles de conception de .NET Framework](../../../docs/standard/design-guidelines/index.md)  
 [Instructions d’utilisation](../../../docs/standard/design-guidelines/usage-guidelines.md)
