---
title: "Procédure : développer un WCF Data Service qui fonctionne sur IIS"
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
helpviewer_keywords:
- WCF Data Services, developing
- WCF Data Services, deploying
- WCF Data Services, hosting
ms.assetid: f6f768c5-4989-49e3-a36f-896ab4ded86e
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 467c572d456bf2beca9f69359d362867aefbe5a1
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-develop-a-wcf-data-service-running-on-iis"></a><span data-ttu-id="d984a-102">Procédure : développer un WCF Data Service qui fonctionne sur IIS</span><span class="sxs-lookup"><span data-stu-id="d984a-102">How to: Develop a WCF Data Service Running on IIS</span></span>
<span data-ttu-id="d984a-103">Cette rubrique montre comment utiliser [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] pour créer un service de données qui est basé sur la base de données Northwind hébergé par une application Web ASP.NET qui s’exécute sur Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="d984a-103">This topic shows how to use [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] to create a data service that is based on the Northwind sample database that is hosted by an ASP.NET Web application that is running on Internet Information Services (IIS).</span></span> <span data-ttu-id="d984a-104">Pour obtenir un exemple montrant comment créer le même service de données Northwind en tant qu’une application Web ASP.NET qui s’exécute sur le serveur de développement ASP.NET, consultez le [démarrage rapide WCF Data Services](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="d984a-104">For an example of how to create the same Northwind data service as an ASP.NET Web application that runs on the ASP.NET Development Server, see the [WCF Data Services quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d984a-105">Pour créer le service de données Northwind, vous avez dû installer l'exemple de base de données Northwind sur l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="d984a-105">To create the Northwind data service, you must have installed the Northwind sample database on the local computer.</span></span> <span data-ttu-id="d984a-106">Pour télécharger cet exemple de base de données, consultez la page de téléchargement, [Exemples de bases de données pour SQL Server](http://go.microsoft.com/fwlink/?linkid=24758).</span><span class="sxs-lookup"><span data-stu-id="d984a-106">To download this sample database, see the download page, [Sample Databases for SQL Server](http://go.microsoft.com/fwlink/?linkid=24758).</span></span>  
  
 <span data-ttu-id="d984a-107">Cette rubrique indique comment créer un service de données à l’aide du fournisseur Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="d984a-107">This topic shows how to create a data service by using the Entity Framework provider.</span></span> <span data-ttu-id="d984a-108">Il existe d'autres fournisseurs de services de données.</span><span class="sxs-lookup"><span data-stu-id="d984a-108">Other data services providers are available.</span></span> <span data-ttu-id="d984a-109">Pour plus d’informations, consultez [des fournisseurs de Services de données](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="d984a-109">For more information, see [Data Services Providers](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="d984a-110">Après avoir créé le service, vous devez explicitement fournir un accès aux ressources du service de données.</span><span class="sxs-lookup"><span data-stu-id="d984a-110">After you create the service, you must explicitly provide access to data service resources.</span></span> <span data-ttu-id="d984a-111">Pour plus d’informations, consultez [Comment : activer l’accès au Service de données](../../../../docs/framework/data/wcf/how-to-enable-access-to-the-data-service-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="d984a-111">For more information, see [How to: Enable Access to the Data Service](../../../../docs/framework/data/wcf/how-to-enable-access-to-the-data-service-wcf-data-services.md).</span></span>  
  
### <a name="to-create-the-aspnet-web-application-that-runs-on-iis"></a><span data-ttu-id="d984a-112">Pour créer l'application Web ASP.NET qui s'exécute sur les services IIS</span><span class="sxs-lookup"><span data-stu-id="d984a-112">To create the ASP.NET Web application that runs on IIS</span></span>  
  
1.  <span data-ttu-id="d984a-113">Dans Visual Studio, sur le **fichier** menu, sélectionnez **nouveau**, puis sélectionnez **projet**.</span><span class="sxs-lookup"><span data-stu-id="d984a-113">In Visual Studio, on the **File** menu, select **New**, and then select **Project**.</span></span>  
  
2.  <span data-ttu-id="d984a-114">Dans le **nouveau projet** boîte de dialogue, sélectionnez Visual Basic ou Visual c# comme langage de programmation.</span><span class="sxs-lookup"><span data-stu-id="d984a-114">In the **New Project** dialog box, select either Visual Basic or Visual C# as the programming language.</span></span>  
  
3.  <span data-ttu-id="d984a-115">Dans le **modèles** volet, sélectionnez **Application Web ASP.NET**.</span><span class="sxs-lookup"><span data-stu-id="d984a-115">In the **Templates** pane, select **ASP.NET Web Application**.</span></span> <span data-ttu-id="d984a-116">Remarque : si vous utilisez Visual Studio Web Developer, vous devrez créer un nouveau site web au lieu d’une nouvelle application Web.</span><span class="sxs-lookup"><span data-stu-id="d984a-116">Note: If you use Visual Studio Web Developer, you must create a new Web site instead of a new Web application.</span></span>  
  
4.  <span data-ttu-id="d984a-117">Type `NorthwindService` en tant que le nom du projet.</span><span class="sxs-lookup"><span data-stu-id="d984a-117">Type `NorthwindService` as the name of the project.</span></span>  
  
5.  <span data-ttu-id="d984a-118">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="d984a-118">Click **OK**.</span></span>  
  
6.  <span data-ttu-id="d984a-119">Sur le **projet** menu, sélectionnez **propriétés NorthwindService**.</span><span class="sxs-lookup"><span data-stu-id="d984a-119">On the **Project** menu, select **NorthwindService Properties**.</span></span>  
  
7.  <span data-ttu-id="d984a-120">Sélectionnez le **Web** onglet, puis sélectionnez **utiliser le serveur Web IIS Local**.</span><span class="sxs-lookup"><span data-stu-id="d984a-120">Select the **Web** tab, and then select **Use Local IIS Web Server**.</span></span>  
  
8.  <span data-ttu-id="d984a-121">Cliquez sur **créer un répertoire virtuel** puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="d984a-121">Click **Create Virtual Directory** and then click **OK**.</span></span>  
  
9. <span data-ttu-id="d984a-122">À partir de l'invite de commandes avec des privilèges d'administrateur, exécutez une des commandes suivantes (en fonction du système d'exploitation) :</span><span class="sxs-lookup"><span data-stu-id="d984a-122">From the command prompt with administrator privileges, execute one of the following commands (depending on the operating system):</span></span>  
  
    -   <span data-ttu-id="d984a-123">Systèmes 32 bits :</span><span class="sxs-lookup"><span data-stu-id="d984a-123">32-bit systems:</span></span>  
  
        ```console
        "%windir%\Microsoft.NET\Framework\v3.0\Windows Communication Foundation\ServiceModelReg.exe" -i  
        ```  
  
    -   <span data-ttu-id="d984a-124">Systèmes 64 bits :</span><span class="sxs-lookup"><span data-stu-id="d984a-124">64-bit systems:</span></span>  
  
        ```console
        "%windir%\Microsoft.NET\Framework64\v3.0\Windows Communication Foundation\ServiceModelReg.exe" -i  
        ```  
  
     <span data-ttu-id="d984a-125">Cela permet de vérifier que Windows Communication Foundation (WCF) est inscrit sur l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="d984a-125">This makes sure that Windows Communication Foundation (WCF) is registered on the computer.</span></span>  
  
10. <span data-ttu-id="d984a-126">À partir de l'invite de commandes avec des privilèges d'administrateur, exécutez une des commandes suivantes (en fonction du système d'exploitation) :</span><span class="sxs-lookup"><span data-stu-id="d984a-126">From the command prompt with administrator privileges, execute one of the following commands (depending on the operating system):</span></span>  
  
    -   <span data-ttu-id="d984a-127">Systèmes 32 bits :</span><span class="sxs-lookup"><span data-stu-id="d984a-127">32-bit systems:</span></span>  
  
        ```console
        "%windir%\Microsoft.NET\Framework\v4.0.30319\aspnet_regiis.exe" -i -enable  
        ```  
  
    -   <span data-ttu-id="d984a-128">Systèmes 64 bits :</span><span class="sxs-lookup"><span data-stu-id="d984a-128">64-bit systems:</span></span>  
  
        ```console
        "%windir%\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe" -i -enable  
        ```  
  
     <span data-ttu-id="d984a-129">Cela permet de s'assurer qu'IIS s'exécute correctement après que WCF a été installé sur l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="d984a-129">This makes sure that IIS runs correctly after WCF has been installed on the computer.</span></span> <span data-ttu-id="d984a-130">Vous devrez peut-être redémarrer IIS.</span><span class="sxs-lookup"><span data-stu-id="d984a-130">You might have to also restart IIS.</span></span>  
  
11. <span data-ttu-id="d984a-131">Lorsque l'application ASP.NET s'exécute sur IIS7, vous devez aussi effectuer les étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="d984a-131">When the ASP.NET application runs on IIS7, you must also perform the following steps:</span></span>  
  
    1.  <span data-ttu-id="d984a-132">Ouvrez le Gestionnaire des services Internet et accédez à l’application PhotoService sous **Site Web par défaut**.</span><span class="sxs-lookup"><span data-stu-id="d984a-132">Open IIS Manager and navigate to the PhotoService application under **Default Web Site**.</span></span>  
  
    2.  <span data-ttu-id="d984a-133">Dans **affichage des fonctionnalités**, double-cliquez sur **authentification**.</span><span class="sxs-lookup"><span data-stu-id="d984a-133">In **Features View**, double-click **Authentication**.</span></span>  
  
    3.  <span data-ttu-id="d984a-134">Sur le **authentification** page, sélectionnez **l’authentification anonyme**.</span><span class="sxs-lookup"><span data-stu-id="d984a-134">On the **Authentication** page, select **Anonymous Authentication**.</span></span>  
  
    4.  <span data-ttu-id="d984a-135">Dans le **Actions** volet, cliquez sur **modifier** pour définir la sécurité principal sous lequel les utilisateurs anonymes se connecte au site.</span><span class="sxs-lookup"><span data-stu-id="d984a-135">In the **Actions** pane, click **Edit** to set the security principal under which anonymous users will connect to the site.</span></span>  
  
    5.  <span data-ttu-id="d984a-136">Dans le **modifier les informations d’identification d’authentification anonyme** boîte de dialogue, sélectionnez **identité du pool d’applications**.</span><span class="sxs-lookup"><span data-stu-id="d984a-136">In the **Edit Anonymous Authentication Credentials** dialog box, select **Application pool identity**.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="d984a-137">Lorsque vous utilisez le compte de service réseau, vous accordez aux utilisateurs anonymes l'accès à tout le réseau interne associé à ce compte.</span><span class="sxs-lookup"><span data-stu-id="d984a-137">When you use the Network Service account, you grant anonymous users all the internal network access associated with that account.</span></span>  
  
12. <span data-ttu-id="d984a-138">En utilisant SQL Server Management Studio, l'utilitaire sqlcmd.exe ou l'Éditeur Transact-SQL dans Visual Studio, exécutez la commande Transact-SQL suivante sur l'instance SQL Server à laquelle la base de données Northwind est attachée :</span><span class="sxs-lookup"><span data-stu-id="d984a-138">By using SQL Server Management Studio, the sqlcmd.exe utility, or the Transact-SQL Editor in Visual Studio, execute the following Transact-SQL command against the instance of SQL Server that has the Northwind database attached:</span></span>  
  
    ```sql  
    CREATE LOGIN [NT AUTHORITY\NETWORK SERVICE] FROM WINDOWS;  
    GO   
    ```  
  
     <span data-ttu-id="d984a-139">Cela crée une connexion dans l'instance SQL Server pour le compte Windows utilisé pour exécuter IIS.</span><span class="sxs-lookup"><span data-stu-id="d984a-139">This creates a login in the SQL Server instance for the Windows account used to run IIS.</span></span> <span data-ttu-id="d984a-140">Cela permet à IIS de se connecter à l'instance de SQL Server.</span><span class="sxs-lookup"><span data-stu-id="d984a-140">This enables IIS to connect to the SQL Server instance.</span></span>  
  
13. <span data-ttu-id="d984a-141">Avec la base de données Northwind attachée, exécutez les commandes Transact-SQL suivantes :</span><span class="sxs-lookup"><span data-stu-id="d984a-141">With the Northwind database attached, execute the following Transact-SQL commands:</span></span>  
  
    ```sql  
    USE Northwind  
    GO  
    CREATE USER [NT AUTHORITY\NETWORK SERVICE]   
    FOR LOGIN [NT AUTHORITY\NETWORK SERVICE] WITH DEFAULT_SCHEMA=[dbo];  
    GO  
    ALTER LOGIN [NT AUTHORITY\NETWORK SERVICE]   
    WITH DEFAULT_DATABASE=[Northwind];   
    GO  
    EXEC sp_addrolemember 'db_datareader', 'NT AUTHORITY\NETWORK SERVICE'  
    GO  
    EXEC sp_addrolemember 'db_datawriter', 'NT AUTHORITY\NETWORK SERVICE'  
    GO   
    ```  
  
     <span data-ttu-id="d984a-142">Cela accorde des droits à la nouvelle connexion et permet à IIS de lire et d'écrire les données dans la base de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="d984a-142">This grants rights to the new login, which enables IIS to read data from and write data to the Northwind database.</span></span>  
  
### <a name="to-define-the-data-model"></a><span data-ttu-id="d984a-143">Pour définir le modèle de données</span><span class="sxs-lookup"><span data-stu-id="d984a-143">To define the data model</span></span>  
  
1.  <span data-ttu-id="d984a-144">Dans **l’Explorateur de solutions**, cliquez sur le nom du projet ASP.NET, puis cliquez sur **ajouter un nouvel élément.**</span><span class="sxs-lookup"><span data-stu-id="d984a-144">In **Solution Explorer**, right-click the name of the ASP.NET project, and then click **Add New Item.**</span></span>  
  
2.  <span data-ttu-id="d984a-145">Dans le **ajouter un nouvel élément** boîte de dialogue, sélectionnez **ADO.NET Entity Data Model**.</span><span class="sxs-lookup"><span data-stu-id="d984a-145">In the **Add New Item** dialog box, select **ADO.NET Entity Data Model**.</span></span>  
  
3.  <span data-ttu-id="d984a-146">Tapez le nom du modèle de données `Northwind.edmx`.</span><span class="sxs-lookup"><span data-stu-id="d984a-146">For the name of the data model, type `Northwind.edmx`.</span></span>  
  
4.  <span data-ttu-id="d984a-147">Dans l’Assistant Entity Data Model, sélectionnez **générer à partir de la base de données**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="d984a-147">In the Entity Data Model Wizard, select **Generate from Database**, and then click **Next**.</span></span>  
  
5.  <span data-ttu-id="d984a-148">Connecter le modèle de données à la base de données en effectuant l’une des étapes suivantes, puis cliquez sur **suivant**:</span><span class="sxs-lookup"><span data-stu-id="d984a-148">Connect the data model to the database by doing one of the following steps, and then click **Next**:</span></span>  
  
    -   <span data-ttu-id="d984a-149">Si vous n’avez pas d’une connexion de base de données déjà configurée, cliquez sur **nouvelle connexion** et créer une nouvelle connexion.</span><span class="sxs-lookup"><span data-stu-id="d984a-149">If you do not have a database connection already configured, click **New Connection** and create a new connection.</span></span> <span data-ttu-id="d984a-150">Pour plus d’informations, consultez [Comment : créer des connexions aux bases de données SQL Server](http://go.microsoft.com/fwlink/?LinkId=123631).</span><span class="sxs-lookup"><span data-stu-id="d984a-150">For more information, see [How to: Create Connections to SQL Server Databases](http://go.microsoft.com/fwlink/?LinkId=123631).</span></span> <span data-ttu-id="d984a-151">Cette instance [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] doit avoir l'exemple de base de données Northwind joint.</span><span class="sxs-lookup"><span data-stu-id="d984a-151">This [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] instance must have the Northwind sample database attached.</span></span>  
  
         <span data-ttu-id="d984a-152">\- ou -</span><span class="sxs-lookup"><span data-stu-id="d984a-152">\- or -</span></span>  
  
    -   <span data-ttu-id="d984a-153">Si vous avez une connexion de base de données déjà configurée pour vous connecter à la base de données Northwind, sélectionnez cette connexion dans la liste des connexions.</span><span class="sxs-lookup"><span data-stu-id="d984a-153">If you have a database connection already configured to connect to the Northwind database, select that connection from the list of connections.</span></span>  
  
6.  <span data-ttu-id="d984a-154">Dans la page finale de l'Assistant, activez les cases à cocher pour toutes les tables de la base de données puis désactivez les cases pour les vues et les procédures stockées.</span><span class="sxs-lookup"><span data-stu-id="d984a-154">On the final page of the wizard, select the check boxes for all tables in the database, and clear the check boxes for views and stored procedures.</span></span>  
  
7.  <span data-ttu-id="d984a-155">Cliquez sur **Terminer** pour fermer l’Assistant.</span><span class="sxs-lookup"><span data-stu-id="d984a-155">Click **Finish** to close the wizard.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d984a-156">Ce modèle de données généré expose les propriétés de clé étrangère sur les types d'entité.</span><span class="sxs-lookup"><span data-stu-id="d984a-156">This generated data model exposes foreign key properties on entity types.</span></span> <span data-ttu-id="d984a-157">Les modèles de données créés à l'aide de Visual Studio 2008 n'incluent pas ces propriétés de clé étrangère.</span><span class="sxs-lookup"><span data-stu-id="d984a-157">Data models created using Visual Studio 2008 do not include these foreign key properties.</span></span> <span data-ttu-id="d984a-158">Vous devez donc mettre à jour les classes de service de données clientes de toutes les applications clientes créées pour accéder au service de données Northwind créé à l'aide de Visual Studio 2008 avant d'essayer d'accéder à cette version du service de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="d984a-158">Because of this, you must update the client data service classes of any client applications that were created to access the Northwind data service that was created using Visual Studio 2008 before attempting to access this version of the Northwind data service.</span></span>  
  
### <a name="to-create-the-data-service"></a><span data-ttu-id="d984a-159">Pour créer le service de données</span><span class="sxs-lookup"><span data-stu-id="d984a-159">To create the data service</span></span>  
  
1.  <span data-ttu-id="d984a-160">Dans **l’Explorateur de solutions**, cliquez sur le nom de votre projet ASP.NET, puis cliquez sur **ajouter un nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="d984a-160">In **Solution Explorer**, right-click the name of your ASP.NET project, and then click **Add New Item**.</span></span>  
  
2.  <span data-ttu-id="d984a-161">Dans le **ajouter un nouvel élément** boîte de dialogue, sélectionnez **Service de données ADO.NET**.</span><span class="sxs-lookup"><span data-stu-id="d984a-161">In the **Add New Item** dialog box, select **ADO.NET Data Service**.</span></span>  
  
3.  <span data-ttu-id="d984a-162">Tapez le nom du service `Northwind`.</span><span class="sxs-lookup"><span data-stu-id="d984a-162">For the name of the service, type `Northwind`.</span></span>  
  
     <span data-ttu-id="d984a-163">Visual Studio crée le balisage XML et des fichiers de code pour le nouveau service.</span><span class="sxs-lookup"><span data-stu-id="d984a-163">Visual Studio creates the XML markup and code files for the new service.</span></span> <span data-ttu-id="d984a-164">La fenêtre de l'éditeur de code s'ouvre par défaut.</span><span class="sxs-lookup"><span data-stu-id="d984a-164">By default, the code-editor window opens.</span></span> <span data-ttu-id="d984a-165">Dans **l’Explorateur de solutions**, le service aura le nom, Northwind, avec l’extension. svc.cs ou. svc.vb.</span><span class="sxs-lookup"><span data-stu-id="d984a-165">In **Solution Explorer**, the service will have the name, Northwind, with the extension .svc.cs or .svc.vb.</span></span>  
  
4.  <span data-ttu-id="d984a-166">Dans le code du service de données, remplacez le commentaire `/* TODO: put your data source class name here */` dans la définition de la classe qui définit le service de données par le type qui est le conteneur d'entités du modèle de données, dans ce cas `NorthwindEntities`.</span><span class="sxs-lookup"><span data-stu-id="d984a-166">In the code for the data service, replace the comment `/* TODO: put your data source class name here */` in the definition of the class that defines the data service with the type that is the entity container of the data model, which in this case is `NorthwindEntities`.</span></span> <span data-ttu-id="d984a-167">La définition de classe doit ressembler aux éléments suivants:</span><span class="sxs-lookup"><span data-stu-id="d984a-167">The class definition should look this the following:</span></span>  
  
     [!code-csharp[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart service/cs/northwind.svc.cs#servicedefinition)]
     [!code-vb[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart service/vb/northwind.svc.vb#servicedefinition)]  
  
## <a name="see-also"></a><span data-ttu-id="d984a-168">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d984a-168">See Also</span></span>  
 [<span data-ttu-id="d984a-169">Exposition de vos données en tant que Service</span><span class="sxs-lookup"><span data-stu-id="d984a-169">Exposing Your Data as a Service</span></span>](../../../../docs/framework/data/wcf/exposing-your-data-as-a-service-wcf-data-services.md)
