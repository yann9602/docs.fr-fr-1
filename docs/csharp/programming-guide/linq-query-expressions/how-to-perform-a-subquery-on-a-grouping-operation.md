---
title: "Comment&#160;: effectuer une sous-requ&#234;te sur une op&#233;ration de regroupement (Guide de programmation&#160;C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "regrouper les requêtes LINQ (C#)"
  - "groupes (C#), expressions de requête LINQ"
  - "groupes (LINQ en C#), sous-requêtes"
  - "requêtes (LINQ en C#), regroupement"
  - "requêtes (LINQ en C#), sous-requêtes"
  - "expressions de requête (LINQ en C#), regroupement"
  - "expressions de requête (LINQ en C#), sous-requêtes"
  - "sous-requêtes (C#)"
ms.assetid: 7b0805cd-53b4-429d-86b6-d37fb08f2c95
caps.latest.revision: 15
caps.handback.revision: 15
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Comment&#160;: effectuer une sous-requ&#234;te sur une op&#233;ration de regroupement (Guide de programmation&#160;C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Cette rubrique présente deux façons différentes de créer une requête qui organise les données sources en groupes, puis effectue une sous\-requête sur chaque groupe individuellement.  La technique de base dans chaque exemple est de grouper les éléments source en utilisant une *continuation* nommée `newGroup`, puis de générer ensuite une nouvelle sous\-requête sur `newGroup`.  Cette sous\-requête est exécutée sur chaque nouveau groupe créé par la requête externe.  Notez que dans cet exemple particulier, la sortie définitive n'est pas un groupe mais une séquence en deux dimensions de types anonymes.  
  
 Pour plus d'informations sur la manière de grouper, consultez [group, clause](../../../csharp/language-reference/keywords/group-clause.md).  
  
 Pour plus d'informations sur les continuations, consultez [into](../../../csharp/language-reference/keywords/into.md).  L'exemple suivant utilise une structure de données en mémoire comme source de données, mais les mêmes principes s'appliquent à tout type de source de données [!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq_md.md)].  
  
## Exemple  
 [!code-cs[csProgGuideLINQ#23](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-perform-a-subquery-on-a-grouping-operation_1.cs)]  
  
## Compilation du code  
 Cet exemple contient des références aux objets définis dans l'exemple d'application dans [Comment : interroger une collection d'objets](../../../csharp/programming-guide/linq-query-expressions/how-to-query-a-collection-of-objects.md).  Pour compiler et exécuter cette méthode, collez\-la dans la classe `StudentClass` de cette application et ajoutez\-lui un appel de la méthode `Main`.  
  
 Lorsque vous adaptez cette méthode à votre propre application, souvenez\-vous que LINQ requiert la version 3.5 du [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] et que le projet doit contenir une référence à System.Core.dll et une directive using pour System.Linq.  Les types LINQ to SQL, LINQ to XML et LINQ to DataSet requièrent des utilisations et des références supplémentaires.  Pour plus d'informations, consultez [How to: Create a LINQ Project](../Topic/How%20to:%20Create%20a%20LINQ%20Project.md).  
  
## Voir aussi  
 [Expressions de requête \(LINQ\)](../../../csharp/programming-guide/linq-query-expressions/index.md)