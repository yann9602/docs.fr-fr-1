---
title: Oracle et ADO.NET
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
ms.assetid: 8ee8e389-53cf-45cf-80bd-1df63ef34f2e
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: c615c985f885734800b471ee31451cfb8a4c8500
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="oracle-and-adonet"></a>Oracle et ADO.NET
> [!NOTE]
>  Les types dans <xref:System.Data.OracleClient> sont déconseillés. Les types restent pris en charge dans la version actuelle du .NET Framework, mais seront supprimés dans une version ultérieure. Microsoft recommande l'utilisation d'un fournisseur Oracle tiers.  
  
 Cette section décrit des fonctions et des comportements spécifiques au fournisseur de données [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] pour Oracle.  
  
 Le fournisseur de données [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] pour Oracle donne accès à une base de données Oracle utilisant l'interface OCI (Oracle Call Interface) fournie par le logiciel client Oracle. La fonctionnalité du fournisseur de données est conçue pour être similaire à celle des fournisseurs de données [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] pour [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)], OLE DB et ODBC.  
  
 Pour utiliser le fournisseur de données [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] pour Oracle, une application doit faire référence à l'espace de noms <xref:System.Data.OracleClient> comme suit :  
  
```vb  
Imports System.Data.OracleClient  
```  
  
```csharp  
using System.Data.OracleClient;  
```  
  
 Vous devez également inclure une référence à la DLL lorsque vous compilez votre code. Par exemple, si vous compilez un programme C#, votre ligne de commande doit inclure :  
  
```  
csc /r:System.Data.OracleClient.dll  
```  
  
## <a name="in-this-section"></a>Dans cette section  
 [Configuration système requise](../../../../docs/framework/data/adonet/system-requirements-for-the-dotnet-data-provider-for-oracle.md)  
 Décrit les exigences liées à l'utilisation du fournisseur de données [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] pour Oracle et décrit un certain nombre de problèmes dont il faut être conscient lors de son utilisation.  
  
 [BFILE Oracle](../../../../docs/framework/data/adonet/oracle-bfiles.md)  
 Décrit la classe <xref:System.Data.OracleClient.OracleBFile> qui est utilisée pour travailler avec le type de données Oracle BFILE.  
  
 [LOB Oracle](../../../../docs/framework/data/adonet/oracle-lobs.md)  
 Décrit la classe <xref:System.Data.OracleClient.OracleLob> qui est utilisée pour travailler avec les types de données Oracle LOB.  
  
 [REF CURSOR Oracle](../../../../docs/framework/data/adonet/oracle-ref-cursors.md)  
 Décrit la prise en charge pour le type de données Oracle REF CURSOR.  
  
 [OracleTypes](../../../../docs/framework/data/adonet/oracletypes.md)  
 Décrit les structures que vous pouvez utiliser pour travailler avec des types de données Oracle, notamment <xref:System.Data.OracleClient.OracleNumber> et <xref:System.Data.OracleClient.OracleString>.  
  
 [Séquences Oracle](../../../../docs/framework/data/adonet/oracle-sequences.md)  
 Décrit la prise en charge de l'extraction des valeurs de séquence Oracle générées par le serveur.  
  
 [Mappages de types de données Oracle](../../../../docs/framework/data/adonet/oracle-data-type-mappings.md)  
 Répertorie les types de données Oracle et leurs mappages sur le <xref:System.Data.OracleClient.OracleDataReader>.  
  
 [Transactions distribuées Oracle](../../../../docs/framework/data/adonet/oracle-distributed-transactions.md)  
 Décrit la manière dont l'objet <xref:System.Data.OracleClient.OracleConnection> s'inscrit automatiquement dans une transaction distribuée existante s'il détermine qu'une transaction est active.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Sécurisation des applications ADO.NET](../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 Présente les procédés de codage sécurisé utilisés avec [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)].  
  
 [DataSets, DataTables et DataViews](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 Explique comment créer et utiliser des `DataSets`, des `DataSets` typés, des `DataTables` et des `DataViews`.  
  
 [Extraction et modification de données dans ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 Décrit comment utiliser des données dans ADO.NET.  
  
 [SQL Server et ADO.NET](../../../../docs/framework/data/adonet/sql/index.md)  
 Décrit comment utiliser des fonctions et fonctionnalités spécifiques à [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)].  
  
 [DbProviderFactories](../../../../docs/framework/data/adonet/dbproviderfactories.md)  
 Décrit des classes génériques qui vous permettent d'écrire du code indépendant du fournisseur dans [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)].  
  
## <a name="see-also"></a>Voir aussi  
 [ADO.NET](../../../../docs/framework/data/adonet/index.md)  
 [Fournisseurs managés ADO.NET et centre de développement DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)
