---
title: "Création du service de données"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 34d1d971-5e18-4c22-9bf6-d3612e27ea59
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 57e305fd8b03e8d46c1fdcb7dd551f32062a1009
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="creating-the-data-service"></a><span data-ttu-id="ab50b-102">Création du service de données</span><span class="sxs-lookup"><span data-stu-id="ab50b-102">Creating the Data Service</span></span>
<span data-ttu-id="ab50b-103">Dans cette tâche, vous allez créer un exemple de service de données qui utilise [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] pour exposer un [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] flux basé sur la base de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="ab50b-103">In this task, you will create a sample data service that uses [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] to expose an [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] feed that is based on the Northwind sample database.</span></span> <span data-ttu-id="ab50b-104">La tâche implique les étapes fondamentales suivantes :</span><span class="sxs-lookup"><span data-stu-id="ab50b-104">The task involves the following basic steps:</span></span>  
  
1.  <span data-ttu-id="ab50b-105">Créez une application Web [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ab50b-105">Create an [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web application.</span></span>  
  
2.  <span data-ttu-id="ab50b-106">Définissez le modèle de données à l'aide des outils [!INCLUDE[adonet_edm](../../../../includes/adonet-edm-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ab50b-106">Define the data model by using the [!INCLUDE[adonet_edm](../../../../includes/adonet-edm-md.md)] tools.</span></span>  
  
3.  <span data-ttu-id="ab50b-107">Ajoutez le service de données à l'application Web.</span><span class="sxs-lookup"><span data-stu-id="ab50b-107">Add the data service to the Web application.</span></span>  
  
4.  <span data-ttu-id="ab50b-108">Activez l'accès au service de données.</span><span class="sxs-lookup"><span data-stu-id="ab50b-108">Enable access to the data service.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ab50b-109">L'application Web [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] que vous créez lorsque vous effectuez cette tâche s'exécute sur le serveur de développement [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] fourni par [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ab50b-109">The [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web application that you create when you complete this task runs on the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Development Server provided by [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)].</span></span> <span data-ttu-id="ab50b-110">Le serveur de développement [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] prend uniquement en charge l'accès à partir de l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="ab50b-110">[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Development Server only supports access from the local computer.</span></span> <span data-ttu-id="ab50b-111">Pour simplifier les opérations de test et de dépannage du service de données pendant le développement, envisagez d'exécuter l'application qui héberge le service de données à l'aide des Services IIS (Internet Information Services).</span><span class="sxs-lookup"><span data-stu-id="ab50b-111">To also make it easier to test and troubleshoot the data service during development, consider running the application that hosts the data service by using Internet Information Services (IIS).</span></span> <span data-ttu-id="ab50b-112">Pour plus d'informations, consultez [How to: Develop a WCF Data Service Running on IIS](../../../../docs/framework/data/wcf/how-to-develop-a-wcf-data-service-running-on-iis.md).</span><span class="sxs-lookup"><span data-stu-id="ab50b-112">For more information, see [How to: Develop a WCF Data Service Running on IIS](../../../../docs/framework/data/wcf/how-to-develop-a-wcf-data-service-running-on-iis.md).</span></span>  
  
### <a name="to-create-the-aspnet-web-application"></a><span data-ttu-id="ab50b-113">Pour créer l'application Web ASP.NET</span><span class="sxs-lookup"><span data-stu-id="ab50b-113">To create the ASP.NET Web application</span></span>  
  
1.  <span data-ttu-id="ab50b-114">Dans [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)], dans le **fichier** menu, sélectionnez **nouveau**, puis sélectionnez **projet**.</span><span class="sxs-lookup"><span data-stu-id="ab50b-114">In [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)], on the **File** menu, select **New**, and then select **Project**.</span></span>  
  
2.  <span data-ttu-id="ab50b-115">Dans le **nouveau projet** boîte de dialogue, sous [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] ou [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] sélectionner le **Web** modèle, puis sélectionnez **Application Web ASP.NET**.</span><span class="sxs-lookup"><span data-stu-id="ab50b-115">In the **New Project** dialog box, under either [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] or [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] select the **Web** template, and then select **ASP.NET Web Application**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ab50b-116">Si vous utilisez [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] Web Developer, vous devrez créer un nouveau site Web au lieu d'une nouvelle application Web.</span><span class="sxs-lookup"><span data-stu-id="ab50b-116">If you use [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] Web Developer, you must create a new Web site instead of a new Web application.</span></span>  
  
