---
title: "Notifications de requête dans SQL Server"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0f0ba1a1-3180-4af8-87f7-c795dc8f8f55
caps.latest.revision: "6"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 376f2cfefcaf53affe5a20a5812a02839dd5d4a9
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="query-notifications-in-sql-server"></a><span data-ttu-id="a5c3d-102">Notifications de requête dans SQL Server</span><span class="sxs-lookup"><span data-stu-id="a5c3d-102">Query Notifications in SQL Server</span></span>
<span data-ttu-id="a5c3d-103">Basées sur l'infrastructure Service Broker, les notifications de requête permettent de notifier des applications en cas de modification de données.</span><span class="sxs-lookup"><span data-stu-id="a5c3d-103">Built upon the Service Broker infrastructure, query notifications allow applications to be notified when data has changed.</span></span> <span data-ttu-id="a5c3d-104">Cette fonction est particulièrement utile pour les applications qui génèrent un cache d'informations à partir d'une base de données, telles que les applications Web, et qui doivent être informées en cas de modification des données sources.</span><span class="sxs-lookup"><span data-stu-id="a5c3d-104">This feature is particularly useful for applications that provide a cache of information from a database, such as a Web application, and need to be notified when the source data is changed.</span></span>  
  
 <span data-ttu-id="a5c3d-105">ADO.NET vous permet d'implémenter les notifications de requête de trois manières :</span><span class="sxs-lookup"><span data-stu-id="a5c3d-105">There are three ways you can implement query notifications using ADO.NET:</span></span>  
  
1.  <span data-ttu-id="a5c3d-106">L'implémentation de bas niveau est assurée par la classe `SqlNotificationRequest` qui expose les fonctionnalités côté serveur, vous permettant d'exécuter une commande avec une demande de notification.</span><span class="sxs-lookup"><span data-stu-id="a5c3d-106">The low-level implementation is provided by the `SqlNotificationRequest` class that exposes server-side functionality, enabling you to execute a command with a notification request.</span></span>  
  
2.  <span data-ttu-id="a5c3d-107">L'implémentation de haut niveau est assurée par la classe `SqlDependency` qui fournit une abstraction de haut niveau des fonctionnalités de notification entre l'application source et SQL Server, ce qui vous permet d'utiliser une dépendance pour détecter des modifications au niveau serveur.</span><span class="sxs-lookup"><span data-stu-id="a5c3d-107">The high-level implementation is provided by the `SqlDependency` class, which is a class that provides a high-level abstraction of notification functionality between the source application and SQL Server, enabling you to use a dependency to detect changes in the server.</span></span> <span data-ttu-id="a5c3d-108">Généralement, il s'agit de la manière la plus simple et la plus efficace, pour des applications clientes managées, d'exploiter la fonctionnalité de notification de SQL Server en utilisant le fournisseur de données .NET Framework pour SQL Server.</span><span class="sxs-lookup"><span data-stu-id="a5c3d-108">In most cases, this is the simplest and most effective way to leverage SQL Server notifications capability by managed client applications using the .NET Framework Data Provider for SQL Server.</span></span>  
  
