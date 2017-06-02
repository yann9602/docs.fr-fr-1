---
title: "Tableaux | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "indications de conception de bibliothèques de classes (.NET Framework), tableaux"
  - "tableaux (.NET Framework), les instructions d’utilisation"
  - "tableaux vides"
ms.assetid: 66a1b3d8-6f3f-4715-b235-e1ff95e32d8e
caps.latest.revision: 18
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 18
---
# Tableaux
**✓ faire** préférez l’utilisation de collections sur les tableaux dans les API publiques. Le [Collections](../../../docs/standard/design-guidelines/guidelines-for-collections.md) section fournit des détails sur le choix entre les collections et tableaux.  
  
 **X ne pas** utiliser des champs de tableau en lecture seule. Le champ lui\-même est en lecture seule et ne peut pas être modifié, mais les éléments du tableau peuvent être modifiés.  
  
 **✓ envisagez** à l’aide de tableaux en escalier au lieu de tableaux multidimensionnels.  
  
 Un tableau en escalier est un tableau dont les éléments sont également des tableaux. Les tableaux qui composent les éléments peuvent être de différentes tailles, ce qui conduit à un gaspillage d’espace pour certains jeux de données \(par exemple, une matrice éparse\) par rapport aux tableaux multidimensionnels. En outre, le CLR optimise les opérations d’index sur des tableaux en escalier, afin qu’ils peuvent présenter de meilleures performances d’exécution dans certains scénarios.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Tous droits réservés.*  
  
 *Réimprimé avec l’autorisation de Pearson éducation, Inc. à partir de [Framework Design Guidelines : Conventions, langages et des modèles pour les bibliothèques .NET réutilisable, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison\-Wesley Professional dans le cadre de la série de développement de Microsoft Windows.*  
  
## Voir aussi  
 <xref:System.Array>   
 [Instructions de conception d’infrastructure](../../../docs/standard/design-guidelines/index.md)   
 [Indications relatives à l'utilisation](../../../docs/standard/design-guidelines/usage-guidelines.md)