---
title: "&#39;Module&#39; statements can occur only at file or namespace level | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "bc30617"
  - "vbc30617"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30617"
ms.assetid: 5e9de8e5-d26b-4fb2-9e28-814413fe9cef
caps.latest.revision: 8
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 8
---
# &#39;Module&#39; statements can occur only at file or namespace level
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Les instructions `Module` doivent apparaître au début de votre fichier source, immédiatement après les instructions `Option` et `Imports`, les attributs globaux et les déclarations d'espaces de noms, mais avant toutes les autres déclarations.  
  
 **ID d'erreur :** BC30617  
  
### Pour corriger cette erreur  
  
-   Déplacez l'instruction `Module` au début de votre déclaration d'espace de noms ou de votre fichier source.  
  
## Voir aussi  
 [Module Statement](../../../visual-basic/language-reference/statements/module-statement.md)