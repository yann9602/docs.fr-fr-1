---
title: "DataSets typ&#233;s | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 033d2548-cf24-4c05-8179-67d8b009c048
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# DataSets typ&#233;s
En plus d'un accès par liaison tardive aux valeurs via des variables faiblement typées, l'objet <xref:System.Data.DataSet> permet un accès aux données par l'intermédiaire d'une métaphore fortement typée.  Les tables et les colonnes qui appartiennent au **DataSet** sont accessibles à l'aide de noms conviviaux pour l'utilisateur et de variables fortement typées.  
  
 Un **DataSet** typé est une classe dérivée d'un **DataSet**.  En tant que tel, il hérite de l'ensemble des méthodes, événements et propriétés d'un **DataSet**.  En outre, un **DataSet** typé fournit des méthodes, événements et propriétés fortement typés.  Cela signifie que vous pouvez accéder à des tables et à des colonnes par leur nom au lieu d'utiliser les méthodes associées à des collections.  Un **DataSet** typé permet non seulement d'améliorer la lisibilité du code, mais aussi d'obtenir de l'éditeur de code Visual Studio .NET qu'il complète automatiquement les lignes à mesure que vous les tapez.  
  
 Un **DataSet** fortement typé vous permet encore d'accéder à des valeurs avec le type approprié au moment de la compilation.  Avec un **DataSet** fortement typé, les erreurs d'incompatibilité de types sont interceptées non pas à l'exécution, mais dès la compilation.  
  
## Dans cette section  
 [Génération d'objets DataSet fortement typés](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-strongly-typed-datasets.md)  
 Explique comment créer et utiliser un **DataSet** fortement typé.  
  
 [Annotation de DataSets typés](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/annotating-typed-datasets.md)  
 Explique comment annoter le schéma XSD \(XML Schema Definition language\) utilisé pour générer un **DataSet** fortement typé afin de donner aux éléments du **DataSet** des noms conviviaux sans pour autant modifier le schéma sous\-jacent.  
  
## Voir aussi  
 [Objets DataSet, DataTable et DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)   
 [Fournisseurs managés ADO.NET et Centre de développement de DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)