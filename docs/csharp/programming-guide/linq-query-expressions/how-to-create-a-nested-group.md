---
title: "Comment&#160;: cr&#233;er un groupe imbriqu&#233; (Guide de programmation&#160;C#) | Microsoft Docs"
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
  - "regrouper les groupes en requêtes LINQ"
  - "regrouper les requêtes LINQ"
  - "groupes (LINQ en C#), imbriqués"
  - "requêtes imbriquées (C#)"
  - "requêtes (LINQ en C#), groupes imbriqués"
  - "expressions de requête (LINQ en C#), groupes imbriqués"
ms.assetid: f48c64af-6d4e-473c-ab27-02f78b5ec2b9
caps.latest.revision: 12
caps.handback.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Comment&#160;: cr&#233;er un groupe imbriqu&#233; (Guide de programmation&#160;C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

L'exemple suivant indique comment créer des groupes imbriqués dans une expression de requête [!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq_md.md)].  Chaque groupe créé par année d'étude ou niveau d'étude est subdivisé en groupes par noms d'individus.  
  
## Exemple  
 [!code-cs[csProgGuideLINQ#24](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-create-a-nested-group_1.cs)]  
  
 Notez que trois boucles `foreach` imbriquées sont requises pour itérer au sein des éléments internes d'un groupe imbriqué.  
  
## Compilation du code  
 Cet exemple contient des références aux objets définis dans l'exemple d'application dans [Comment : interroger une collection d'objets](../../../csharp/programming-guide/linq-query-expressions/how-to-query-a-collection-of-objects.md).  Pour compiler et exécuter cette méthode, collez\-la dans la classe `StudentClass` de cette application et ajoutez\-lui un appel de la méthode `Main`.  
  
 Lorsque vous adaptez cette méthode à votre propre application, souvenez\-vous que LINQ requiert la version 3.5 du [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] et que le projet doit contenir une référence à System.Core.dll et une directive using pour System.Linq.  Les types LINQ to SQL, LINQ to XML et LINQ to DataSet requièrent des utilisations et des références supplémentaires.  Pour plus d'informations, consultez [How to: Create a LINQ Project](../Topic/How%20to:%20Create%20a%20LINQ%20Project.md).  
  
## Voir aussi  
 [Expressions de requête \(LINQ\)](../../../csharp/programming-guide/linq-query-expressions/index.md)