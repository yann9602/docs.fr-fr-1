---
title: "XML literals and XML properties are not supported in embedded code within ASP.NET | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbc31200"
  - "bc31200"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC31200"
ms.assetid: 053e8cba-8584-45cc-9fa0-43d122779772
caps.latest.revision: 9
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 9
---
# XML literals and XML properties are not supported in embedded code within ASP.NET
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Les littéraux XML et les propriétés XML ne sont pas pris en charge dans le code incorporé au sein d'ASP.NETPour utiliser les fonctionnalités XML, utilisez une approche code\-behind.  
  
 Un littéral XML ou une propriété d'axe XML a été défini\(e\) dans le code incorporé \(`<%= =>`\) d'un fichier ASP.NET.  
  
 **ID d'erreur :** BC31200  
  
### Pour corriger cette erreur  
  
-   Déplacez le code qui inclut le littéral XML ou la propriété d'axe XML dans un fichier code\-behind ASP.NET.  
  
## Voir aussi  
 [XML Literals](../../../visual-basic/language-reference/xml-literals/index.md)   
 [XML Axis Properties](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)   
 [XML](../../../visual-basic/programming-guide/language-features/xml/index.md)