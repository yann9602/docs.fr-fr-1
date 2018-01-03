---
title: "Mise en miroir de bases de données dans SQL Server"
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
ms.assetid: 89befaff-bb46-4290-8382-e67cdb0e3de9
caps.latest.revision: "6"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 6956d48163f9b9da66258c0dbb3452beab5420d9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="database-mirroring-in-sql-server"></a>Mise en miroir de bases de données dans SQL Server
La mise en miroir des bases de données dans SQL Server vous permet de conserver une copie, ou miroir, d'une base de données SQL Server sur un serveur en veille. La mise en miroir garantit que deux copies distinctes des données existent en permanence, en offrant une haute disponibilité et une redondance complète des données. Le fournisseur de données .NET pour SQL Server offre une prise en charge implicite de la mise en miroir de base de données, de façon à ce que le développeur ne doive pas exécuter d'action ni écrire de code une fois qu'il a été configuré pour une base de données SQL Server. En outre, l'objet <xref:System.Data.SqlClient.SqlConnection> prend en charge un mode de connexion explicite qui permet la fourniture du nom d'un serveur partenaire de basculement dans la propriété <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.  
  
 La séquence d'événements simplifiée suivante se produit pour un objet <xref:System.Data.SqlClient.SqlConnection> qui vise une base de données configurée pour la mise en miroir :  
  
1.  L'application cliente se connecte avec succès à la base de données principale et le serveur renvoie le nom du serveur partenaire, qui est ensuite mis en cache sur le client.  
  
2.  En cas d'échec du serveur contenant la base de données principale ou d'interruption de la connectivité, l'état de la connexion et de la transaction est perdu. L'application cliente tente de rétablir une connexion à la base de données principale et échoue.  
  
3.  L'application cliente tente ensuite de façon transparente d'établir une connexion avec la base de données miroir sur le serveur partenaire. Si elle réussit, la connexion est redirigée vers la base de données miroir qui devient alors la nouvelle base de données principale.  
  
## <a name="specifying-the-failover-partner-in-the-connection-string"></a>Spécification du partenaire de basculement dans la chaîne de connexion  
 Si vous fournissez le nom d'un serveur partenaire de basculement dans la chaîne de connexion, le client essaie d'établir de façon transparente une connexion avec ce partenaire si la base de données principale est indisponible lors de la première connexion de l'application cliente.  
  
```  
";Failover Partner=PartnerServerName"  
```  
  
 Si vous omettez le nom du serveur partenaire de basculement et que la base de données principale est indisponible lors de la première connexion de l'application cliente, un <xref:System.Data.SqlClient.SqlException> est déclenché.  
  
 Lorsqu'un <xref:System.Data.SqlClient.SqlConnection> est correctement ouvert, le nom du partenaire de basculement est retourné par le serveur et remplace toute valeur fournie dans la chaîne de connexion.  
  
> [!NOTE]
>  Vous devez spécifier explicitement le nom de catalogue ou de base de données initial dans la chaîne de connexion pour les scénarios de mise en miroir de bases de données. Si le client reçoit des informations de basculement sur une connexion qui n'a pas de base de données ou de catalogue initial spécifié explicitement, les informations de basculement ne sont pas mises en cache et l'application ne tente pas de basculer en cas d'échec du serveur principal. Si une chaîne de connexion a une valeur pour le partenaire de basculement, mais pas de valeur pour la base de donneés ou le catalogue initial, un `InvalidArgumentException` est déclenché.  
  
## <a name="retrieving-the-current-server-name"></a>Extraction du nom de serveur actuel  
 En cas de basculement, vous pouvez extraire le nom du serveur auquel la connexion actuelle est réellement connectée en utilisant la propriété <xref:System.Data.SqlClient.SqlConnection.DataSource%2A> d'un objet <xref:System.Data.SqlClient.SqlConnection>. Le fragment de code suivant extrait le nom du serveur actif, en partant de l'hypothèse que la variable de connexion fait référence à un <xref:System.Data.SqlClient.SqlConnection> ouvert.  
  
 Lorsqu’un événement de basculement se produit et de la connexion est basculée vers le serveur miroir, le **DataSource** propriété est mise à jour pour refléter le nom du miroir.  
  
```vb  
Dim activeServer As String = connection.DataSource  
```  
  
```csharp  
string activeServer = connection.DataSource;  
```  
  
## <a name="sqlclient-mirroring-behavior"></a>Comportement de mise en miroir de SqlClient  
 Le client tente toujours de se connecter au serveur principal actuel. S'il échoue, il essaie le partenaire de basculement. Si la base de données miroir a déjà été basculée vers le rôle principal sur le serveur partenaire, la connexion réussit et le nouveau mappage miroir-principal est envoyé au client et mis en cache pendant la durée de l'appel <xref:System.AppDomain>. Il n’est pas stocké dans un stockage persistant et n’est pas disponible pour les connexions suivantes dans un autre **AppDomain** ou processus. Toutefois, il est disponible pour les connexions suivantes au sein du même **AppDomain**. Notez qu’un autre **AppDomain** ou processus qui s’exécute toujours sur le même ou un autre ordinateur doté de son pool de connexions, et ces connexions ne sont pas réinitialisées. Dans ce cas, si la base de données principal tombe en panne, chaque processus ou **AppDomain** échoue une fois et le pool est automatiquement effacé.  
  
> [!NOTE]
>  La prise en charge de la mise en miroir sur le serveur est configurée pour chaque base de données. Si des opérations de manipulation des données sont exécutées sur d'autres bases de données non incluses dans l'ensemble principal/miroir, soit en utilisant des noms multipart, soit en modifiant la base de données en cours, les modifications apportées à ces autres bases de données ne sont pas propagées en cas d'échec. Aucune erreur n'est générée en cas de modification des données d'une base de données non mise en miroir. Le développeur doit évoluer l'impact possible de telles opérations.  
  
## <a name="database-mirroring-resources"></a>Ressources relatives à la mise en miroir de bases de données  
 Pour obtenir des informations et de la documentation conceptuelle sur la configuration, le déploiement et l'administration de la mise en miroir, voir les ressources suivantes dans la documentation en ligne de SQL Server.  
  
|Ressource|Description|  
|--------------|-----------------|  
|[La mise en miroir de base de données](http://msdn.microsoft.com/library/bb934127.aspx) dans la documentation en ligne de SQL Server|Décrit comment installer et configurer la mise en miroir dans SQL Server.|  
  
## <a name="see-also"></a>Voir aussi  
 [Fournisseurs managés ADO.NET et centre de développement DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)
