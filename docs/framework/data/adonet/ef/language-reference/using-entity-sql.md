---
title: "USING (Entity SQL) | Microsoft Docs"
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
  - "ESQL"
ms.assetid: 20f58b8f-6070-4456-b7e8-5ff3d6269273
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# USING (Entity SQL)
Spécifie les espaces de noms utilisés dans une expression de requête.  
  
## Syntaxe  
  
```  
USING [ alias = ] namespace  
```  
  
## Arguments  
 `alias`  
 Spécifie un alias plus court avec lequel qualifier un espace de noms.  
  
 `namespace`  
 Tout espace de noms valide.  
  
## Exemple  
 La requête Entity SQL ci\-dessous utilise l'opérateur USING pour spécifier les espaces de noms utilisés dans une expression de requête.  Pour compiler et exécuter cette requête, procédez comme suit :  
  
1.  Suivez la procédure indiquée dans [Procédure : exécuter une requête qui retourne des résultats PrimitiveType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).  
  
2.  Transmettez à la méthode `ExecutePrimitiveTypeQuery` la requête suivante en tant qu'argument :  
  
```  
using SqlServer; RAND()  
```  
  
## Voir aussi  
 [Espaces de noms](../../../../../../docs/framework/data/adonet/ef/language-reference/namespaces-entity-sql.md)   
 [Référence Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)