---
title: "Impossible de combiner SimplifiedChinese et VbStrConv.TraditionalChinese | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbrArgument_StrConvSCandTC"
ms.assetid: d8e6a11b-f549-43b5-8337-0594340e1325
caps.latest.revision: 10
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 10
---
# Impossible de combiner SimplifiedChinese et VbStrConv.TraditionalChinese
Votre application essaie de combiner les membres de l’énumération `VbStrConv``SimplifiedChinese` et `TraditionalChinese`, qui s’excluent mutuellement.  
  
### Pour corriger cette erreur  
  
-   Supprimez  `VbStrConv.SimplifiedChinese` ou `VbStrConv.TraditionalChinese`.  
  
## Voir aussi  
 <xref:System.Globalization>   
 [NOTINBUILD Énumération VbStrConv](http://msdn.microsoft.com/fr-fr/59f83dd9-6361-47df-a836-02ba9d4cb936)   
 [Introduction aux applications internationales basées sur le .NET Framework](/visual-studio/ide/introduction-to-international-applications-based-on-the-dotnet-framework)