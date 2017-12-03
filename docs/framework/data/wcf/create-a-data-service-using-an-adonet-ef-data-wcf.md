---
title: "Comment : créer un service de données à l’aide d’une source de données Entity Framework ADO.NET (services de données WCF)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF Data Services, providers
- WCF Data Services, Entity Framework
ms.assetid: 6d11fec8-0108-42f5-8719-2a7866d04428
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 77a4b90b16a92e993d9283932b2a609f874c7568
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-create-a-data-service-using-an-adonet-entity-framework-data-source-wcf-data-services"></a><span data-ttu-id="7a163-102">Comment : créer un service de données à l’aide d’une source de données Entity Framework ADO.NET (services de données WCF)</span><span class="sxs-lookup"><span data-stu-id="7a163-102">How to: Create a Data Service Using an ADO.NET Entity Framework Data Source (WCF Data Services)</span></span>
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]<span data-ttu-id="7a163-103"> expose les données d'entité comme un service de données.</span><span class="sxs-lookup"><span data-stu-id="7a163-103"> exposes entity data as a data service.</span></span> <span data-ttu-id="7a163-104">Ces données d'entité sont fournies par [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)][!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] lorsque la source de données est une base de données relationnelle.</span><span class="sxs-lookup"><span data-stu-id="7a163-104">This entity data is provided by the [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)][!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] when the data source is a relational database.</span></span> <span data-ttu-id="7a163-105">Cette rubrique vous indique comment créer un modèle de données basé sur [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] dans une application Web [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] qui repose sur une base de données existante et utilise ce modèle de données pour créer un service de données.</span><span class="sxs-lookup"><span data-stu-id="7a163-105">This topic shows you how to create an [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)]-based data model in a [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] Web application that is based on an existing database and use this data model to create a new data service.</span></span>  
  
 <span data-ttu-id="7a163-106">[!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] fournit également un outil en ligne de commande qui peut générer un modèle [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] en dehors d'un projet [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7a163-106">The [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] also provides a command line tool that can generate an [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] model outside of a [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] project.</span></span> <span data-ttu-id="7a163-107">Pour plus d’informations, consultez [Comment : utiliser des EdmGen.exe pour générer des fichiers de modèle et de mappage](../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span><span class="sxs-lookup"><span data-stu-id="7a163-107">For more information, see [How to: Use EdmGen.exe to Generate the Model and Mapping Files](../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span></span>  
  
### <a name="to-add-an-entity-framework-model-that-is-based-on-an-existing-database-to-an-existing-web-application"></a><span data-ttu-id="7a163-108">Pour ajouter à une application Web existante un modèle Entity Framework qui repose sur une base de données existante</span><span class="sxs-lookup"><span data-stu-id="7a163-108">To add an Entity Framework model that is based on an existing database to an existing Web application</span></span>  
  
1.  <span data-ttu-id="7a163-109">Sur le **projet** menu, cliquez sur **ajouter un nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="7a163-109">On the **Project** menu, click **Add new item**.</span></span>  
  
2.  <span data-ttu-id="7a163-110">Dans le **modèles** volet, cliquez sur le **données** catégorie, puis sélectionnez **ADO.NET Entity Data Model**.</span><span class="sxs-lookup"><span data-stu-id="7a163-110">In the **Templates** pane, click the **Data** category, and then select **ADO.NET Entity Data Model**.</span></span>  
  
3.  <span data-ttu-id="7a163-111">Tapez le nom du modèle, puis **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="7a163-111">Type the model name and then click **Add**.</span></span>  
  
     <span data-ttu-id="7a163-112">La première page de l'Assistant [!INCLUDE[adonet_edm](../../../../includes/adonet-edm-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7a163-112">The first page of the [!INCLUDE[adonet_edm](../../../../includes/adonet-edm-md.md)] Wizard is displayed.</span></span>  
  
4.  <span data-ttu-id="7a163-113">Dans le **choisir le contenu du modèle** boîte de dialogue, sélectionnez **générer à partir de la base de données**.</span><span class="sxs-lookup"><span data-stu-id="7a163-113">In the **Choose Model Contents** dialog box, select **Generate from database**.</span></span> <span data-ttu-id="7a163-114">Cliquez ensuite sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="7a163-114">Then click **Next**.</span></span>  
  