3.  <span data-ttu-id="ab50b-117">Type `NorthwindService` en tant que le nom du projet.</span><span class="sxs-lookup"><span data-stu-id="ab50b-117">Type `NorthwindService` as the name of the project.</span></span>  
  
4.  <span data-ttu-id="ab50b-118">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="ab50b-118">Click **OK**.</span></span>  
  
5.  <span data-ttu-id="ab50b-119">(Facultatif) Spécifiez un numéro de port spécifique pour votre application Web.</span><span class="sxs-lookup"><span data-stu-id="ab50b-119">(Optional) Specify a specific port number for your Web application.</span></span> <span data-ttu-id="ab50b-120">Remarque : le numéro de port `12345` est utilisé pour le reste du démarrage rapide.</span><span class="sxs-lookup"><span data-stu-id="ab50b-120">Note: the port number `12345` is used in the rest of the quickstart.</span></span>  
  
    1.  <span data-ttu-id="ab50b-121">Dans **l’Explorateur de solutions**, cliquez sur le nom de la [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] de projet que vous venez créé, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="ab50b-121">In **Solution Explorer**, right-click the name of the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] project that you just created, and then click **Properties**.</span></span>  
  
    2.  <span data-ttu-id="ab50b-122">Sélectionnez le **Web** onglet et définir la valeur de la **port spécifique** zone de texte `12345`.</span><span class="sxs-lookup"><span data-stu-id="ab50b-122">Select the **Web** tab, and set the value of the **Specific port** text box to `12345`.</span></span>  
  
### <a name="to-define-the-data-model"></a><span data-ttu-id="ab50b-123">Pour définir le modèle de données</span><span class="sxs-lookup"><span data-stu-id="ab50b-123">To define the data model</span></span>  
  
1.  <span data-ttu-id="ab50b-124">Dans **l’Explorateur de solutions**, cliquez sur le nom de la [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] de projet, puis cliquez sur **ajouter un nouvel élément.**</span><span class="sxs-lookup"><span data-stu-id="ab50b-124">In **Solution Explorer**, right-click the name of the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] project, and then click **Add New Item.**</span></span>  
  
2.  <span data-ttu-id="ab50b-125">Dans le **ajouter un nouvel élément** boîte de dialogue, cliquez sur le **données** modèle, puis sélectionnez **ADO.NET Entity Data Model**.</span><span class="sxs-lookup"><span data-stu-id="ab50b-125">In the **Add New Item** dialog box, click the **Data** template and then select **ADO.NET Entity Data Model**.</span></span>  
  
3.  <span data-ttu-id="ab50b-126">Tapez le nom du modèle de données `Northwind.edmx`.</span><span class="sxs-lookup"><span data-stu-id="ab50b-126">For the name of the data model, type `Northwind.edmx`.</span></span>  
  
4.  <span data-ttu-id="ab50b-127">Dans le [!INCLUDE[adonet_edm](../../../../includes/adonet-edm-md.md)] Assistant, sélectionnez **générer à partir de la base de données**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="ab50b-127">In the [!INCLUDE[adonet_edm](../../../../includes/adonet-edm-md.md)] Wizard, select **Generate from Database**, and then click **Next**.</span></span>  
  
