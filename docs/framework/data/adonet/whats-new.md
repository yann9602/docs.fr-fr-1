---
title: "Quel &#39; nouveauté dans ADO.NET"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3bb65d38-cce2-46f5-b979-e5c505e95e10
caps.latest.revision: "25"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 3944fb6d68ed054feb8d7ddec149745b78810ee2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="what39s-new-in-adonet"></a>Quel &#39; nouveauté dans ADO.NET
Les fonctionnalités suivantes sont nouvelles dans [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] dans le [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)].  
  
## <a name="sqlclient-data-provider"></a>Fournisseur de données SqlClient  
 Les fonctionnalités suivantes sont nouvelles dans le fournisseur de données [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] pour [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] dans [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)] :  
  
-   Les mots clés de chaîne de connexion ConnectRetryCount et ConnectRetryInterval (<xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>) vous permettent de contrôler la fonctionnalité de résilience des connexions inactives.  
  
-   La diffusion en continu [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] vers une application prend en charge des scénarios où les données sur le serveur ne sont pas structurées.  Consultez [prise en charge de la diffusion en continu SqlClient](../../../../docs/framework/data/adonet/sqlclient-streaming-support.md) pour plus d’informations.  
  
-   La prise en charge a été ajoutée pour la programmation asynchrone.  Consultez [de programmation asynchrone](../../../../docs/framework/data/adonet/asynchronous-programming.md) pour plus d’informations.  
  
-   Les échecs de connexion sont désormais enregistrés dans le journal des événements étendus. Pour plus d’informations, consultez [Traçage de données dans ADO.NET](../../../../docs/framework/data/adonet/data-tracing.md).  
  
-   SqlClient prend désormais en charge la haute disponibilité [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)], la fonctionnalité de récupération d'urgence, AlwaysOn. Pour plus d’informations, consultez [prise en charge de SqlClient pour la haute disponibilité, la récupération d’urgence](../../../../docs/framework/data/adonet/sql/sqlclient-support-for-high-availability-disaster-recovery.md).  
  
-   Un mot de passe peut être passé comme <xref:System.Security.SecureString> lorsque vous utilisez l'authentification [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)]. Pour plus d'informations, voir <xref:System.Data.SqlClient.SqlCredential>.  
  
-   Lorsque `TrustServerCertificate` a la valeur false et `Encrypt` a la valeur true, le nom du serveur (ou l'adresse IP) dans un certificat SSL [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] doit correspondre exactement au nom du serveur (ou à l'adresse IP) spécifié dans la chaîne de connexion. Sinon, la connexion échouera. Pour plus d'informations, consultez la description de l'option de connexion `Encrypt` dans <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.  
  
     Si cette modification empêche une application existante de se connecter, vous pouvez résoudre le problème de l'application en utilisant l'un des éléments suivants :  
  
    -   Délivrez un certificat qui spécifie le nom court dans le champ de nom commun (CN) ou d'autre nom de l'objet (SAN). Cette solution fonctionne pour la mise en miroir de base de données.  
  
    -   Ajoutez un alias qui mappe le nom court au nom de domaine complet.  
  
    -   Utilisez le nom de domaine qualifié complet dans la chaîne de connexion.  
  
-   SqlClient prend en charge la protection étendue. Pour plus d’informations sur la Protection étendue, consultez [la connexion à la base de données du moteur à l’aide de la Protection étendue](http://go.microsoft.com/fwlink/?LinkId=219978).  
  
-   SqlClient prend en charge les connexions aux bases de données LocalDB. Pour plus d’informations, consultez [prise en charge de SqlClient pour LocalDB](../../../../docs/framework/data/adonet/sql/sqlclient-support-for-localdb.md).  
  
-   `Type System Version=SQL Server 2012;` est une nouvelle valeur à passer à la propriété de connexion `Type System Version`. La valeur `Type System Version=Latest;` est désormais obsolète et a été rendue équivalente à `Type System Version=SQL Server 2008;`. Pour plus d'informations, consultez <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.  
  
-   SqlClient fournit la prise en charge supplémentaire des colonnes éparses, une fonctionnalité ajoutée dans SQL Server 2008. Si votre application accède déjà aux données dans un table qui utilise des colonnes éparses, vous devez constater une augmentation des performances. La colonne IsColumnSet de <xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A> indique si une colonne est une colonne éparse qui est membre d'un jeu de colonnes. <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A>Indique si une colonne est une colonne fragmentée (consultez [Collections de schémas SQL Server](../../../../docs/framework/data/adonet/sql-server-schema-collections.md) pour plus d’informations). Pour plus d’informations sur les colonnes éparses, consultez [à l’aide des colonnes éparses](http://go.microsoft.com/fwlink/?LinkId=224244).  
  
-   L'assembly Microsoft.SqlServer.Types.dll, contenant les types de données spatiales, a été mis à niveau de la version 10.0 vers la version 11.0. Les applications qui référencent cet assembly peuvent échouer. Pour plus d’informations, consultez [modifications avec rupture des fonctionnalités du moteur de base de données](http://go.microsoft.com/fwlink/?LinkId=224367).  
  
## <a name="adonet-entity-framework"></a>ADO.NET Entity Framework  
 [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)] ajoute des API qui permettent d'ajouter de nouveaux scénarios lorsque vous utilisez Entity Framework 5.0. Pour plus d’informations sur les améliorations et fonctionnalités qui ont été ajoutées à Entity Framework 5.0, consultez les rubriques suivantes : [Nouveautés](http://go.microsoft.com/fwlink/?LinkID=251106) et [versions et Entity Framework le contrôle de version](http://go.microsoft.com/fwlink/?LinkId=234899).  
  
## <a name="see-also"></a>Voir aussi  
 [ADO.NET](../../../../docs/framework/data/adonet/index.md)  
 [Vue d’ensemble d’ADO.NET](../../../../docs/framework/data/adonet/ado-net-overview.md)  
 [SQL Server et ADO.NET](../../../../docs/framework/data/adonet/sql/index.md)  
 [Nouveautés de WCF Data Services](http://msdn.microsoft.com/en-us/cf22cad5-b8d9-472b-8d7c-b863b64eaae8)  
 [Fournisseurs managés ADO.NET et centre de développement DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)
