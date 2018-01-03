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
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 853bf55f96be3adeba11ff14e36fd56631536b69
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="sql-generation-in-the-sample-provider"></a>Génération SQL dans le Fournisseur d'exemples
Le [Entity Framework Sample Provider](http://go.microsoft.com/fwlink/?LinkId=180616) illustre les composants de fournisseurs de données ADO.NET qui prennent en charge la [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].  Il utilise une base de données SQL Server 2005 et est implémenté comme un wrapper pour le fournisseur de données System.Data.SqlClient ADO.NET 2.0.  
  
 Le module Génération SQL du Fournisseur d'exemples (situé sous le dossier Génération SQL, à l'exception du fichier DmlSqlGenerator.cs) prend un DbQueryCommandTree d'entrée et produit une instruction SQL SELECT unique.  
  
## <a name="in-this-section"></a>Dans cette section  
 Cette section comprend les rubriques suivantes :  
  
 [Architecture et conception](../../../../../docs/framework/data/adonet/ef/architecture-and-design.md)  
  
 [Procédure pas à pas : génération SQL](../../../../../docs/framework/data/adonet/ef/walkthrough-sql-generation.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Génération SQL](../../../../../docs/framework/data/adonet/ef/sql-generation.md)
