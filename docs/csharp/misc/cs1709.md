---
title: "Avertissement du compilateur&#160;(niveau&#160;1)&#160;CS1709 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1709"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1709"
ms.assetid: e2bb1d30-4f30-4e10-82da-df1d3418454c
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Avertissement du compilateur&#160;(niveau&#160;1)&#160;CS1709
Le nom de fichier spécifié pour la directive de préprocesseur est vide  
  
 Vous avez spécifié une directive de préprocesseur qui comprend un nom de fichier, mais ce fichier est vide. Pour remédier à cet avertissement, ajoutez le contenu nécessaire au fichier.  
  
## Exemple  
 L’exemple suivant génère l’erreur CS1709 :  
  
```  
// CS1709.cs class Test { static void Main() { #pragma checksum "" "{406EA660-64CF-4C82-B6F0-42D48172A799}" ""  // CS1709 } }  
```