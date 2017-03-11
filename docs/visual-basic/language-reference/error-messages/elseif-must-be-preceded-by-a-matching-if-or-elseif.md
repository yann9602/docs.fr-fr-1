---
title: "&#39;#ElseIf&#39; must be preceded by a matching &#39;#If&#39; or &#39;#ElseIf&#39; | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbc30014"
  - "bc30014"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30014"
ms.assetid: 5215585e-2efa-485a-9efe-9833a1cc83a0
caps.latest.revision: 9
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 9
---
# &#39;#ElseIf&#39; must be preceded by a matching &#39;#If&#39; or &#39;#ElseIf&#39;
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

`#ElseIf` est une directive de compilation conditionnelle.  Une clause `#ElseIf` doit être précédée d'une clause `#If` ou `#ElseIf` correspondante.  
  
 **ID d'erreur :** BC30014  
  
### Pour corriger cette erreur  
  
1.  Vérifiez qu'une clause `#If`  ou `#ElseIf` précédente n'a pas été séparée de cette clause `#ElseIf` par l'interposition d'un bloc de compilation conditionnelle ou par une clause `#End If` dont l'emplacement est incorrect.  
  
2.  Si `#ElseIf` est précédée d'une directive `#Else`, supprimez `#Else` ou remplacez\-la par `#ElseIf`.  
  
3.  Si tout le reste est en ordre, ajoutez une directive `#If` au début du bloc de compilation conditionnelle.  
  
## Voir aussi  
 [\#If...Then...\#Else Directives](../../../visual-basic/language-reference/directives/if-then-else-directives.md)