5.  <span data-ttu-id="7a163-115">Cliquez sur le **nouvelle connexion** bouton.</span><span class="sxs-lookup"><span data-stu-id="7a163-115">Click the **New Connection** button.</span></span>  
  
6.  <span data-ttu-id="7a163-116">Dans le **propriétés de connexion** boîte de dialogue, tapez le nom de votre serveur, sélectionnez la méthode d’authentification, tapez le nom de la base de données, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="7a163-116">In the **Connection Properties** dialog box, type your server name, select the authentication method, type the database name, and then click **OK**.</span></span>  
  
     <span data-ttu-id="7a163-117">Le **choisir votre connexion de données**boîte de dialogue est mis à jour avec vos paramètres de connexion de base de données.</span><span class="sxs-lookup"><span data-stu-id="7a163-117">The **Choose Your Data Connection**s dialog box is updated with your database connection settings.</span></span>  
  
7.  <span data-ttu-id="7a163-118">Vérifiez que le **enregistrer les paramètres de connexion de l’entité dans App.Config en tant que :** case à cocher est activée.</span><span class="sxs-lookup"><span data-stu-id="7a163-118">Ensure that the **Save entity connection settings in App.Config as:** checkbox is checked.</span></span> <span data-ttu-id="7a163-119">Cliquez ensuite sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="7a163-119">Then click **Next**.</span></span>  
  
8.  <span data-ttu-id="7a163-120">Dans le **choisir vos objets de base de données** boîte de dialogue, sélectionnez all de base de données des objets que vous envisagez d’exposer dans le service de données.</span><span class="sxs-lookup"><span data-stu-id="7a163-120">In the **Choose Your Database Objects** dialog box, select all of database objects that you plan to expose in the data service.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="7a163-121">Les objets inclus dans le modèle de données ne sont pas exposés automatiquement par le service de données.</span><span class="sxs-lookup"><span data-stu-id="7a163-121">Objects included in the data model are not automatically exposed by the data service.</span></span> <span data-ttu-id="7a163-122">Ils doivent être exposés explicitement par le service lui-même.</span><span class="sxs-lookup"><span data-stu-id="7a163-122">They must be explicitly exposed by the service itself.</span></span> <span data-ttu-id="7a163-123">Pour plus d’informations, consultez [configuration du Service de données](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="7a163-123">For more information, see [Configuring the Data Service](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md).</span></span>  
  
9. <span data-ttu-id="7a163-124">Cliquez sur **Terminer** pour terminer l’Assistant.</span><span class="sxs-lookup"><span data-stu-id="7a163-124">Click **Finish** to complete the wizard.</span></span>  
  
     <span data-ttu-id="7a163-125">Cela crée un modèle de données par défaut basé sur la base de données spécifique.</span><span class="sxs-lookup"><span data-stu-id="7a163-125">This creates a default data model based on the specific database.</span></span> <span data-ttu-id="7a163-126">[!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] permet de personnaliser le modèle de données.</span><span class="sxs-lookup"><span data-stu-id="7a163-126">The [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] enables to customize the data model.</span></span> <span data-ttu-id="7a163-127">Pour plus d’informations, consultez l’article [Tâches MSBuild](http://msdn.microsoft.com/en-us/7166f1f1-4de8-4bd4-86b5-5e20a2ebaccb).</span><span class="sxs-lookup"><span data-stu-id="7a163-127">For more information, see [Tasks](http://msdn.microsoft.com/en-us/7166f1f1-4de8-4bd4-86b5-5e20a2ebaccb).</span></span>  
  
### <a name="to-create-the-data-service-by-using-the-new-data-model"></a><span data-ttu-id="7a163-128">Pour créer le service de données à l'aide du nouveau modèle de données</span><span class="sxs-lookup"><span data-stu-id="7a163-128">To create the data service by using the new data model</span></span>  
  
1.  <span data-ttu-id="7a163-129">Dans [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)], ouvrez le fichier .edmx qui représente le modèle de données.</span><span class="sxs-lookup"><span data-stu-id="7a163-129">In [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)], open the .edmx file that represents the data model.</span></span>  
  
2.  <span data-ttu-id="7a163-130">Dans le **Explorateur de modèles**, cliquez sur le modèle, cliquez sur **propriétés**, puis notez le nom du conteneur d’entités.</span><span class="sxs-lookup"><span data-stu-id="7a163-130">In the **Model Browser**, right-click the model, click **Properties**, and then note the name of the entity container.</span></span>  
  
