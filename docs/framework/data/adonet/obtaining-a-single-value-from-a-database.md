---
title: "Obtention d'une valeur unique à partir d'une base de données"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: b38526cd-a62a-48cb-822a-e91dfa68e02d
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 513310ddfb578f127ee70059dec386f207180907
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="obtaining-a-single-value-from-a-database"></a>Obtention d'une valeur unique à partir d'une base de données
Vous aurez peut-être besoin de retourner des informations de base de données qui sont simplement une valeur unique plutôt qu'une table ou un flux de données. Par exemple, vous souhaitez retourner le résultat d’une fonction d’agrégation telles que COUNT (\*), SUM (price) ou AVG (Quantity). Le **commande** objet permet de retourner des valeurs uniques à l’aide de la **ExecuteScalar** (méthode). Le **ExecuteScalar** méthode retourne, sous la forme d’une valeur scalaire, la valeur de la première colonne de la première ligne du jeu de résultats.  
  
 L'exemple de code suivant insère une nouvelle valeur dans la base de données en utilisant un objet <xref:System.Data.SqlClient.SqlCommand>. La méthode <xref:System.Data.SqlClient.SqlCommand.ExecuteScalar%2A> est utilisée pour retourner la valeur de la colonne d'identité de l'enregistrement inséré.  
  
 [!code-csharp[DataWorks SqlCommand.ExecuteScalar#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlCommand.ExecuteScalar/CS/source.cs#1)]
 [!code-vb[DataWorks SqlCommand.ExecuteScalar#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlCommand.ExecuteScalar/VB/source.vb#1)]  
  
## <a name="see-also"></a>Voir aussi  
 [Commandes et paramètres](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [Exécution d’une commande](../../../../docs/framework/data/adonet/executing-a-command.md)  
 [DbConnection, DbCommand et DbException](../../../../docs/framework/data/adonet/dbconnection-dbcommand-and-dbexception.md)  
 [Fournisseurs managés ADO.NET et centre de développement DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)
