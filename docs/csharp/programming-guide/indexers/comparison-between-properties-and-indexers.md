---
title: "Comparaison entre propri&#233;t&#233;s et indexeurs (Guide de programmation C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "indexeurs (C#), différences par rapport aux propriétés"
  - "propriétés (C#), et indexeurs"
ms.assetid: 3358a89f-44a0-4a4d-bf8c-07237a90af39
caps.latest.revision: 14
caps.handback.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Comparaison entre propri&#233;t&#233;s et indexeurs (Guide de programmation C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Les indexeurs sont semblables aux propriétés.  À l'exception des différences répertoriées dans le tableau suivant, toutes les règles définies pour les accesseurs des propriétés s'appliquent également aux accesseurs des indexeurs.  
  
|Propriété|Indexeur|  
|---------------|--------------|  
|Autorise à appeler des méthodes comme si elles étaient membres de données publiques.|Autorise l'accès à des éléments d'une collection interne d'un objet en utilisant la notation de tableau sur l'objet lui\-même.|  
|Accès par un nom simple.|Accès par un index.|  
|Peut être un membre statique ou un membre d'instance.|Doit être un membre d'instance.|  
|Un accesseur [get](../../../csharp/language-reference/keywords/get.md) d'une propriété n'a aucun paramètre.|Un accesseur `get` d'un indexeur possède la même liste de paramètres formels que l'indexeur.|  
|Un accesseur [set](../../../csharp/language-reference/keywords/set.md) d'une propriété contient le paramètre `value` implicite.|Un accesseur `set` d'un indexeur possède la même liste de paramètres formels que l'indexeur, outre le paramètre [value](../../../csharp/language-reference/keywords/value.md).|  
|Prend en charge la syntaxe abrégée avec les [Propriétés implémentées automatiquement](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md).|Ne prend pas en charge la syntaxe abrégée.|  
  
## Voir aussi  
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Indexeurs](../../../csharp/programming-guide/indexers/index.md)   
 [Propriétés](../../../csharp/programming-guide/classes-and-structs/properties.md)