---
title: "Constructor &#39;&lt;name&gt;&#39; cannot call itself | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "bc30298"
  - "vbc30298"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30298"
ms.assetid: 2d77b7f4-0640-4f89-9c65-f101fd2847c0
caps.latest.revision: 8
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 8
---
# Constructor &#39;&lt;name&gt;&#39; cannot call itself
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Une procédure `Sub New` dans une classe ou une structure s'appelle elle\-même.  
  
 Un constructeur a pour but d'initialiser une instance d'une classe ou d'une structure lorsqu'elle est créée pour la première fois.  Une classe ou une structure peut contenir plusieurs constructeurs, à condition qu'ils présentent des listes de paramètres différentes.  Un constructeur est autorisé à appeler un autre constructeur pour exécuter ses fonctionnalités en plus des siennes.  Mais cela n'a pas de sens qu'un constructeur s'appelle lui\-même, et en fait, cela entraînerait une récurrence infinie.  
  
 **ID d'erreur :** BC30298  
  
### Pour corriger cette erreur  
  
1.  Vérifiez la liste des paramètres du constructeur appelé.  Elle doit être différente de celle du constructeur qui effectue l'appel.  
  
2.  Si vous ne comptez pas appeler un autre constructeur, supprimez l'intégralité de l'appel `Sub New`.  
  
## Voir aussi  
 [Object Lifetime: How Objects Are Created and Destroyed](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)