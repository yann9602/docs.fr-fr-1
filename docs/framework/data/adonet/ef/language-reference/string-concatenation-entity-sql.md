---
title: "+ (concat&#233;nation de cha&#238;nes) (Entity SQL) | Microsoft Docs"
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
ms.assetid: 580130fa-6c7c-4f76-a47d-d22c27ccadf6
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# + (concat&#233;nation de cha&#238;nes) (Entity SQL)
Concatène deux chaînes.  
  
## Syntaxe  
  
```  
  
expression  
+  
expression  
  
```  
  
## Arguments  
 `expression`  
 Toute expression valide de l'un des types de données EDM.String. Les deux expressions doivent être du même type de données. Si tel n'est pas le cas, l'une doit être implicitement convertible dans le type de données de l'autre.  
  
## Types de résultats  
 Type de données qui résulte de la promotion de type implicite de deux arguments. Pour plus d’informations sur la promotion de type implicite, consultez [système de type](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md).  
  
## Exemple  
 La requête Entity SQL ci\-dessous utilise l'opérateur \+ pour concaténer deux chaînes. Cette requête est basée sur le modèle de vente AdventureWorks Sales Model. Pour compiler et exécuter cette requête, procédez comme suit :  
  
1.  Suivez la procédure indiquée dans [Procédure : exécuter une requête qui retourne des résultats PrimitiveType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).  
  
2.  Transmettez à la méthode `ExecutePrimitiveTypeQuery` la requête suivante en tant qu'argument :  
  
 [!code-csharp[DP EntityServices Concepts 2#CONCAT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#concat)]  
  
## Voir aussi  
 [Référence Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)   
 [Types de modèles conceptuels \(CSDL\)](http://msdn.microsoft.com/fr-fr/987b995f-e429-4569-9559-b4146744def4)