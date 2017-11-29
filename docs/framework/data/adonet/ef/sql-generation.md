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
# <a name="sql-generation"></a><span data-ttu-id="4f656-102">Génération SQL</span><span class="sxs-lookup"><span data-stu-id="4f656-102">SQL Generation</span></span>
<span data-ttu-id="4f656-103">Lorsque vous écrivez un fournisseur pour [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], vous devez traduire des arborescences de commandes [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] dans un langage SQL qu'une base de données spécifique puisse comprendre, tel que Transact-SQL pour SQL Server ou PL/SQL pour Oracle.</span><span class="sxs-lookup"><span data-stu-id="4f656-103">When you write a provider for the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], you must translate [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] command trees into SQL that a specific database can understand, such as Transact-SQL for SQL Server or PL/SQL for Oracle.</span></span> <span data-ttu-id="4f656-104">Dans cette section, vous allez apprendre à développer un composant de génération SQL (pour les requêtes SELECT) pour un fournisseur [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4f656-104">In this section, you will learn how to develop a SQL generation component (for SELECT queries) for an [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] provider.</span></span> <span data-ttu-id="4f656-105">Pour plus d’informations sur les insérer, mettre à jour et supprimer des requêtes, consultez [génération SQL de Modification](../../../../../docs/framework/data/adonet/ef/modification-sql-generation.md).</span><span class="sxs-lookup"><span data-stu-id="4f656-105">For information about insert, update, and delete queries, see [Modification SQL Generation](../../../../../docs/framework/data/adonet/ef/modification-sql-generation.md).</span></span>  
  
 <span data-ttu-id="4f656-106">Pour comprendre cette section, vous devez être familiarisé avec [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] et le modèle de fournisseur ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="4f656-106">To understand this section, you should be familiar with the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] and the ADO.NET Provider Model.</span></span> <span data-ttu-id="4f656-107">Vous devez également comprendre les arborescences de commandes et les <xref:System.Data.Common.CommandTrees.DbExpression>.</span><span class="sxs-lookup"><span data-stu-id="4f656-107">You should also understand command trees and <xref:System.Data.Common.CommandTrees.DbExpression>.</span></span>  
  
## <a name="the-role-of-the-sql-generation-module"></a><span data-ttu-id="4f656-108">Rôle du module de génération SQL</span><span class="sxs-lookup"><span data-stu-id="4f656-108">The Role of the SQL Generation Module</span></span>  
 <span data-ttu-id="4f656-109">Le module de génération SQL d'un fournisseur [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] traduit une arborescence de commandes d'une requête donnée en instruction SQL SELECT unique qui cible une base de données conforme SQL:1999.</span><span class="sxs-lookup"><span data-stu-id="4f656-109">The SQL generation module of an [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] provider translates a given query command tree into a single SQL SELECT statement that targets a SQL:1999-compliant database.</span></span> <span data-ttu-id="4f656-110">Le SQL généré doit avoir aussi peu de requêtes imbriquées que possible.</span><span class="sxs-lookup"><span data-stu-id="4f656-110">The generated SQL should have as few nested queries as possible.</span></span> <span data-ttu-id="4f656-111">Le module de génération SQL ne doit pas simplifier l'arborescence de commandes de requête de sortie.</span><span class="sxs-lookup"><span data-stu-id="4f656-111">The SQL generation module should not simplify the output query command tree.</span></span> <span data-ttu-id="4f656-112">[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] le fera, par exemple en éliminant des jointures et en réduisant des nœuds de filtre consécutifs.</span><span class="sxs-lookup"><span data-stu-id="4f656-112">The [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] will do this, for example by eliminating joins and collapsing consecutive filter nodes.</span></span>  
  
 <span data-ttu-id="4f656-113">Le <!--zz<xref:System.Data.Common.DBProviderServices> --> `System.Data.Common.DBProviderServices` classe est le point de départ pour l’accès à la couche de génération SQL pour convertir des arborescences de commandes en <!--zz<xref:System.Data.Common.DbCommands>--> `System.Data.Common.DbCommands`.</span><span class="sxs-lookup"><span data-stu-id="4f656-113">The <!--zz<xref:System.Data.Common.DBProviderServices> --> `System.Data.Common.DBProviderServices`  class is the starting point for accessing the SQL generation layer to convert command trees into <!--zz<xref:System.Data.Common.DbCommands>--> `System.Data.Common.DbCommands`.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4f656-114">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="4f656-114">In This Section</span></span>  
 [<span data-ttu-id="4f656-115">La forme des arborescences de commandes</span><span class="sxs-lookup"><span data-stu-id="4f656-115">The Shape of the Command Trees</span></span>](../../../../../docs/framework/data/adonet/ef/the-shape-of-the-command-trees.md)  
  
 [<span data-ttu-id="4f656-116">Génération SQL à partir d’arborescences de commandes - meilleures pratiques</span><span class="sxs-lookup"><span data-stu-id="4f656-116">Generating SQL from Command Trees - Best Practices</span></span>](../../../../../docs/framework/data/adonet/ef/generating-sql-from-command-trees-best-practices.md)  
  
 [<span data-ttu-id="4f656-117">Génération SQL dans l’exemple de fournisseur</span><span class="sxs-lookup"><span data-stu-id="4f656-117">SQL Generation in the Sample Provider</span></span>](../../../../../docs/framework/data/adonet/ef/sql-generation-in-the-sample-provider.md)  
  
## <a name="see-also"></a><span data-ttu-id="4f656-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4f656-118">See Also</span></span>  
 [<span data-ttu-id="4f656-119">L’écriture d’un fournisseur de données Entity Framework</span><span class="sxs-lookup"><span data-stu-id="4f656-119">Writing an Entity Framework Data Provider</span></span>](../../../../../docs/framework/data/adonet/ef/writing-an-ef-data-provider.md)
