---
title: "Génération SQL"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0e16aa02-d458-4418-a765-58b42aad9315
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 727aa0ca3e1673a5bbd29884077ed5aa65d792f2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="sql-generation"></a>Génération SQL
Lorsque vous écrivez un fournisseur pour [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], vous devez traduire des arborescences de commandes [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] dans un langage SQL qu'une base de données spécifique puisse comprendre, tel que Transact-SQL pour SQL Server ou PL/SQL pour Oracle. Dans cette section, vous allez apprendre à développer un composant de génération SQL (pour les requêtes SELECT) pour un fournisseur [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]. Pour plus d’informations sur les insérer, mettre à jour et supprimer des requêtes, consultez [génération SQL de Modification](../../../../../docs/framework/data/adonet/ef/modification-sql-generation.md).  
  
 Pour comprendre cette section, vous devez être familiarisé avec [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] et le modèle de fournisseur ADO.NET. Vous devez également comprendre les arborescences de commandes et les <xref:System.Data.Common.CommandTrees.DbExpression>.  
  
## <a name="the-role-of-the-sql-generation-module"></a>Rôle du module de génération SQL  
 Le module de génération SQL d'un fournisseur [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] traduit une arborescence de commandes d'une requête donnée en instruction SQL SELECT unique qui cible une base de données conforme SQL:1999. Le SQL généré doit avoir aussi peu de requêtes imbriquées que possible. Le module de génération SQL ne doit pas simplifier l'arborescence de commandes de requête de sortie. [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] le fera, par exemple en éliminant des jointures et en réduisant des nœuds de filtre consécutifs.  
  
 Le <!--zz<xref:System.Data.Common.DBProviderServices> --> `System.Data.Common.DBProviderServices` classe est le point de départ pour l’accès à la couche de génération SQL pour convertir des arborescences de commandes en <!--zz<xref:System.Data.Common.DbCommands>--> `System.Data.Common.DbCommands`.  
  
## <a name="in-this-section"></a>Dans cette section  
 [La forme des arborescences de commandes](../../../../../docs/framework/data/adonet/ef/the-shape-of-the-command-trees.md)  
  
 [Génération SQL à partir d’arborescences de commandes - meilleures pratiques](../../../../../docs/framework/data/adonet/ef/generating-sql-from-command-trees-best-practices.md)  
  
 [Génération SQL dans l’exemple de fournisseur](../../../../../docs/framework/data/adonet/ef/sql-generation-in-the-sample-provider.md)  
  
## <a name="see-also"></a>Voir aussi  
 [L’écriture d’un fournisseur de données Entity Framework](../../../../../docs/framework/data/adonet/ef/writing-an-ef-data-provider.md)