3.  <span data-ttu-id="a5c3d-109">En outre, les applications Web créées à l'aide d'ASP.NET 2.0 ou version ultérieure peuvent utiliser les classes d'assistance `SqlCacheDependency`.</span><span class="sxs-lookup"><span data-stu-id="a5c3d-109">In addition, Web applications built using ASP.NET 2.0 or later can use the `SqlCacheDependency` helper classes.</span></span>  
  
 <span data-ttu-id="a5c3d-110">Les notifications de requête sont utilisées pour les applications qui doivent actualiser des affichages ou des caches suite à l'apport de modifications aux données sous-jacentes.</span><span class="sxs-lookup"><span data-stu-id="a5c3d-110">Query notifications are used for applications that need to refresh displays or caches in response to changes in underlying data.</span></span> <span data-ttu-id="a5c3d-111">Microsoft SQL Server permet aux applications .NET Framework d'envoyer une commande à SQL Server et de demander la génération d'une notification si l'exécution de cette commande produit des ensembles de résultats différents de ceux extraits initialement.</span><span class="sxs-lookup"><span data-stu-id="a5c3d-111">Microsoft SQL Server allows .NET Framework applications to send a command to SQL Server and request notification if executing the same command would produce result sets different from those initially retrieved.</span></span> <span data-ttu-id="a5c3d-112">Les notifications générées au niveau du serveur sont envoyées via des files d'attente pour être traitées ultérieurement.</span><span class="sxs-lookup"><span data-stu-id="a5c3d-112">Notifications generated at the server are sent through queues to be processed later.</span></span>  
  
 <span data-ttu-id="a5c3d-113">Vous pouvez configurer des notifications pour les instructions SELECT et EXECUTE.</span><span class="sxs-lookup"><span data-stu-id="a5c3d-113">You can set up notifications for SELECT and EXECUTE statements.</span></span> <span data-ttu-id="a5c3d-114">Avec une instruction EXECUTE, SQL Server enregistre une notification pour la commande exécutée et non l'instruction EXECUTE elle-même.</span><span class="sxs-lookup"><span data-stu-id="a5c3d-114">When using an EXECUTE statement, SQL Server registers a notification for the command executed rather than the EXECUTE statement itself.</span></span> <span data-ttu-id="a5c3d-115">La commande doit répondre aux spécifications et aux limitations d'une instruction SELECT.</span><span class="sxs-lookup"><span data-stu-id="a5c3d-115">The command must meet the requirements and limitations for a SELECT statement.</span></span> <span data-ttu-id="a5c3d-116">Lorsqu'une commande qui enregistre une notification contient plusieurs instructions, le moteur de base de données crée une notification pour chaque instruction du lot.</span><span class="sxs-lookup"><span data-stu-id="a5c3d-116">When a command that registers a notification contains more than one statement, the Database Engine creates a notification for each statement in the batch.</span></span>  
  
 <span data-ttu-id="a5c3d-117">Si vous développez une application où vous avez besoin des notifications de seconde fiable lorsque les données modifiées, consultez les sections **planification d’une stratégie de Notifications de requête efficace** et **Alternatives à la requête Notifications** dans les [planification des Notifications](http://go.microsoft.com/fwlink/?LinkId=211984) rubrique dans la documentation en ligne de SQL Server.</span><span class="sxs-lookup"><span data-stu-id="a5c3d-117">If you are developing an application where you need reliable sub-second notifications when data changes, review the sections **Planning an Efficient Query Notifications Strategy** and **Alternatives to Query Notifications** in the [Planning for Notifications](http://go.microsoft.com/fwlink/?LinkId=211984) topic in SQL Server Books Online.</span></span> <span data-ttu-id="a5c3d-118">Pour plus d'informations sur les notifications de requête et Service Broker de SQL Server, voir les liens aux rubriques ci-dessous dans la documentation en ligne de SQL Server.</span><span class="sxs-lookup"><span data-stu-id="a5c3d-118">For more information about Query Notifications and SQL Server Service Broker, see the following links to topics in SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="a5c3d-119">**Documentation en ligne de SQL Server**</span><span class="sxs-lookup"><span data-stu-id="a5c3d-119">**SQL Server Books Online**</span></span>  
  
-   [<span data-ttu-id="a5c3d-120">À l’aide de Notifications de requête</span><span class="sxs-lookup"><span data-stu-id="a5c3d-120">Using Query Notifications</span></span>](http://msdn.microsoft.com/library/ms175110.aspx)  
  
-   [<span data-ttu-id="a5c3d-121">Création d’une requête de Notification</span><span class="sxs-lookup"><span data-stu-id="a5c3d-121">Creating a Query for Notification</span></span>](http://msdn.microsoft.com/library/ms181122.aspx)  
  
-   [<span data-ttu-id="a5c3d-122">Service Broker</span><span class="sxs-lookup"><span data-stu-id="a5c3d-122">Service Broker</span></span>](http://msdn.microsoft.com/library/bb522889.aspx)  
  
-   [<span data-ttu-id="a5c3d-123">Centre d’informations du développeur Service Broker</span><span class="sxs-lookup"><span data-stu-id="a5c3d-123">Service Broker Developer InfoCenter</span></span>](http://msdn.microsoft.com/library/ms166100.aspx)  
  
-   [<span data-ttu-id="a5c3d-124">Développement (Service Broker)</span><span class="sxs-lookup"><span data-stu-id="a5c3d-124">Development (Service Broker)</span></span>](http://msdn.microsoft.com/library/bb522908.aspx)  
  
## <a name="in-this-section"></a><span data-ttu-id="a5c3d-125">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="a5c3d-125">In This Section</span></span>  
 [<span data-ttu-id="a5c3d-126">Activation de notifications de requête</span><span class="sxs-lookup"><span data-stu-id="a5c3d-126">Enabling Query Notifications</span></span>](../../../../../docs/framework/data/adonet/sql/enabling-query-notifications.md)  
 <span data-ttu-id="a5c3d-127">Explique comment utiliser des notifications de requête incluant les exigences relatives à leur utilisation et à leur activation.</span><span class="sxs-lookup"><span data-stu-id="a5c3d-127">Discusses how to use query notifications, including the requirements for enabling and using them.</span></span>  
  
 [<span data-ttu-id="a5c3d-128">SqlDependency dans une application ASP.NET</span><span class="sxs-lookup"><span data-stu-id="a5c3d-128">SqlDependency in an ASP.NET Application</span></span>](../../../../../docs/framework/data/adonet/sql/sqldependency-in-an-aspnet-app.md)  
 <span data-ttu-id="a5c3d-129">Montre comment utiliser les notifications de requête à partir d'une application ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="a5c3d-129">Demonstrates how to use query notifications from an ASP.NET application.</span></span>  
  
 [<span data-ttu-id="a5c3d-130">Détection des modifications avec SqlDependency</span><span class="sxs-lookup"><span data-stu-id="a5c3d-130">Detecting Changes with SqlDependency</span></span>](../../../../../docs/framework/data/adonet/sql/detecting-changes-with-sqldependency.md)  
 <span data-ttu-id="a5c3d-131">Montre comment détecter lorsque les résultats de la requête seront différents de ceux reçus à l'origine.</span><span class="sxs-lookup"><span data-stu-id="a5c3d-131">Demonstrates how to detect when query results will be different from those originally received.</span></span>  
  
 [<span data-ttu-id="a5c3d-132">Exécution de SqlCommand avec une SqlNotificationRequest</span><span class="sxs-lookup"><span data-stu-id="a5c3d-132">SqlCommand Execution with a SqlNotificationRequest</span></span>](../../../../../docs/framework/data/adonet/sql/sqlcommand-execution-with-a-sqlnotificationrequest.md)  
 <span data-ttu-id="a5c3d-133">Illustre la configuration d'un objet <xref:System.Data.SqlClient.SqlCommand> pour travailler avec une notification de requête.</span><span class="sxs-lookup"><span data-stu-id="a5c3d-133">Demonstrates configuring a <xref:System.Data.SqlClient.SqlCommand> object to work with a query notification.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="a5c3d-134">Référence</span><span class="sxs-lookup"><span data-stu-id="a5c3d-134">Reference</span></span>  
 <xref:System.Data.Sql.SqlNotificationRequest>  
 <span data-ttu-id="a5c3d-135">Décrit la classe <xref:System.Data.Sql.SqlNotificationRequest> et tous ses membres.</span><span class="sxs-lookup"><span data-stu-id="a5c3d-135">Describes the <xref:System.Data.Sql.SqlNotificationRequest> class and all of its members.</span></span>  
  
 <xref:System.Data.SqlClient.SqlDependency>  
 <span data-ttu-id="a5c3d-136">Décrit la classe <xref:System.Data.SqlClient.SqlDependency> et tous ses membres.</span><span class="sxs-lookup"><span data-stu-id="a5c3d-136">Describes the <xref:System.Data.SqlClient.SqlDependency> class and all of its members.</span></span>  
  
 <xref:System.Web.Caching.SqlCacheDependency>  
 <span data-ttu-id="a5c3d-137">Décrit la classe <xref:System.Web.Caching.SqlCacheDependency> et tous ses membres.</span><span class="sxs-lookup"><span data-stu-id="a5c3d-137">Describes the <xref:System.Web.Caching.SqlCacheDependency> class and all of its members.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5c3d-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a5c3d-138">See Also</span></span>  
 [<span data-ttu-id="a5c3d-139">SQL Server et ADO.NET</span><span class="sxs-lookup"><span data-stu-id="a5c3d-139">SQL Server and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/index.md)  
 [<span data-ttu-id="a5c3d-140">Fournisseurs managés ADO.NET et centre de développement DataSet</span><span class="sxs-lookup"><span data-stu-id="a5c3d-140">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
