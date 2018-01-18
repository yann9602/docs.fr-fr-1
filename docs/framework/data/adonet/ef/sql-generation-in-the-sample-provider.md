---
title: "Génération SQL dans le Fournisseur d'exemples"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e70f553d-4622-4627-928e-1aa2ee605d8e
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 7a7f95f7432fdac00a34e7d878ef979656a7af4e
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="sql-generation-in-the-sample-provider"></a><span data-ttu-id="9cc4c-102">Génération SQL dans le Fournisseur d'exemples</span><span class="sxs-lookup"><span data-stu-id="9cc4c-102">SQL Generation in the Sample Provider</span></span>
<span data-ttu-id="9cc4c-103">Le [Entity Framework Sample Provider](http://go.microsoft.com/fwlink/?LinkId=180616) illustre les composants de fournisseurs de données ADO.NET qui prennent en charge la [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9cc4c-103">The [Entity Framework Sample Provider](http://go.microsoft.com/fwlink/?LinkId=180616) demonstrates the new components of ADO.NET Data Providers that support the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span>  <span data-ttu-id="9cc4c-104">Il utilise une base de données SQL Server 2005 et est implémenté comme un wrapper pour le fournisseur de données System.Data.SqlClient ADO.NET 2.0.</span><span class="sxs-lookup"><span data-stu-id="9cc4c-104">It works with a SQL Server 2005 database and is implemented as a wrapper for the System.Data.SqlClient ADO.NET 2.0 Data Provider.</span></span>  
  
 <span data-ttu-id="9cc4c-105">Le module Génération SQL du Fournisseur d'exemples (situé sous le dossier Génération SQL, à l'exception du fichier DmlSqlGenerator.cs) prend un DbQueryCommandTree d'entrée et produit une instruction SQL SELECT unique.</span><span class="sxs-lookup"><span data-stu-id="9cc4c-105">The SQL Generation module of the Sample Provider (located under the SQL Generation folder, except for the file DmlSqlGenerator.cs) takes an input DbQueryCommandTree and produces a single SQL SELECT statement.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9cc4c-106">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="9cc4c-106">In This Section</span></span>  
 <span data-ttu-id="9cc4c-107">Cette section comprend les rubriques suivantes :</span><span class="sxs-lookup"><span data-stu-id="9cc4c-107">This section includes the following topics:</span></span>  
  
 [<span data-ttu-id="9cc4c-108">Architecture et conception</span><span class="sxs-lookup"><span data-stu-id="9cc4c-108">Architecture and Design</span></span>](../../../../../docs/framework/data/adonet/ef/architecture-and-design.md)  
  
 [<span data-ttu-id="9cc4c-109">Procédure pas à pas : génération SQL</span><span class="sxs-lookup"><span data-stu-id="9cc4c-109">Walkthrough: SQL Generation</span></span>](../../../../../docs/framework/data/adonet/ef/walkthrough-sql-generation.md)  
  
## <a name="see-also"></a><span data-ttu-id="9cc4c-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9cc4c-110">See Also</span></span>  
 [<span data-ttu-id="9cc4c-111">Génération SQL</span><span class="sxs-lookup"><span data-stu-id="9cc4c-111">SQL Generation</span></span>](../../../../../docs/framework/data/adonet/ef/sql-generation.md)
