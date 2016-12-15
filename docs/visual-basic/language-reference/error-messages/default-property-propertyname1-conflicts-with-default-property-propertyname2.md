---
title: "Default property &#39;&lt;propertyname1&gt;&#39; conflicts with default property &#39;&lt;propertyname2&gt;&#39; in &#39;&lt;classname&gt;&#39; and so should be declared &#39;Shadows&#39; | Microsoft Docs"
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
  - "vbc40007"
  - "bc40007"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC40007"
ms.assetid: 692ccf76-5715-4f11-a972-84cf9de30bc1
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Default property &#39;&lt;propertyname1&gt;&#39; conflicts with default property &#39;&lt;propertyname2&gt;&#39; in &#39;&lt;classname&gt;&#39; and so should be declared &#39;Shadows&#39;
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Une propriété est déclarée avec le même nom qu'une propriété définie dans la classe de base.  Dans ce cas, la propriété de cette classe doit occulter la propriété de la classe de base.  
  
 Ce message est un avertissement.  `Shadows` est supposé par défaut.  Pour plus d'informations sur le masquage des avertissements ou le traitement des avertissements en tant qu'erreurs, consultez [Configuration d'avertissements en Visual Basic](/visual-studio/ide/configuring-warnings-in-visual-basic).  
  
 **ID d'erreur :** BC40007  
  
### Pour corriger cette erreur  
  
-   Ajoutez le mot clé `Shadows` à la déclaration ou changez le nom de la propriété déclarée.  
  
## Voir aussi  
 [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)   
 [Shadowing in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)