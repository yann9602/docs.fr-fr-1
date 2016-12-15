---
title: "VbStrConv.Wide et VbStrConv.Narrow ne s’appliquent pas aux param&#232;tres r&#233;gionaux sp&#233;cifi&#233;s | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbrArgument_WideNarrowNotApplicable"
ms.assetid: 5811098c-b124-4caf-8a2b-f81f12f1d5f5
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# VbStrConv.Wide et VbStrConv.Narrow ne s’appliquent pas aux param&#232;tres r&#233;gionaux sp&#233;cifi&#233;s
L’application essaie d’utiliser les membres d’énumération `VbStrConv``Wide` ou `Narrow`, qui ne peuvent pas être appliqués aux paramètres régionaux spécifiés.  
  
### Pour corriger cette erreur  
  
1.  Supprimez `VbStrConv.Wide` ou `VbStrConv.Narrow`.  
  
## Voir aussi  
 <xref:System.Globalization>   
 [NOTINBUILD VbStrConv, énumération](http://msdn.microsoft.com/fr-fr/59f83dd9-6361-47df-a836-02ba9d4cb936)   
 [Introduction aux applications internationales basées sur le .NET Framework](/visual-studio/ide/introduction-to-international-applications-based-on-the-dotnet-framework)