3.  <span data-ttu-id="7a163-131">Dans **l’Explorateur de solutions**, cliquez sur le nom de votre [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] de projet, puis cliquez sur **ajouter un nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="7a163-131">In **Solution Explorer**, right-click the name of your [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] project, and then click **Add New Item**.</span></span>  
  
4.  <span data-ttu-id="7a163-132">Dans le **ajouter un nouvel élément** boîte de dialogue, sélectionnez **Service de données WCF**.</span><span class="sxs-lookup"><span data-stu-id="7a163-132">In the **Add New Item** dialog box, select **WCF Data Service**.</span></span>  
  
5.  <span data-ttu-id="7a163-133">Fournissez un nom pour le service, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="7a163-133">Supply a name for the service, and then click **OK**.</span></span>  
  
     [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)]<span data-ttu-id="7a163-134"> crée le balisage XML et des fichiers de code pour le nouveau service.</span><span class="sxs-lookup"><span data-stu-id="7a163-134"> creates the XML markup and code files for the new service.</span></span> <span data-ttu-id="7a163-135">La fenêtre de l'éditeur de code s'ouvre par défaut.</span><span class="sxs-lookup"><span data-stu-id="7a163-135">By default, the code-editor window opens.</span></span>  
  
6.  <span data-ttu-id="7a163-136">Dans le code pour le service de données, remplacez le commentaire `/* TODO: put your data source class name here */` dans la définition de la classe qui définit le service de données par le type qui hérite de la classe <xref:System.Data.Objects.ObjectContext> et qui correspond au conteneur d'entités du modèle de données, noté à l'étape 2.</span><span class="sxs-lookup"><span data-stu-id="7a163-136">In the code for the data service, replace the comment `/* TODO: put your data source class name here */` in the definition of the class that defines the data service with the type that inherits from the <xref:System.Data.Objects.ObjectContext> class and that is the entity container of the data model, which was noted in step 2.</span></span>  
  
7.  <span data-ttu-id="7a163-137">Dans le code pour le service de données, permettez aux clients autorisés d'accéder aux jeux d'entités exposés par le service de données.</span><span class="sxs-lookup"><span data-stu-id="7a163-137">In the code for the data service, enable authorized clients to access the entity sets that the data service exposes.</span></span> <span data-ttu-id="7a163-138">Pour plus d’informations, consultez [création du Service de données](../../../../docs/framework/data/wcf/creating-the-data-service.md).</span><span class="sxs-lookup"><span data-stu-id="7a163-138">For more information, see [Creating the Data Service](../../../../docs/framework/data/wcf/creating-the-data-service.md).</span></span>  
  
8.  <span data-ttu-id="7a163-139">Pour tester le service de données Northwind.svc à l’aide d’un navigateur Web, suivez les instructions de la rubrique [l’accès au Service à partir d’un navigateur Web](../../../../docs/framework/data/wcf/accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md).</span><span class="sxs-lookup"><span data-stu-id="7a163-139">To test the Northwind.svc data service by using a Web browser, follow the instructions in the topic [Accessing the Service from a Web Browser](../../../../docs/framework/data/wcf/accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a163-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7a163-140">See Also</span></span>  
 [<span data-ttu-id="7a163-141">Définition de WCF Data Services</span><span class="sxs-lookup"><span data-stu-id="7a163-141">Defining WCF Data Services</span></span>](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)  
 [<span data-ttu-id="7a163-142">Fournisseurs de Services de données</span><span class="sxs-lookup"><span data-stu-id="7a163-142">Data Services Providers</span></span>](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)  
 [<span data-ttu-id="7a163-143">Comment : créer un Service de données à l’aide du fournisseur de réflexion</span><span class="sxs-lookup"><span data-stu-id="7a163-143">How to: Create a Data Service Using the Reflection Provider</span></span>](../../../../docs/framework/data/wcf/create-a-data-service-using-rp-wcf-data-services.md)  
 [<span data-ttu-id="7a163-144">Comment : créer un Service de données à l’aide d’un LINQ vers la Source de données SQL</span><span class="sxs-lookup"><span data-stu-id="7a163-144">How to: Create a Data Service Using a LINQ to SQL Data Source</span></span>](../../../../docs/framework/data/wcf/create-a-data-service-using-linq-to-sql-wcf.md)
