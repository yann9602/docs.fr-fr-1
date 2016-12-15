---
title: "G&#233;n&#233;riques et tableaux (guide de programmation C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "tableaux (C#), génériques"
  - "génériques (C#), tableaux"
ms.assetid: 7d956536-3851-41b5-94ad-3e7c0a5fe485
caps.latest.revision: 17
caps.handback.revision: 17
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# G&#233;n&#233;riques et tableaux (guide de programmation C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

En C\# 2.0 et versions ultérieures, les tableaux unidimensionnels qui ont une limite inférieure de zéro implémentent automatiquement <xref:System.Collections.Generic.IList%601>.  Cela vous permet de créer des méthodes génériques qui peuvent utiliser le même code pour itérer au sein de tableaux et d'autres types de collections.  Cette technique est essentiellement utile pour lire les données dans des collections.  L'interface <xref:System.Collections.Generic.IList%601> ne peut pas être utilisée pour ajouter ou supprimer des éléments d'un tableau.  Une exception sera levée si vous essayez d'appeler une méthode <xref:System.Collections.Generic.IList%601> telle que <xref:System.Collections.Generic.IList%601.RemoveAt%2A> dans un tableau de ce contexte.  
  
 L'exemple de code suivant montre comment une méthode générique seule qui prend un paramètre d'entrée <xref:System.Collections.Generic.IList%601> peut itérer à la fois au sein d'une liste et d'un tableau \(en l'occurrence un tableau d'entiers\).  
  
 [!code-cs[csProgGuideGenerics#35](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-arrays_1.cs)]  
  
## Voir aussi  
 <xref:System.Collections.Generic>   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Génériques](../../../csharp/programming-guide/generics/index.md)   
 [Tableaux](../../../csharp/programming-guide/arrays/index.md)   
 [Génériques](../Topic/Generics%20in%20the%20.NET%20Framework.md)