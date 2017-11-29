---
title: "Mappages de types de données dans ADO.NET"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d4afab94-ada6-4c77-a73c-41f17bae6b5a
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 65f9d8a6182c5882a173a3a3733c1c0c220efbf6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="data-type-mappings-in-adonet"></a>Mappages de types de données dans ADO.NET
Le .NET Framework est basé sur le système de type commun, qui définit la manière dont les types sont déclarés, utilisés et gérés dans le runtime. Il est constitué de types de valeur et de types de référence, qui dérivent tous du type de base <xref:System.Object>. Lorsque vous travaillez avec une source de données, le type de données est déduit du fournisseur de données s'il n'est pas explicitement spécifié. Par exemple, un objet <xref:System.Data.DataSet> est indépendant de toute source de données spécifique. Les données d'un `DataSet` sont extraites d'une source de données et les modifications y sont répercutées à l'aide d'un `DataAdapter`. Autrement dit, lorsqu'un `DataAdapter` remplit un objet <xref:System.Data.DataTable> dans un `DataSet` avec des valeurs provenant d'une source de données, les types de données des colonnes du `DataTable` qui en résultent sont des types [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] et non des types spécifiques au fournisseur de données [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] utilisé pour la connexion à la source de données.  
  
 De même, lorsqu'un `DataReader` retourne une valeur d'une source de données, la valeur résultante est stockée dans une variable locale de type [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]. Pour les opérations `Fill` du `DataAdapter` comme pour les méthodes `Get` du `DataReader`, le type [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] est déduit de la valeur retournée du fournisseur de données [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].  
  
 Si vous ne souhaitez pas utiliser le type de données déduit, vous pouvez appeler les méthodes d'accesseur typé du `DataReader`, lorsque vous connaissez le type spécifique de la valeur retournée. Ces méthodes permettent d'obtenir des performances optimales en retournant une valeur comme type [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] spécifique, évitant ainsi toute conversion de type supplémentaire.  
  
> [!NOTE]
>  Les valeurs null des types de données du fournisseur de données [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] sont représentées par `DBNull.Value`.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Mappages de Type de données SQL Server](../../../../docs/framework/data/adonet/sql-server-data-type-mappings.md)  
 Répertorie les mappages de types de données déduits et les méthodes d'accesseur de données pour <xref:System.Data.SqlClient>.  
  
 [Mappages de types de données OLE DB](../../../../docs/framework/data/adonet/ole-db-data-type-mappings.md)  
 Répertorie les mappages de types de données déduits et les méthodes d'accesseur de données pour <xref:System.Data.OleDb>.  
  
 [Mappages de types de données ODBC](../../../../docs/framework/data/adonet/odbc-data-type-mappings.md)  
 Répertorie les mappages de types de données déduits et les méthodes d'accesseur de données pour <xref:System.Data.Odbc>.  
  
 [Mappages de types de données Oracle](../../../../docs/framework/data/adonet/oracle-data-type-mappings.md)  
 Répertorie les mappages de types de données déduits et les méthodes d'accesseur de données pour <xref:System.Data.OracleClient>.  
  
 [Chiffres à virgule flottante](../../../../docs/framework/data/adonet/floating-point-numbers.md)  
 Décrit les problèmes que les développeurs rencontrent fréquemment lorsqu'ils utilisent des nombres à virgule flottante.  
  
## <a name="see-also"></a>Voir aussi  
 [Types de données SQL Server et ADO.NET](../../../../docs/framework/data/adonet/sql/sql-server-data-types.md)  
 [Configuration des paramètres et des Types de données de paramètre](../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md)  
 [La récupération des informations de schéma de base de données](../../../../docs/framework/data/adonet/retrieving-database-schema-information.md)  
 [Système de type commun](../../../../docs/standard/base-types/common-type-system.md)  
 [Conversion de Types](http://msdn.microsoft.com/en-us/6038316e-bdaf-4f55-8006-407f591ce156)  
 [Fournisseurs managés ADO.NET et centre de développement DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)
