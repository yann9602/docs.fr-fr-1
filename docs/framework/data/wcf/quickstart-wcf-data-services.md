---
title: "Démarrage rapide (services de données WCF)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF Data Services, quick-start example
- WCF Data Services, Entity Data Model (EDM) service
ms.assetid: 7b18ca1e-d4d6-4c7a-afb9-ce3cebb98a8d
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 08296be1002ee50e18a45c546645f4cc117d6bb5
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="quickstart-wcf-data-services"></a><span data-ttu-id="d513a-102">Démarrage rapide (services de données WCF)</span><span class="sxs-lookup"><span data-stu-id="d513a-102">Quickstart (WCF Data Services)</span></span>
<span data-ttu-id="d513a-103">Ce démarrage rapide vous aide à vous familiariser avec [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] et [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] via une série de tâches qui prennent en charge les rubriques de [mise en route](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="d513a-103">This quickstart helps you become familiar with [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] and the [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] through a series of tasks that support the topics in [Getting Started](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md).</span></span>  
  
## <a name="what-you-will-learn"></a><span data-ttu-id="d513a-104">Contenu du didacticiel</span><span class="sxs-lookup"><span data-stu-id="d513a-104">What You Will Learn</span></span>  
 <span data-ttu-id="d513a-105">La première tâche dans ce démarrage rapide montre comment créer un service de données pour exposer un flux [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] issu de l'exemple de base de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="d513a-105">The first task in this quickstart shows how to create a data service to expose an [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed from the Northwind sample database.</span></span> <span data-ttu-id="d513a-106">Dans les rubriques ultérieures, vous accéderez au flux [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] à l'aide d'un navigateur Web et vous créerez également une application cliente [!INCLUDE[avalon1](../../../../includes/avalon1-md.md)] qui consomme le flux [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] à l'aide de bibliothèques clientes.</span><span class="sxs-lookup"><span data-stu-id="d513a-106">In later topics, you will access the [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed by using a Web browser, and also create a [!INCLUDE[avalon1](../../../../includes/avalon1-md.md)] client application that consumes the [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed by using client libraries.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="d513a-107">Composants requis</span><span class="sxs-lookup"><span data-stu-id="d513a-107">Prerequisites</span></span>  
 <span data-ttu-id="d513a-108">Pour effectuer ce démarrage rapide, vous devez installer les composants suivants :</span><span class="sxs-lookup"><span data-stu-id="d513a-108">To complete this quickstart, you must install the following components:</span></span>  
  
-   [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)]<span data-ttu-id="d513a-109">.</span><span class="sxs-lookup"><span data-stu-id="d513a-109">.</span></span>  
  
-   <span data-ttu-id="d513a-110">Une instance de [!INCLUDE[msCoName](../../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d513a-110">An instance of [!INCLUDE[msCoName](../../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="d513a-111">Ceci comprend SQL Server Express, qui est inclus dans une installation par défaut de [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d513a-111">This includes SQL Server Express, which is included in a default installation of [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)].</span></span>  
  
-   <span data-ttu-id="d513a-112">Exemple de base de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="d513a-112">The Northwind sample database.</span></span> <span data-ttu-id="d513a-113">Pour télécharger cet exemple de base de données, consultez la page de téléchargement, [Exemples de bases de données pour SQL Server](http://go.microsoft.com/fwlink/?linkid=24758).</span><span class="sxs-lookup"><span data-stu-id="d513a-113">To download this sample database, see the download page, [Sample Databases for SQL Server](http://go.microsoft.com/fwlink/?linkid=24758).</span></span>  
  
## <a name="wcf-data-services-quickstart-tasks"></a><span data-ttu-id="d513a-114">Tâches de démarrage rapide WCF Data Services</span><span class="sxs-lookup"><span data-stu-id="d513a-114">WCF Data Services Quickstart Tasks</span></span>  
 [<span data-ttu-id="d513a-115">Création du service de données</span><span class="sxs-lookup"><span data-stu-id="d513a-115">Creating the Data Service</span></span>](../../../../docs/framework/data/wcf/creating-the-data-service.md)  
 <span data-ttu-id="d513a-116">Définir l'application [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] , définir le modèle de données, créer le service de données et autoriser l'accès aux ressources.</span><span class="sxs-lookup"><span data-stu-id="d513a-116">Define the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] application, define the data model, create the data service, and enable access to resources.</span></span>  
  
 [<span data-ttu-id="d513a-117">L’accès au Service à partir d’un navigateur Web</span><span class="sxs-lookup"><span data-stu-id="d513a-117">Accessing the Service from a Web Browser</span></span>](../../../../docs/framework/data/wcf/accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md)  
 <span data-ttu-id="d513a-118">Démarrer le service à partir de [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] et y accéder en soumettant des demandes HTTP GET au flux exposé via un navigateur Web.</span><span class="sxs-lookup"><span data-stu-id="d513a-118">Start the service from [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] and access the service by submitting HTTP GET requests through a Web browser to the exposed feed.</span></span>  
  
 [<span data-ttu-id="d513a-119">Création de l’Application cliente .NET Framework</span><span class="sxs-lookup"><span data-stu-id="d513a-119">Creating the .NET Framework Client Application</span></span>](../../../../docs/framework/data/wcf/creating-the-dotnet-client-application-wcf-data-services-quickstart.md)  
 <span data-ttu-id="d513a-120">Créer une application cliente [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] pour consommer le flux [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] , lier des données aux contrôles Windows, modifier les données liées dans les contrôles dépendants, puis renvoyer les modifications au service de données.</span><span class="sxs-lookup"><span data-stu-id="d513a-120">Create a [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] client application to consume the [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed, bind data to Windows controls, change data in the bound controls, and then send the changes back to the data service.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d513a-121">Les fichiers projet d’une version terminée du démarrage rapide peuvent être téléchargés à partir de la page [WCF Data Services Quickstart (OData Service and WPF Client)](http://go.microsoft.com/fwlink/?LinkId=179994) .</span><span class="sxs-lookup"><span data-stu-id="d513a-121">Project files from a completed version of the quickstart can be downloaded from the [WCF Data Services Documentation Samples](http://go.microsoft.com/fwlink/?LinkId=179994) page.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="d513a-122">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="d513a-122">Next Steps</span></span>  
 <span data-ttu-id="d513a-123">[Démarrer le didacticiel Démarrage rapide](../../../../docs/framework/data/wcf/creating-the-data-service.md).</span><span class="sxs-lookup"><span data-stu-id="d513a-123">[Start the Quickstart](../../../../docs/framework/data/wcf/creating-the-data-service.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d513a-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d513a-124">See Also</span></span>  
 [<span data-ttu-id="d513a-125">ADO.NET Entity Framework</span><span class="sxs-lookup"><span data-stu-id="d513a-125">ADO.NET Entity Framework</span></span>](../../../../docs/framework/data/adonet/ef/index.md)