5.  <span data-ttu-id="ab50b-128">Connecter le modèle de données à la base de données en effectuant l’une des étapes suivantes, puis cliquez sur **suivant**:</span><span class="sxs-lookup"><span data-stu-id="ab50b-128">Connect the data model to the database by doing one of the following steps, and then click **Next**:</span></span>  
  
    -   <span data-ttu-id="ab50b-129">Si vous n’avez pas d’une connexion de base de données déjà configurée, cliquez sur **nouvelle connexion** et créer une nouvelle connexion.</span><span class="sxs-lookup"><span data-stu-id="ab50b-129">If you do not have a database connection already configured, click **New Connection** and create a new connection.</span></span> <span data-ttu-id="ab50b-130">Pour plus d’informations, consultez [Comment : créer des connexions aux bases de données SQL Server](http://go.microsoft.com/fwlink/?LinkId=123631).</span><span class="sxs-lookup"><span data-stu-id="ab50b-130">For more information, see [How to: Create Connections to SQL Server Databases](http://go.microsoft.com/fwlink/?LinkId=123631).</span></span> <span data-ttu-id="ab50b-131">Cette instance [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] doit avoir l'exemple de base de données Northwind joint.</span><span class="sxs-lookup"><span data-stu-id="ab50b-131">This [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] instance must have the Northwind sample database attached.</span></span>  
  
         <span data-ttu-id="ab50b-132">\- ou -</span><span class="sxs-lookup"><span data-stu-id="ab50b-132">\- or -</span></span>  
  
    -   <span data-ttu-id="ab50b-133">Si vous avez une connexion de base de données déjà configurée pour vous connecter à la base de données Northwind, sélectionnez cette connexion dans la liste des connexions.</span><span class="sxs-lookup"><span data-stu-id="ab50b-133">If you have a database connection already configured to connect to the Northwind database, select that connection from the list of connections.</span></span>  
  
6.  <span data-ttu-id="ab50b-134">Dans la page finale de l'Assistant, activez les cases à cocher pour toutes les tables de la base de données puis désactivez les cases pour les vues et les procédures stockées.</span><span class="sxs-lookup"><span data-stu-id="ab50b-134">On the final page of the wizard, select the check boxes for all tables in the database, and clear the check boxes for views and stored procedures.</span></span>  
  
7.  <span data-ttu-id="ab50b-135">Cliquez sur **Terminer** pour fermer l’Assistant.</span><span class="sxs-lookup"><span data-stu-id="ab50b-135">Click **Finish** to close the wizard.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ab50b-136">Ce modèle de données généré expose les propriétés de clé étrangère sur les types d'entité.</span><span class="sxs-lookup"><span data-stu-id="ab50b-136">This generated data model exposes foreign key properties on entity types.</span></span> <span data-ttu-id="ab50b-137">Les modèles de données créés à l'aide de [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] 2008 n'incluent pas ces propriétés de clé étrangère.</span><span class="sxs-lookup"><span data-stu-id="ab50b-137">Data models created using [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] 2008 do not include these foreign key properties.</span></span> <span data-ttu-id="ab50b-138">Vous devez donc mettre à jour les classes de service de données clientes de toutes les applications clientes créées pour accéder au service de données Northwind créé à l'aide de [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] 2008 avant d'essayer d'accéder à cette version du service de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="ab50b-138">Because of this, you must update the client data service classes of any client applications that were created to access the Northwind data service that was created using [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] 2008 before attempting to access this version of the Northwind data service.</span></span>  
  
### <a name="to-create-the-data-service"></a><span data-ttu-id="ab50b-139">Pour créer le service de données</span><span class="sxs-lookup"><span data-stu-id="ab50b-139">To create the data service</span></span>  
  
1.  <span data-ttu-id="ab50b-140">Dans **l’Explorateur de solutions**, cliquez sur le nom de votre [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] de projet, puis cliquez sur **ajouter un nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="ab50b-140">In **Solution Explorer**, right-click the name of your [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] project, and then click **Add New Item**.</span></span>  
  
2.  <span data-ttu-id="ab50b-141">Dans le **ajouter un nouvel élément** boîte de dialogue, sélectionnez **Service de données WCF**.</span><span class="sxs-lookup"><span data-stu-id="ab50b-141">In the **Add New Item** dialog box, select **WCF Data Service**.</span></span>  
  
3.  <span data-ttu-id="ab50b-142">Tapez le nom du service `Northwind`.</span><span class="sxs-lookup"><span data-stu-id="ab50b-142">For the name of the service, type `Northwind`.</span></span>  
  
     [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)]<span data-ttu-id="ab50b-143">Visual Studio crée le balisage XML et des fichiers de code pour le nouveau service.</span><span class="sxs-lookup"><span data-stu-id="ab50b-143">Visual Studio creates the XML markup and code files for the new service.</span></span> <span data-ttu-id="ab50b-144">La fenêtre de l'éditeur de code s'ouvre par défaut.</span><span class="sxs-lookup"><span data-stu-id="ab50b-144">By default, the code-editor window opens.</span></span> <span data-ttu-id="ab50b-145">Dans **l’Explorateur de solutions**, le service aura le nom, Northwind, avec l’extension. svc.cs ou. svc.vb.</span><span class="sxs-lookup"><span data-stu-id="ab50b-145">In **Solution Explorer**, the service will have the name, Northwind, with the extension .svc.cs or .svc.vb.</span></span>  
  
