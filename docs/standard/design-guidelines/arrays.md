---
title: Tableaux
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- class library design guidelines [.NET Framework], arrays
- arrays [.NET Framework], usage guidelines
- empty arrays
ms.assetid: 66a1b3d8-6f3f-4715-b235-e1ff95e32d8e
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 2e634cdcff0b1b2968a3b64d8d05cb57feeddb51
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/23/2017
---
# <a name="arrays"></a>Tableaux
**✓ FAIRE** préférez l’utilisation de collections sur des tableaux dans les API publiques. Le [Collections](../../../docs/standard/design-guidelines/guidelines-for-collections.md) section fournit des détails sur le choix entre les collections et tableaux.  
  
 **X ne sont pas** utiliser les champs de tableau en lecture seule. Le champ lui-même est en lecture seule et ne peut pas être modifié, mais les éléments du tableau peuvent être modifiés.  
  
 **✓ Envisagez** à l’aide de tableaux en escalier à la place de tableaux multidimensionnels.  
  
 Un tableau en escalier est un tableau comportant des éléments qui sont également des tableaux. Les tableaux qui composent les éléments peuvent être de différentes tailles, conduisant à un gaspillage d’espace pour certains jeux de données (par exemple, une matrice éparse) par rapport aux tableaux multidimensionnels. En outre, le CLR optimise les opérations d’index sur des tableaux en escalier, afin qu’ils peuvent exposer les meilleures performances dans certains scénarios d’exécution.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Tous droits réservés.*  
  
 *Réimprimées avec l’autorisation de Pearson éducation, Inc. à partir de [règles de conception d’infrastructure : Conventions, idiomes et des modèles pour les bibliothèques .NET réutilisable, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série de développement Microsoft Windows.*  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Array>  
 [Règles de conception de .NET Framework](../../../docs/standard/design-guidelines/index.md)  
 [Indications relatives à l’utilisation](../../../docs/standard/design-guidelines/usage-guidelines.md)
