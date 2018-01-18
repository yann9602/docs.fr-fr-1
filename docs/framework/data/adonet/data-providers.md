---
title: "Fournisseur de données .NET Framework"
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
ms.assetid: 03a9fc62-2d24-491a-9fe6-d6bdb6dcb131
caps.latest.revision: "13"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: ec484bc544f2889d6f37055cb9863b4806ec20c8
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="net-framework-data-providers"></a>Fournisseur de données .NET Framework
Un fournisseur de données [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] est utilisé pour la connexion à une base de données, l'exécution de commandes et l'extraction de résultats. Ces résultats sont traités directement, placés dans un objet <xref:System.Data.DataSet> pour pouvoir être exposés à l'utilisateur le cas échéant, combinés aux données de différentes sources ou accessibles à distance entre couches. Les fournisseurs de données [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] sont légers et créent une couche minimale entre la source des données et le code, ce qui augmente les performances sans nuire aux fonctionnalités.  
  
 Le tableau suivant répertorie les fournisseurs de données inclus dans le [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].  
  
|Fournisseur de données[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] |Description|  
|-------------------------------------------------------------------------------|-----------------|  
|[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Fournisseur de données pour [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)]|Fournit l'accès aux données pour Microsoft [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)]. Utilise l'espace de noms <xref:System.Data.SqlClient> .|  
|[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Fournisseur de données pour OLE DB|Pour les sources de données exposées à l'aide de OLE DB. Utilise l'espace de noms <xref:System.Data.OleDb> .|  
|[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]Fournisseur de données pour ODBC|Pour les sources de données exposées à l'aide de ODBC. Utilise l'espace de noms <xref:System.Data.Odbc> .|  
|[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Fournisseur de données pour Oracle|Pour les sources de données Oracle. Le fournisseur de données [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] pour Oracle prend en charge le logiciel client Oracle version 8.1.7 et ultérieure, et utilise l'espace de noms <xref:System.Data.OracleClient> .|  
|fournisseur EntityClient|Fournit un accès aux données pour les applications EDM (Entity Data Model). Utilise l'espace de noms <xref:System.Data.EntityClient> .|  
|Fournisseur de données [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] pour [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] Compact 4.0.|Fournit l'accès aux données pour Microsoft [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] Compact 4.0. Utilise l’espace de noms [System.Data.SqlServerCe](http://msdn.microsoft.com/library/system.data.sqlserverce.aspx) .|  
  
## <a name="core-objects-of-net-framework-data-providers"></a>Objets principaux des fournisseurs de données .NET Framework  
 Le tableau suivant présente les quatre principaux objets qui composent un fournisseur de données [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] .  
  
|Objet|Description|  
|------------|-----------------|  
|`Connection`|Établit une connexion à une source de données spécifique. La classe de base pour tous les objets `Connection` est la classe <xref:System.Data.Common.DbConnection> .|  
|`Command`|Exécute une commande sur une source de données. Expose `Parameters` et peut exécuter dans la portée d'une `Transaction` à partir d'un `Connection`. La classe de base pour tous les objets `Command` est la classe <xref:System.Data.Common.DbCommand> .|  
|`DataReader`|Lit un flux de données avant uniquement (forward only) et en lecture seule à partir d'une source de données. La classe de base pour tous les objets `DataReader` est la classe <xref:System.Data.Common.DbDataReader> .|  
|`DataAdapter`|Remplit un `DataSet` et répercute les mises à jour dans la source de données. La classe de base pour tous les objets `DataAdapter` est la classe <xref:System.Data.Common.DbDataAdapter> .|  
  
 En plus des principales classes répertoriées dans le tableau précédemment dans ce document, un fournisseur de données [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] contient également les classes répertoriées dans le tableau suivant.  
  
|Objet|Description|  
|------------|-----------------|  
|`Transaction`|Inscrit des commandes dans des transactions au niveau de la source de données. La classe de base pour tous les objets `Transaction` est la classe <xref:System.Data.Common.DbTransaction> . ADO.NET fournit aussi la prise en charge pour les transactions à l'aide des classes dans l'espace de noms <xref:System.Transactions> .|  
|`CommandBuilder`|Objet d'assistance qui génère automatiquement les propriétés de commande d'un `DataAdapter` ou dérive les informations sur les paramètres à partir d'une procédure stockée et remplit la collection `Parameters` d'un objet `Command`. La classe de base pour tous les objets `CommandBuilder` est la classe <xref:System.Data.Common.DbCommandBuilder> .|  
|`ConnectionStringBuilder`|Objet d'assistance qui offre une manière simple de créer et de gérer le contenu de chaînes de connexion utilisées par les objets `Connection` . La classe de base pour tous les objets `ConnectionStringBuilder` est la classe <xref:System.Data.Common.DbConnectionStringBuilder> .|  
|`Parameter`|Définit les paramètres des valeurs d'entrée, de sortie et de retour pour les commandes et les procédures stockées. La classe de base pour tous les objets `Parameter` est la classe <xref:System.Data.Common.DbParameter> .|  
|`Exception`|Retourné en cas d'erreur au niveau de la source de données. En cas d'erreur côté client, les fournisseurs de données [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] lèvent une exception [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]. La classe de base pour tous les objets `Exception` est la classe <xref:System.Data.Common.DbException> .|  
|`Error`|Expose les informations provenant d'un avertissement ou d'une erreur retournée par une source de données.|  
|`ClientPermission`|Fourni pour les attributs de sécurité d'accès du code du fournisseur de données [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] . La classe de base pour tous les objets `ClientPermission` est la classe <xref:System.Data.Common.DBDataPermission> .|  
  
## <a name="net-framework-data-provider-for-includessnoversionincludesssnoversion-mdmd-sqlclient"></a>Fournisseur de données .NET Framework pour [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] (SqlClient)  
 Le fournisseur de données [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] pour [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] (SqlClient) utilise son propre protocole pour communiquer avec [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)]. Il est léger et ses performances sont élevées car il est optimisé de façon à accéder directement à [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] , sans ajout d'une couche OLE DB ou ODBC (Open DataBase Connectivity). L'illustration suivante compare le fournisseur de données [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] pour [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] avec le fournisseur de données [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] pour OLE DB. Le fournisseur de données [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] pour OLE DB communique avec une source de données OLE DB à la fois par l'intermédiaire du composant de service OLE DB, qui assure le regroupement de connexion et les services de transactions, et par le biais du fournisseur OLE DB de la source de données.  
  
> [!NOTE]
>  Le fournisseur de données [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] pour ODBC présente une architecture similaire à celle du fournisseur de données [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] pour OLE DB ; par exemple, il appelle un composant de service ODBC.  
  
 ![Fournisseurs de données](../../../../docs/framework/data/adonet/media/netdataproviders-bpuedev11.gif "NETDataProviders_bpuedev11")  
Comparaison du fournisseur de données .NET Framework pour SQL Server et du fournisseur de données .NET Framework pour OLE DB  
  
 Les classes du fournisseur de données [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] pour [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] sont situées dans l'espace de noms <xref:System.Data.SqlClient> .  
  
 Le fournisseur de données [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] pour [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] prend en charge les transactions locales et distribuées. Pour les transactions distribuées, le fournisseur de données [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] pour [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)]s'inscrit automatiquement par défaut dans une transaction et obtient des détails de transaction des services de composants Windows ou <xref:System.Transactions>. Pour plus d’informations, consultez [Transactions et la concurrence](../../../../docs/framework/data/adonet/transactions-and-concurrency.md).  
  
 L'exemple de code suivant montre comment inclure l'espace de noms `System.Data.SqlClient` dans vos applications.  
  