4.  <span data-ttu-id="ab50b-146">Dans le code du service de données, remplacez le commentaire `/* TODO: put your data source class name here */` dans la définition de la classe qui définit le service de données par le type qui est le conteneur d'entités du modèle de données, dans ce cas `NorthwindEntities`.</span><span class="sxs-lookup"><span data-stu-id="ab50b-146">In the code for the data service, replace the comment `/* TODO: put your data source class name here */` in the definition of the class that defines the data service with the type that is the entity container of the data model, which in this case is `NorthwindEntities`.</span></span> <span data-ttu-id="ab50b-147">La définition de classe doit ressembler aux éléments suivants:</span><span class="sxs-lookup"><span data-stu-id="ab50b-147">The class definition should look this the following:</span></span>  
  
     [!code-csharp[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart service/cs/northwind.svc.cs#servicedefinition)]
     [!code-vb[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart service/vb/northwind.svc.vb#servicedefinition)]  
  
### <a name="to-enable-access-to-data-service-resources"></a><span data-ttu-id="ab50b-148">Pour activer l'accès aux ressources du service de données</span><span class="sxs-lookup"><span data-stu-id="ab50b-148">To enable access to data service resources</span></span>  
  
1.  <span data-ttu-id="ab50b-149">Dans le code du service de données, remplacez le code d'espace réservé dans la fonction `InitializeService` par le code suivant :</span><span class="sxs-lookup"><span data-stu-id="ab50b-149">In the code for the data service, replace the placeholder code in the `InitializeService` function with the following:</span></span>  
  
     [!code-csharp[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart service/cs/northwind.svc.cs#allreadconfig)]
     [!code-vb[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart service/vb/northwind.svc.vb#allreadconfig)]  
  
     <span data-ttu-id="ab50b-150">Cela permet aux clients autorisés d'accéder aux ressources en lecture et en écriture pour les jeux d'entités spécifiés.</span><span class="sxs-lookup"><span data-stu-id="ab50b-150">This enables authorized clients to have read and write access to resources for the specified entity sets.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ab50b-151">Tout client qui peut accéder à l'application [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] peut également accéder aux ressources exposées par le service de données.</span><span class="sxs-lookup"><span data-stu-id="ab50b-151">Any client that can access the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] application can also access the resources exposed by the data service.</span></span> <span data-ttu-id="ab50b-152">Dans un service de données de production, pour empêcher l'accès non autorisé aux ressources, vous devez également sécuriser l'application elle-même.</span><span class="sxs-lookup"><span data-stu-id="ab50b-152">In a production data service, to prevent unauthorized access to resources you should also secure the application itself.</span></span> <span data-ttu-id="ab50b-153">Pour plus d'informations, consultez [Securing WCF Data Services](../../../../docs/framework/data/wcf/securing-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="ab50b-153">For more information, see [Securing WCF Data Services](../../../../docs/framework/data/wcf/securing-wcf-data-services.md).</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="ab50b-154">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="ab50b-154">Next Steps</span></span>  
 <span data-ttu-id="ab50b-155">Vous avez créé un nouveau service de données qui expose un [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] flux basé sur la base de données Northwind et que vous avez activé l’accès au flux pour les clients qui ont des autorisations sur le [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] application Web.</span><span class="sxs-lookup"><span data-stu-id="ab50b-155">You have successfully created a new data service that exposes an [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed that is based on the Northwind sample database, and you have enabled access to the feed for clients that have permissions on the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web application.</span></span> <span data-ttu-id="ab50b-156">Vous démarrerez ensuite le service de données à partir de [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] et vous allez accéder à la [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] flux en soumettant des demandes HTTP GET via un navigateur Web :</span><span class="sxs-lookup"><span data-stu-id="ab50b-156">Next, you will start the data service from [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] and you will access the [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed by submitting HTTP GET requests through a Web browser:</span></span>  
  
 [<span data-ttu-id="ab50b-157">Accès au service à partir d’un navigateur web</span><span class="sxs-lookup"><span data-stu-id="ab50b-157">Accessing the Service from a Web Browser</span></span>](../../../../docs/framework/data/wcf/accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md)  
  
## <a name="see-also"></a><span data-ttu-id="ab50b-158">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ab50b-158">See Also</span></span>  
 [<span data-ttu-id="ab50b-159">Outils ADO.NET Entity Data Model</span><span class="sxs-lookup"><span data-stu-id="ab50b-159">ADO.NET Entity Data Model  Tools</span></span>](http://msdn.microsoft.com/en-us/91076853-0881-421b-837a-f582f36be527)
