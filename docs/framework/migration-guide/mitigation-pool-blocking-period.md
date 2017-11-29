---
title: "Atténuation : Période de blocage du pool"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 92d2de20-79be-4df1-b182-144143a8866a
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 8749e2d7b91e611ee153c6f36708fa34a44ecccd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="mitigation-pool-blocking-period"></a>Atténuation : Période de blocage du pool
La période de blocage du pool de connexions a été supprimée pour les connexions aux bases de données SQL Azure.  
  
## <a name="additional-description"></a>Description complémentaire  
 Dans le [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] et les versions antérieures, quand une application rencontre un échec temporaire lors de la connexion à une base de données, la connexion ne peut pas être retentée rapidement, car le pool de connexions met l’erreur en cache, puis l’affiche de nouveau pendant 5 secondes à 1 minute. Pour plus d’informations, consultez [Regroupement de connexions SQL Server (ADO.NET)](../../../docs/framework/data/adonet/sql-server-connection-pooling.md). Ce comportement pose problème pour les connexions aux bases de données SQL Azure, qui échouent souvent avec des erreurs temporaires, généralement rétablies au bout de quelques secondes. La fonctionnalité de blocage du pool de connexions signifie que l’application ne peut pas se connecter à la base de données pendant une période prolongée, même si la base de données est disponible. Ce comportement est particulièrement problématique pour les applications web qui se connectent aux bases de données SQL Azure et qui doivent obtenir un affichage en quelques secondes.  
  
 À compter du [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], pour les demandes d’ouverture de connexion envoyées aux bases de données SQL Azure connues (*.database.windows.net, \*.database.chinacloudapi.cn, \*.database.usgovcloudapi.net, \*.database.cloudapi.de), les erreurs d’ouverture de connexion ne sont pas mises en cache. Pour toutes les autres tentatives de connexion, la période de blocage du pool de connexions continue d’être appliquée.  
  
## <a name="impact"></a>Impact  
 Ce changement permet aux demandes d’ouverture de connexion d’être retentées immédiatement pour les bases de données SQL Azure, ce qui améliore les performances des applications cloud.  
  
## <a name="mitigation"></a>Atténuation  
 Pour les applications qui sont affectées par ce changement, vous pouvez configurer la période de blocage du pool de connexions en définissant la nouvelle propriété <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod%2A>.  La valeur de la propriété est un membre de l’énumération <xref:System.Data.SqlClient.PoolBlockingPeriod?displayProperty=nameWithType> qui peut prendre l’une des trois valeurs suivantes :  
  
-   `PoolBlockingPeriod.AlwaysBlock` 
  
-   `PoolBlockingPeriod.Auto`  
  
-   `PoolBlockingPeriod.NeverBlock` 
  
 Vous pouvez restaurer le comportement précédent en affectant la valeur `PoolBlockingPeriod.AlwaysBlock` à la propriété <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod%2A>.  
  
## <a name="see-also"></a>Voir aussi  
 [Modifications du runtime](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-6-2.md)
