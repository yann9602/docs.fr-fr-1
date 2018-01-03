---
title: "Exécution d'une commande"
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
ms.assetid: 40494916-c25a-4cb8-8f7c-fcb8d378464e
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 43fb2d8e42aeae5340874ab082f33257b197eac3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="executing-a-command"></a>Exécution d'une commande
Chaque fournisseur de données .NET Framework inclus avec le .NET Framework possède son propre objet de commande qui hérite de <xref:System.Data.Common.DbCommand>. Le fournisseur de données .NET Framework pour OLE DB inclut un objet <xref:System.Data.OleDb.OleDbCommand>, le fournisseur de données .NET Framework pour SQL Server inclut un objet <xref:System.Data.SqlClient.SqlCommand>, le fournisseur de données .NET Framework pour ODBC inclut un objet <xref:System.Data.Odbc.OdbcCommand> et le fournisseur de données .NET Framework pour Oracle inclut un objet <xref:System.Data.OracleClient.OracleCommand>. Chacun de ces objets expose des méthodes pour exécuter les commandes en fonction du type de commande et de la valeur de retour souhaitée, comme cela est décrit dans le tableau ci-dessous.  
  
|Commande|Valeur de retour|  
|-------------|------------------|  
|`ExecuteReader`|Retourne un objet `DataReader`.|  
|`ExecuteScalar`|Retourne une valeur scalaire unique.|  
|`ExecuteNonQuery`|Exécute une commande qui ne retourne aucune ligne.|  
|`ExecuteXMLReader`|Retourne un <xref:System.Xml.XmlReader>. Disponible pour un objet `SqlCommand` uniquement.|  
  
 Chaque objet de commande fortement typé prend également en charge une énumération <xref:System.Data.CommandType> qui spécifie la manière dont une chaîne de commande est interprétée, comme cela est décrit dans le tableau ci-dessous.  
  
|CommandType|Description|  
|-----------------|-----------------|  
|`Text`|Commande SQL qui définit les instructions à exécuter au niveau de la source de données.|  
|`StoredProcedure`|Nom de la procédure stockée. Vous pouvez utiliser la propriété `Parameters` d'une commande pour accéder aux paramètres d'entrée et de sortie et aux valeurs de retour, quelle que soit la méthode `Execute` appelée. Lorsque vous utilisez `ExecuteReader`, les valeurs de retour et les paramètres de sortie ne seront pas accessibles tant que `DataReader` ne sera pas fermé.|  
|`TableDirect`|Nom d'une table.|  
  
## <a name="example"></a>Exemple  
 L'exemple de code ci-dessous montre comment créer un objet <xref:System.Data.SqlClient.SqlCommand> pour exécuter une procédure stockée en définissant ses propriétés. Un objet <xref:System.Data.SqlClient.SqlParameter> permet de spécifier le paramètre d'entrée de la procédure stockée. La commande est exécutée à l'aide de la méthode <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> et la sortie de <xref:System.Data.SqlClient.SqlDataReader> est affichée dans la fenêtre de console.  
  
 [!code-csharp[DataWorks SqlClient.StoredProcedure#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.StoredProcedure/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.StoredProcedure#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.StoredProcedure/VB/source.vb#1)]  
  
### <a name="troubleshooting-commands"></a>Dépannage des commandes  
 Le fournisseur de données .NET Framework pour SQL Server ajoute des compteurs de performance pour vous permettre de détecter des problèmes intermittents liés à des échecs lors de l'exécution des commandes. Pour plus d’informations, consultez [les compteurs de Performance](../../../../docs/framework/data/adonet/performance-counters.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Commandes et paramètres](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [DataAdapters et DataReaders](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [Utilisation de DataReaders](http://msdn.microsoft.com/en-us/126a966a-d08d-4d22-a19f-f432908b2b54)  
 [Fournisseurs managés ADO.NET et centre de développement DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)
