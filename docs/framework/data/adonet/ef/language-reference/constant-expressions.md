---
title: "Expressions constantes | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: 9d98a7be-b110-4edb-8eba-bed10f250b6d
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# Expressions constantes
Une expression constante est composée d'une valeur constante.  Les valeurs constantes sont converties directement en expressions d'arborescence de commandes constantes, sans aucune traduction sur le client.  Cela inclut les expressions qui génèrent une valeur constante.  Par conséquent, le comportement de la source de données doit être prévu pour toutes les expressions impliquant des constantes.  Il peut en résulter un comportement différent du comportement CLR.  
  
 L'exemple suivant illustre une expression constante qui est évaluée sur le serveur.  
  
 [!code-csharp[DP L2E Conceptual Examples#ConstantExpression](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#constantexpression)]
 [!code-vb[DP L2E Conceptual Examples#ConstantExpression](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#constantexpression)]  
  
 [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] ne prend pas en charge l'utilisation d'une classe d'utilisateur comme constante.  Toutefois, une référence de propriété sur une classe d'utilisateur est considérée comme une constante. Elle est donc convertie en expression constante d'arborescence de commandes et exécutée sur la source de données.  
  
## Voir aussi  
 [Expressions dans les requêtes LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/expressions-in-linq-to-entities-queries.md)