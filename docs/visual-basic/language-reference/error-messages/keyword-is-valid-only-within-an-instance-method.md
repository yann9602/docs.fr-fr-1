---
title: "&#39;&lt;keyword&gt;&#39; is valid only within an instance method | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "bc30043"
  - "vbc30043"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30043"
ms.assetid: 7973aa82-a681-440c-9bca-242627d7ba86
caps.latest.revision: 10
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 10
---
# &#39;&lt;keyword&gt;&#39; is valid only within an instance method
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Les mots clés `Me`, `MyClass` et `MyBase` font référence à des instances de classe spécifiques.  Vous ne pouvez pas les utiliser à l'intérieur d'une procédure `Function` ou `Sub` partagée.  
  
 **ID d'erreur :** BC30043  
  
### Pour corriger cette erreur  
  
-   Supprimez le mot clé de la procédure ou supprimez le mot clé `Shared` de la déclaration de procédure.  
  
## Voir aussi  
 [Object Variable Assignment](../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)   
 [Me, My, MyBase, and MyClass](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)   
 [Inheritance Basics](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)