```vb  
Imports System.Data.SqlClient  
```  
  
```csharp  
using System.Data.SqlClient;  
```  
  
## <a name="net-framework-data-provider-for-ole-db"></a>Fournisseur de données .NET Framework pour OLE DB  
 Le fournisseur de données [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] pour OLE DB (OleDb) utilise un fournisseur OLE DB natif par le biais de COM Interop pour permettre l'accès aux données. Le fournisseur de données [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] pour OLE DB prend en charge les transactions locales et distribuées. Pour les transactions distribuées, le fournisseur de données [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] pour OLE DB s'inscrit automatiquement par défaut dans une transaction et obtient des détails de transaction des services de composants Windows. Pour plus d’informations, consultez [Transactions et la concurrence](../../../../docs/framework/data/adonet/transactions-and-concurrency.md).  
  
 Le tableau suivant montre les fournisseurs qui ont été testés avec [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)].  
  
|Pilote|Fournisseur|  
|------------|--------------|  
|SQLOLEDB|Fournisseur Microsoft OLE DB pour [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)]|  
|MSDAORA|Fournisseur Microsoft OLE DB pour Oracle|  
|Microsoft.Jet.OLEDB.4.0|Fournisseur OLE DB pour Microsoft Jet|  
  
> [!NOTE]
>  Il est déconseillé d'utiliser une base de données Access (Jet) comme source de données pour les applications multithread, telles que les applications [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] . Si vous devez utiliser Jet comme source de données pour une application [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] , sachez que les applications [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] qui se connectent à une base de données Access peuvent rencontrer des problèmes de connexion.  
  
 Le fournisseur de données [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] pour OLE DB ne prend pas en charge les interfaces OLE DB version 2.5. Les fournisseurs OLE DB qui requièrent la prise en charge des interfaces OLE DB 2.5 ne fonctionneront pas correctement avec le fournisseur de données [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] pour OLE DB. C'est le cas du fournisseur Microsoft OLE DB pour Exchange et du fournisseur Microsoft OLE DB pour Internet Publishing.  
  
 Le fournisseur de données [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] pour OLE DB ne fonctionne pas avec le fournisseur OLE DB pour ODBC (MSDASQL). Pour accéder à une source de données ODBC à l'aide de [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)], utilisez le fournisseur de données [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] pour ODBC.  
  
 Les classes du fournisseur de données[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] pour OLE DB sont situées dans l'espace de noms <xref:System.Data.OleDb> . L'exemple de code suivant montre comment inclure l'espace de noms `System.Data.OleDb` dans vos applications.  
  
