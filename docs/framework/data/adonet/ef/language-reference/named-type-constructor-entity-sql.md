---
title: "Constructeur de type nomm&#233; (Entity SQL) | Microsoft Docs"
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
ms.assetid: 549dea04-d93d-4c87-a292-f81b1598dbfd
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# Constructeur de type nomm&#233; (Entity SQL)
Permet de créer des instances des types nominaux de modèle conceptuel, tels que les types d'entités ou complexes.  
  
## Syntaxe  
  
```  
  
[{identifier. }] identifier( [expression [{, expression }]] )  
```  
  
## Arguments  
 `identifier`  
 Valeur correspondant à un identificateur simple ou entre guillemets. Pour plus d’informations, consultez [Identificateurs](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md)  
  
 `expression`  
 Attributs du type supposés se trouver dans le même ordre d'apparition que dans la déclaration du type.  
  
## Valeur de retour  
 Instances de types complexes et de types d'entités nommés.  
  
## Notes  
 Les exemples suivants montrent comment construire des types nominaux et des types complexes :  
  
 L'expression ci\-dessous crée une instance de type `Person` :  
  
 `Person("abc", 12)`  
  
 L'expression ci\-dessous crée une instance d'un type complexe :  
  
 `MyModel.ZipCode(‘98118’, ‘4567’)`  
  
 L'expression ci\-dessous crée une instance d'un type complexe imbriqué :  
  
 `MyModel.AddressInfo('My street address', 'Seattle', 'WA', MyModel.ZipCode('98118', '4567'))`  
  
 L'expression ci\-dessous crée une instance d'une entité avec un type complexe imbriqué :  
  
 `MyModel.Person("Bill", MyModel.AddressInfo('My street address', 'Seattle', 'WA', MyModel.ZipCode('98118', '4567')))`  
  
 L'exemple suivant montre comment initialiser une propriété d'un type complexe en valeur null : `MyModel.ZipCode(‘98118’, null)`  
  
## Exemple  
 La requête Entity SQL ci\-dessous utilise le constructeur de type nommé pour créer une instance d'un type de modèle conceptuel. Cette requête est basée sur le modèle de vente AdventureWorks Sales Model. Pour compiler et exécuter cette requête, procédez comme suit :  
  
1.  Suivez la procédure indiquée dans [Procédure : exécuter une requête qui retourne des résultats StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Transmettez à la méthode `ExecuteStructuralTypeQuery` la requête suivante en tant qu'argument :  
  
 [!code-csharp[DP EntityServices Concepts 2#NAMED_TYPE_CONSTRUCTOR](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#named_type_constructor)]  
  
## Voir aussi  
 [Construction de types](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md)   
 [Référence Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)