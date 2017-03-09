---
title: "Impossible de combiner VbStrConv.Wide et VbStrConv.Narrow | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbrArgument_IllegalWideNarrow"
ms.assetid: a53b4e6a-36b1-4e36-b2c5-8196313ec599
caps.latest.revision: 8
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 8
---
# Impossible de combiner VbStrConv.Wide et VbStrConv.Narrow
Votre application essaie de combiner les membres de l’énumération `VbStrConv``Wide` et `Narrow`, qui s’excluent mutuellement.  
  
### Pour corriger cette erreur  
  
1.  Supprimez `VbStrConv.Wide` ou `VbStrConv.Narrow`.  
  
## Voir aussi  
 <xref:System.Globalization>   
 [NOTINBUILD Énumération VbStrConv](http://msdn.microsoft.com/fr-fr/59f83dd9-6361-47df-a836-02ba9d4cb936)   
 [Introduction aux applications internationales basées sur le .NET Framework](/visual-studio/ide/introduction-to-international-applications-based-on-the-dotnet-framework)