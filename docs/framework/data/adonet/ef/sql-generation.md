---
title: "G&#233;n&#233;ration SQL | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0e16aa02-d458-4418-a765-58b42aad9315
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# G&#233;n&#233;ration SQL
Lorsque vous écrivez un fournisseur pour [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], vous devez traduire des arborescences de commandes [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] dans un langage SQL qu'une base de données spécifique puisse comprendre, tel que Transact\-SQL pour SQL Server ou PL\/SQL pour Oracle.  Dans cette section, vous allez apprendre à développer un composant de génération SQL \(pour les requêtes SELECT\) pour un fournisseur [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].  Pour plus d'informations sur les requêtes d'insertion, de mise à jour et de suppression, consultez [Génération SQL de modification](../../../../../docs/framework/data/adonet/ef/modification-sql-generation.md).  
  
 Pour comprendre cette section, vous devez être familiarisé avec [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] et le modèle de fournisseur ADO.NET.  Vous devez également comprendre les arborescences de commandes et les <xref:System.Data.Common.CommandTrees.DbExpression>.  
  
## Rôle du module de génération SQL  
 Le module de génération SQL d'un fournisseur [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] traduit une arborescence de commandes d'une requête donnée en instruction SQL SELECT unique qui cible une base de données conforme SQL:1999.  Le SQL généré doit avoir aussi peu de requêtes imbriquées que possible.  Le module de génération SQL ne doit pas simplifier l'arborescence de commandes de requête de sortie.  [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] le fera, par exemple en éliminant des jointures et en réduisant des nœuds de filtre consécutifs.  
  
 La classe <xref:System.Data.Common.DBProviderServices> est le point de départ permettant d'accéder à la couche de génération SQL pour convertir des arborescences de commandes en <xref:System.Data.Common.DbCommands>.  
  
## Dans cette section  
 [Forme des arborescences de commandes](../../../../../docs/framework/data/adonet/ef/the-shape-of-the-command-trees.md)  
  
 [Génération SQL à partir d'arborescences de commandes \- meilleures pratiques](../../../../../docs/framework/data/adonet/ef/generating-sql-from-command-trees-best-practices.md)  
  
 [Génération SQL dans le Fournisseur d'exemples](../../../../../docs/framework/data/adonet/ef/sql-generation-in-the-sample-provider.md)  
  
## Voir aussi  
 [Écriture d'un fournisseur de données Entity Framework](../../../../../docs/framework/data/adonet/ef/writing-an-ef-data-provider.md)