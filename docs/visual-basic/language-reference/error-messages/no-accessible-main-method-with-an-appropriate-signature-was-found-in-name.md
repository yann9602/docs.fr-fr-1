---
title: "No accessible &#39;Main&#39; method with an appropriate signature was found in &#39;&lt;name&gt;&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30737"
  - "vbc30737"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30737"
ms.assetid: 3f40bacd-3fac-4741-b204-852f693d4340
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# No accessible &#39;Main&#39; method with an appropriate signature was found in &#39;&lt;name&gt;&#39;
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Les applications en ligne de commande doivent avoir un `Sub Main` défini.  `Main` doit être déclaré comme `Public Shared` s'il est défini dans une classe, ou comme `Public` s'il est défini dans un module.  
  
 Pour plus d'informations sur `Main`, consultez [NIB: Visual Basic Version of Hello, World](http://msdn.microsoft.com/fr-fr/9d030b60-e148-4366-a462-69532f02294c).  
  
 **ID d'erreur :** BC30737  
  
### Pour corriger cette erreur  
  
-   Définissez une procédure `Public Sub Main` pour votre projet.  Déclarez\-la en tant que `Shared` si et seulement si vous la définissez au sein d'une classe.  
  
## Voir aussi  
 [NIB: Visual Basic Version of Hello, World](http://msdn.microsoft.com/fr-fr/9d030b60-e148-4366-a462-69532f02294c)   
 [Structure of a Visual Basic Program](../../../visual-basic/programming-guide/program-structure/structure-of-a-visual-basic-program.md)   
 [Procedures](../../../visual-basic/programming-guide/language-features/procedures/index.md)