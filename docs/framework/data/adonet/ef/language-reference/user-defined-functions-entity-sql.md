---
title: "Fonctions d&#233;finies par l&#39;utilisateur (Entity SQL) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3f9e6bbd-8e5a-43e1-809f-f8a61338e522
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# Fonctions d&#233;finies par l&#39;utilisateur (Entity SQL)
Entity SQL prend en charge l'appel de fonctions définies par l'utilisateur dans une requête.  Vous pouvez définir ces fonctions incluses avec la requête \(consultez [How to: Call a User\-Defined Function](http://msdn.microsoft.com/fr-fr/ad131b86-8b4e-4747-8605-d4fc64fb9d02)\) ou dans le cadre du modèle conceptuel \([How to: Define Custom Functions in the Conceptual Model](http://msdn.microsoft.com/fr-fr/0dad7b8b-58f6-4271-b238-f34810d68e5f)\).  Les fonctions de modèle conceptuel sont définies comme une commande Entity SQL dans l'élément [DefiningExpression](http://msdn.microsoft.com/fr-fr/d3da8d8b-a048-47ee-8d81-0c2ea3acdd3e) d'un élément [Function](http://msdn.microsoft.com/fr-fr/dc3beca7-55cf-4977-8db0-5064cdbab134) dans le modèle conceptuel.  
  
 Entity SQL permet de définir des fonctions dans la commande de requête elle\-même.  L'opérateur [FUNCTION](../../../../../../docs/framework/data/adonet/ef/language-reference/function-entity-sql.md) définit des fonctions incluses.  Vous pouvez définir plusieurs fonctions dans une même commande et ces fonctions peuvent avoir le même nom de fonction, tant que les signatures des fonctions sont uniques.  Pour plus d'informations, consultez [Résolution de surcharge des fonctions](../../../../../../docs/framework/data/adonet/ef/language-reference/function-overload-resolution-entity-sql.md).  
  
## Voir aussi  
 [Fonctions](../../../../../../docs/framework/data/adonet/ef/language-reference/functions-entity-sql.md)