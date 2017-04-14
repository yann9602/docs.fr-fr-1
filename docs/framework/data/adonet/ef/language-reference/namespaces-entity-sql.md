---
title: "Espaces de noms (Entity SQL) | Microsoft Docs"
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
ms.assetid: 83991c21-60db-4af9-aca3-b416f6cae98e
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# Espaces de noms (Entity SQL)
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] introduit les espaces de noms afin d'éviter les conflits de noms des identificateurs globaux tels que les noms de types, les jeux d'entités, les fonctions, etc.  La prise en charge des espaces de noms dans [!INCLUDE[esql](../../../../../../includes/esql-md.md)] est identique à la prise en charge des espaces de noms dans le [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)].  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] fournit deux formes de la clause USING : les espaces de noms qualifiés \(où un alias plus court est fourni pour l'espace de noms\) et les espaces de noms non qualifiés, tels qu'illustrés dans l'exemple suivant :  
  
 `USING System.Data;`  
  
 `USING tsql = System.Data;`  
  
## Règles de résolution de noms  
 Si un identificateur ne peut pas être résolu dans les portées locales, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tente de localiser le nom dans les portées globales \(les espaces de noms\).  [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tente tout d'abord de faire correspondre l'identificateur \(préfixe\) avec l'un des espaces de noms qualifiés.  Si une correspondance est trouvée, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tente de résoudre le reste de l'identificateur dans l'espace de noms spécifié.  Si aucune correspondance n'est trouvée, une exception est levée.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tente ensuite de rechercher l'identificateur dans tous les espaces de noms non qualifiés \(spécifiés dans le prologue\).  Si l'identificateur est localisé dans exactement un espace de noms, cet emplacement est retourné.  Si plusieurs espaces de noms ont une correspondance pour cet identificateur, une exception est levée.  Si aucun espace de noms ne peut être identifié pour l'identificateur, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] passe le nom à l'étendue externe suivante \(l'objet <xref:System.Data.Common.DbCommand> ou <xref:System.Data.Common.DbConnection>\), comme illustré dans l'exemple suivant :  
  
```  
SELECT TREAT(p AS NamespaceName.Employee)  
FROM ContainerName.Person AS p  
WHERE p IS OF (NamespaceName.Employee)  
```  
  
## Différences par rapport au .NET Framework  
 Dans le [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)], vous pouvez utiliser des espaces de noms partiellement qualifiés.  [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ne permet pas cela.  
  
## Utilisation d'ADO.NET  
 Les requêtes sont exprimées par le biais d'objets <xref:System.Data.Common.DbCommand> ADO.NET.  Les objets <xref:System.Data.Common.DbCommand> peuvent être créés à partir d'objets <xref:System.Data.Common.DbConnection>.  Il est également possible de spécifier des espaces de noms comme faisant partie des objets <xref:System.Data.Common.DbCommand> et <xref:System.Data.Common.DbConnection>.  Si [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ne peut pas résoudre un identificateur dans la requête elle\-même, les espaces de noms externes sont détectés \(en se basant sur les mêmes règles\).  
  
## Voir aussi  
 [Référence Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)   
 [Vue d'ensemble d'Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)