```vb  
Imports System.Data.OleDb  
```  
  
```csharp  
using System.Data.OleDb;  
```  
  
## <a name="net-framework-data-provider-for-odbc"></a>fournisseur de données .NET Framework pour ODBC  
 Le fournisseur de données [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] pour ODBC (Odbc) utilise le gestionnaire de pilotes (DM) ODBC natif pour permettre l'accès aux données. Le fournisseur de données pour ODBC prend en charge les transactions locales et distribuées. Pour les transactions distribuées, le fournisseur de données ODBC s’inscrit automatiquement par défaut dans une transaction et obtient des détails de transaction des services de composants Windows. Pour plus d’informations, consultez [Transactions et la concurrence](../../../../docs/framework/data/adonet/transactions-and-concurrency.md).  
  
 Le tableau suivant indique les pilotes ODBC qui ont été testés avec [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)].  
  
|Pilote|  
|------------|  
|[!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)]|  
|Microsoft ODBC pour Oracle|  
|Pilote Microsoft Access (*.mdb)|  
  
 Les classes du fournisseur de données[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] pour ODBC sont situées dans l'espace de noms <xref:System.Data.Odbc> .  
  
 L'exemple de code suivant montre comment inclure l'espace de noms `System.Data.Odbc` dans vos applications.  
  
```vb  
Imports System.Data.Odbc  
```  
  
```csharp  
using System.Data.Odbc;  
```  
  
