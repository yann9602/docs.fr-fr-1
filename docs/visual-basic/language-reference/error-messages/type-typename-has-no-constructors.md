---
title: "Type &#39;&lt;typename&gt;&#39; has no constructors | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "bc30251"
  - "vbc30251"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30251"
ms.assetid: aff3e1df-abe6-4bc0-9abc-a1e70514c561
caps.latest.revision: 9
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 9
---
# Type &#39;&lt;typename&gt;&#39; has no constructors
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Un type ne prend pas en charge un appel à `Sub New()`. L'une des causes probables est un fichier compilateur ou binaire endommagé.  
  
 **ID d'erreur :** BC30251  
  
### Pour corriger cette erreur  
  
1.  Si le type se trouve dans un projet différent ou dans un fichier référencé, réinstallez le projet ou le fichier.  
  
2.  Si le type se trouve dans le même projet, recompilez l'assembly contenant le type.  
  
3.  Si l'erreur se produit à nouveau, réinstallez le compilateur [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)].  
  
4.  Si l'erreur persiste, rassemblez des informations sur ses circonstances et avertissez les services de support technique Microsoft.  
  
## Voir aussi  
 [Objects and Classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)   
 [Nous contacter](/visual-studio/ide/talk-to-us)