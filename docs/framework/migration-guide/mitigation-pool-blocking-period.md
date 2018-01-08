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
ms.workload: dotnet
ms.openlocfilehash: 42eaddeb2714a8c294f45d24eb7e6d9cf216fecc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="mitigation-pool-blocking-period"></a><span data-ttu-id="71bc1-102">Atténuation : Période de blocage du pool</span><span class="sxs-lookup"><span data-stu-id="71bc1-102">Mitigation: Pool Blocking Period</span></span>
<span data-ttu-id="71bc1-103">La période de blocage du pool de connexions a été supprimée pour les connexions aux bases de données SQL Azure.</span><span class="sxs-lookup"><span data-stu-id="71bc1-103">The connection pool blocking period has been removed for connections to Azure SQL databases.</span></span>  
  
## <a name="additional-description"></a><span data-ttu-id="71bc1-104">Description complémentaire</span><span class="sxs-lookup"><span data-stu-id="71bc1-104">Additional description</span></span>  
 <span data-ttu-id="71bc1-105">Dans le [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] et les versions antérieures, quand une application rencontre un échec temporaire lors de la connexion à une base de données, la connexion ne peut pas être retentée rapidement, car le pool de connexions met l’erreur en cache, puis l’affiche de nouveau pendant 5 secondes à 1 minute. Pour plus d’informations, consultez [Regroupement de connexions SQL Server (ADO.NET)](../../../docs/framework/data/adonet/sql-server-connection-pooling.md).</span><span class="sxs-lookup"><span data-stu-id="71bc1-105">In the [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] and earlier versions, when an app encounters a transient connection failure when connecting to a database, the connection attempt cannot be retried quickly, because the connection pool caches the error and re-throws it for 5 seconds to 1 min. For more information, see [SQL Server Connection Pooling (ADO.NET)](../../../docs/framework/data/adonet/sql-server-connection-pooling.md).</span></span> <span data-ttu-id="71bc1-106">Ce comportement pose problème pour les connexions aux bases de données SQL Azure, qui échouent souvent avec des erreurs temporaires, généralement rétablies au bout de quelques secondes.</span><span class="sxs-lookup"><span data-stu-id="71bc1-106">This behavior is problematic for connections to Azure SQL databases, which often fail with transient errors that are typically recovered from within a few seconds.</span></span> <span data-ttu-id="71bc1-107">La fonctionnalité de blocage du pool de connexions signifie que l’application ne peut pas se connecter à la base de données pendant une période prolongée, même si la base de données est disponible.</span><span class="sxs-lookup"><span data-stu-id="71bc1-107">The connection pool blocking feature means that the app cannot connect to the database for an extensive period, even though the database is available.</span></span> <span data-ttu-id="71bc1-108">Ce comportement est particulièrement problématique pour les applications web qui se connectent aux bases de données SQL Azure et qui doivent obtenir un affichage en quelques secondes.</span><span class="sxs-lookup"><span data-stu-id="71bc1-108">This behavior is particularly problematic for web apps that connect to Azure SQL databases and that need to render within a few seconds.</span></span>  
  
 <span data-ttu-id="71bc1-109">À compter du [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], pour les demandes d’ouverture de connexion envoyées aux bases de données SQL Azure connues (*.database.windows.net, \*.database.chinacloudapi.cn, \*.database.usgovcloudapi.net, \*.database.cloudapi.de), les erreurs d’ouverture de connexion ne sont pas mises en cache.</span><span class="sxs-lookup"><span data-stu-id="71bc1-109">Starting with the [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], for connection open requests to known Azure SQL databases (*.database.windows.net, \*.database.chinacloudapi.cn, \*.database.usgovcloudapi.net, \*.database.cloudapi.de), connection open errors are not cached.</span></span> <span data-ttu-id="71bc1-110">Pour toutes les autres tentatives de connexion, la période de blocage du pool de connexions continue d’être appliquée.</span><span class="sxs-lookup"><span data-stu-id="71bc1-110">For all other connection attempts, the connection pool blocking period continues to be enforced.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="71bc1-111">Impact</span><span class="sxs-lookup"><span data-stu-id="71bc1-111">Impact</span></span>  
 <span data-ttu-id="71bc1-112">Ce changement permet aux demandes d’ouverture de connexion d’être retentées immédiatement pour les bases de données SQL Azure, ce qui améliore les performances des applications cloud.</span><span class="sxs-lookup"><span data-stu-id="71bc1-112">This change allows the connection open attempt to be retried immediately for Azure SQL databases, thereby improving the performance of cloud-enabled apps.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="71bc1-113">Atténuation</span><span class="sxs-lookup"><span data-stu-id="71bc1-113">Mitigation</span></span>  
 <span data-ttu-id="71bc1-114">Pour les applications qui sont affectées par ce changement, vous pouvez configurer la période de blocage du pool de connexions en définissant la nouvelle propriété <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod%2A>.</span><span class="sxs-lookup"><span data-stu-id="71bc1-114">For apps that are adversely affected by this change, the connection pool blocking period can be configured by setting the new <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod%2A> property.</span></span>  <span data-ttu-id="71bc1-115">La valeur de la propriété est un membre de l’énumération <xref:System.Data.SqlClient.PoolBlockingPeriod?displayProperty=nameWithType> qui peut prendre l’une des trois valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="71bc1-115">The value of the property is a member of the <xref:System.Data.SqlClient.PoolBlockingPeriod?displayProperty=nameWithType> enumeration that can take either of three values:</span></span>  
  
-   `PoolBlockingPeriod.AlwaysBlock` 
  
-   `PoolBlockingPeriod.Auto`  
  
-   `PoolBlockingPeriod.NeverBlock` 
  
 <span data-ttu-id="71bc1-116">Vous pouvez restaurer le comportement précédent en affectant la valeur `PoolBlockingPeriod.AlwaysBlock` à la propriété <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod%2A>.</span><span class="sxs-lookup"><span data-stu-id="71bc1-116">The previous behavior can be restored by setting the <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod%2A> property to `PoolBlockingPeriod.AlwaysBlock`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71bc1-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="71bc1-117">See Also</span></span>  
 [<span data-ttu-id="71bc1-118">Modifications du runtime</span><span class="sxs-lookup"><span data-stu-id="71bc1-118">Runtime Changes</span></span>](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-6-2.md)
