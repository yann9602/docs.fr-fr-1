---
title: "Types de donn&#233;es de base | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: eca2c472-9548-4800-bd31-5d8d9f11752b
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# Types de donn&#233;es de base
Les requêtes LINQ to SQL sont traduites en données Transact\-SQL avant d'être exécutées sur Microsoft SQL Server.  LINQ to SQL prend en charge une grande partie des fonctionnalités intégrées que SQL Server prend en charge pour les types de données de base.  
  
## Effectuer un cast  
 Les casts implicites ou explicites sont activés d'un type CLR source en un type CLR cible s'il existe une conversion valide semblable dans SQL Server.  Pour plus d'informations sur le cast CLR, consultez [CType, fonction](../Topic/CType%20Function%20\(Visual%20Basic\).md) \([!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)]\) et [as](../Topic/as%20\(C%23%20Reference\).md).  Après la conversion, les casts modifient le comportement d'opérations effectuées sur une expression CLR pour correspondre au comportement d'autres expressions CLR qui mappent naturellement au type de destination. Les casts sont également traduisibles dans le contexte de mappage d'héritage.  Les objets peuvent être castés à des sous\-types d'entité plus spécifiques afin que les données spécifiques à leur sous\-type soient accessibles.  
  
## Opérateurs d'égalité  
 LINQ to SQL prend en charge les opérateurs d'égalité suivants sur les types de données de base à l'intérieur des requêtes LINQ to SQL :  
  
-   Opérateurs d'égalité et d'inégalité : les opérateurs d'égalité et d'inégalité sont pris en charge pour les types numérique, <xref:System.Boolean>, <xref:System.DateTime>et <xref:System.TimeSpan>.  Pour plus d'informations sur les opérateurs [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] `=` et `<>`, consultez [Comparison Operators](../Topic/Comparison%20Operators%20\(Visual%20Basic\).md). Pour plus d'informations sur les opérateurs de comparaison C\# `==` et `!=`, consultez [\=\=, opérateur](../Topic/==%20Operator%20\(C%23%20Reference\).md) et [\!\=, opérateur](../Topic/!=%20Operator%20\(C%23%20Reference\).md), respectivement.  
  
-   Opérateur Is : l'opérateur `IS` a une traduction prise en charge lorsque le mappage d'héritage est utilisé.  Il peut être utilisé à la place du test direct de la colonne de discriminateur afin de déterminer si un objet correspond à un type d'entité spécifique et se traduit en un contrôle sur la colonne de discriminateur.  Pour plus d'informations sur les opérateurs Visual Basic et C\# Is, consultez [Is Operator](../Topic/Is%20Operator%20\(Visual%20Basic\).md) et [is](../Topic/is%20\(C%23%20Reference\).md).  
  
## Voir aussi  
 [Mappage de type SQL\-CLR](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md)   
 [Fonctions et types de données](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)