> [!NOTE]
>  Le fournisseur de données [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] pour ODBC requiert MDAC version 2.6 ou ultérieure et MDAC 2.8 Service Pack 1 (SP1) est recommandé. Vous pouvez télécharger MDAC 2.8 SP1 à partir du [Data Access and Storage Developer Center](http://go.microsoft.com/fwlink/?linkid=4173).  
  
## <a name="net-framework-data-provider-for-oracle"></a>fournisseur de données .NET Framework pour Oracle  
 Le fournisseur de données [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] pour Oracle (OracleClient) permet l'accès aux sources de données Oracle par le biais du logiciel de connectivité client Oracle. Il prend en charge le logiciel client Oracle version 8.1.7 ou ultérieure. Le fournisseur de données prend en charge les transactions locales et distribuées. Pour plus d’informations, consultez [Transactions et la concurrence](../../../../docs/framework/data/adonet/transactions-and-concurrency.md).  
  
 Le fournisseur de données [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] pour Oracle requiert que le logiciel client Oracle (version 8.1.7 ou ultérieure) soit installé sur le système avant que vous puissiez vous connecter à une source de données Oracle.  
  
 Les classes du fournisseur de données[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] pour Oracle sont situées dans l'espace de noms <xref:System.Data.OracleClient> et sont contenues dans l'assembly `System.Data.OracleClient.dll` . Vous devez référencer `System.Data.dll` ainsi que `System.Data.OracleClient.dll` lorsque vous compilez une application qui utilise le fournisseur de données.  
  
 L'exemple de code suivant montre comment inclure l'espace de noms `System.Data.OracleClient` dans vos applications.  
  
```vb  
Imports System.Data  
Imports System.Data.OracleClient  
```  
  
```csharp  
using System.Data;  
using System.Data.OracleClient;  
```  
  
## <a name="choosing-a-net-framework-data-provider"></a>Choix d'un fournisseur de données .NET Framework  
 Selon le design et la source de données de votre application, le choix de votre fournisseur de données [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] peut améliorer les performances, les fonctionnalités et l'intégrité de votre application. Le tableau suivant présente les avantages et les limites de chaque fournisseur de données [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] .  
  
|Fournisseur|Notes|  
|--------------|-----------|  
|[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Fournisseur de données pour [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)]|Recommandé pour les applications de couche intermédiaire qui utilisent Microsoft [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)].<br /><br /> Recommandé pour les applications monocouches qui utilisent des bases de données Microsoft Database Engine (MSDE) ou [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)].<br /><br /> Recommandé par rapport à l'utilisation du fournisseur OLE DB pour [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] (SQLOLEDB) avec le fournisseur de données [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] pour OLE DB.|  
|[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Fournisseur de données pour OLE DB|Pour [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)], le fournisseur de données [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] pour [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] est recommandé à la place de ce fournisseur.<br /><br /> Il est recommandé pour les applications monocouches qui utilisent des bases de données Microsoft Access. L'utilisation d'une base de données Access pour une application de couche intermédiaire est déconseillée.|  
|[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]« Fournisseur de données pour ODBC|Recommandé pour les applications monocouches et de couche intermédiaire qui utilisent des sources de données ODBC.|  
|[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]« Fournisseur de données pour Oracle|Recommandé pour les applications monocouches et de couche intermédiaire qui utilisent des sources de données Oracle.|  
  
## <a name="entityclient-provider"></a>fournisseur EntityClient  
 Le fournisseur EntityClient permet d'accéder aux données basées sur un modèle de données d'entité EDM (Entity Data Model). Contrairement aux autres fournisseurs de données .NET Framework, il n'interagit pas directement avec une source de données. Au lieu de cela, il utilise Entity SQL pour communiquer avec le fournisseur de données sous-jacent. Pour plus d'informations, consultez [EntityClient and Entity SQL](http://msdn.microsoft.com/en-us/49202ab9-ac98-4b4b-a05c-140e422bf527).  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble d’ADO.NET](../../../../docs/framework/data/adonet/ado-net-overview.md)  
 [Extraction et modification de données dans ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [Fournisseurs managés ADO.NET et centre de développement DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)
