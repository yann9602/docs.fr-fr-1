---
title: "Comment : créer un service de données à l'aide d'un LINQ vers la source de données SQL (services de données WCF)"
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
- WCF Data Services, LINQ to SQL
- WCF Data Services, providers
ms.assetid: 3b01c2fd-8c6e-4bf5-b38f-9e61bdc3c328
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a44498381bc33b6bd418003fbd28fd2fcfca17b6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-data-service-using-a-linq-to-sql-data-source-wcf-data-services"></a><span data-ttu-id="6ae89-102">Comment : créer un service de données à l'aide d'un LINQ vers la source de données SQL (services de données WCF)</span><span class="sxs-lookup"><span data-stu-id="6ae89-102">How to: Create a Data Service Using a LINQ to SQL Data Source (WCF Data Services)</span></span>
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]<span data-ttu-id="6ae89-103"> expose les données d'entité comme un service de données.</span><span class="sxs-lookup"><span data-stu-id="6ae89-103"> exposes entity data as a data service.</span></span> <span data-ttu-id="6ae89-104">Le fournisseur de réflexion vous permet de définir un modèle de données qui est basé sur toute classe qui expose des membres qui retournent un <xref:System.Linq.IQueryable%601> mise en œuvre.</span><span class="sxs-lookup"><span data-stu-id="6ae89-104">The reflection provider enables you to define a data model that is based on any class that exposes members that return an <xref:System.Linq.IQueryable%601> implementation.</span></span> <span data-ttu-id="6ae89-105">Pour pouvoir effectuer des mises à jour des données dans la source de données, ces classes doivent également implémenter l'interface <xref:System.Data.Services.IUpdatable>.</span><span class="sxs-lookup"><span data-stu-id="6ae89-105">To be able to make updates to data in the data source, these classes must also implement the <xref:System.Data.Services.IUpdatable> interface.</span></span> <span data-ttu-id="6ae89-106">Pour plus d’informations, consultez [des fournisseurs de Services de données](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="6ae89-106">For more information, see [Data Services Providers](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md).</span></span> <span data-ttu-id="6ae89-107">Cette rubrique vous montre comment créer des classes LINQ to SQL qui accèdent à l'exemple de base de données Northwind à l'aide du fournisseur de réflexion, et comment créer le service de données basé sur ces classes de données.</span><span class="sxs-lookup"><span data-stu-id="6ae89-107">This topic shows you how to create LINQ to SQL classes that access the Northwind sample database by using the reflection provider, as well as how to create the data service that is based on these data classes.</span></span>  
  
### <a name="to-add-linq-to-sql-classes-to-a-project"></a><span data-ttu-id="6ae89-108">Pour ajouter des classes LINQ to SQL à un projet.</span><span class="sxs-lookup"><span data-stu-id="6ae89-108">To add LINQ to SQL classes to a project</span></span>  
  
1.  <span data-ttu-id="6ae89-109">À partir d’une application Visual Basic ou c#, sur le **projet** menu, cliquez sur **ajouter un nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="6ae89-109">From within a Visual Basic or C# application, on the **Project** menu, click **Add New Item**.</span></span>  
  
2.  <span data-ttu-id="6ae89-110">Cliquez sur le **Classes LINQ to SQL** modèle.</span><span class="sxs-lookup"><span data-stu-id="6ae89-110">Click the **LINQ to SQL Classes** template.</span></span>  
  
3.  <span data-ttu-id="6ae89-111">Remplacez le nom par **Northwind.dbml**.</span><span class="sxs-lookup"><span data-stu-id="6ae89-111">Change the name to **Northwind.dbml**.</span></span>  
  
4.  <span data-ttu-id="6ae89-112">Cliquez sur **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="6ae89-112">Click **Add**.</span></span>  
  
     <span data-ttu-id="6ae89-113">Le fichier Northwind.dbml est ajouté au projet et le Concepteur Objet/Relationnel (Concepteur O/R) s'ouvre.</span><span class="sxs-lookup"><span data-stu-id="6ae89-113">The Northwind.dbml file is added to the project and the Object Relational Designer (O/R Designer) opens.</span></span>  
  
5.  <span data-ttu-id="6ae89-114">Dans **Server**/**l’Explorateur de base de données**, sous Northwind, développez **Tables** et faites glisser le `Customers` table sur le Concepteur Objet/Relationnel (O/R Concepteur).</span><span class="sxs-lookup"><span data-stu-id="6ae89-114">In **Server**/**Database Explorer**, under Northwind, expand **Tables** and drag the `Customers` table onto the Object Relational Designer (O/R Designer).</span></span>  
  
     <span data-ttu-id="6ae89-115">Une classe d'entité `Customer` est créée et apparaît dans l'aire de conception.</span><span class="sxs-lookup"><span data-stu-id="6ae89-115">A `Customer` entity class is created and appears on the design surface.</span></span>  
  
6.  <span data-ttu-id="6ae89-116">Répétez l'étape 6 pour les tables `Orders`, `Order_Details` et `Products`.</span><span class="sxs-lookup"><span data-stu-id="6ae89-116">Repeat step 6 for the `Orders`, `Order_Details`, and `Products` tables.</span></span>  
  
7.  <span data-ttu-id="6ae89-117">Cliquez sur le nouveau fichier .dbml qui représente le LINQ de classes SQL et cliquez sur **afficher le Code**.</span><span class="sxs-lookup"><span data-stu-id="6ae89-117">Right-click the new .dbml file that represents the LINQ to SQL classes and click **View Code**.</span></span>  
  
     <span data-ttu-id="6ae89-118">Cela crée une nouvelle page code-behind nommée Northwind.cs qui contient une définition de classe partielle pour la classe qui hérite de la classe <xref:System.Data.Linq.DataContext>, dans ce cas `NorthwindDataContext`.</span><span class="sxs-lookup"><span data-stu-id="6ae89-118">This creates a new code-behind page named Northwind.cs that contains a partial class definition for the class that inherits from the <xref:System.Data.Linq.DataContext> class, which in this case is `NorthwindDataContext`.</span></span>  
  
8.  <span data-ttu-id="6ae89-119">Remplacez le contenu du fichier de code Northwind.cs par le code suivant.</span><span class="sxs-lookup"><span data-stu-id="6ae89-119">Replace the contents of the Northwind.cs code file with the following code.</span></span> <span data-ttu-id="6ae89-120">Ce code implémente le fournisseur de réflexion en étendant les classes de données et <xref:System.Data.Linq.DataContext> générés par LINQ to SQL :</span><span class="sxs-lookup"><span data-stu-id="6ae89-120">This code implements the reflection provider by extending the <xref:System.Data.Linq.DataContext> and data classes generated by LINQ to SQL:</span></span>  
  
     [!code-csharp[Astoria Linq Provider#Linq2SqlProvider](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria linq provider/cs/northwind.cs#linq2sqlprovider)]
     [!code-vb[Astoria Linq Provider#Linq2SqlProvider](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria linq provider/vb/northwind.vb#linq2sqlprovider)]  
  
### <a name="to-create-a-data-service-by-using-a-linq-to-sql-based-data-model"></a><span data-ttu-id="6ae89-121">Pour créer un service de données en utilisant un modèle de données LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="6ae89-121">To create a data service by using a LINQ to SQL-based data model</span></span>  
  
1.  <span data-ttu-id="6ae89-122">Dans **l’Explorateur de solutions**, cliquez sur le nom de votre projet ASP.NET, puis cliquez sur **ajouter un nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="6ae89-122">In **Solution Explorer**, right-click the name of your ASP.NET project, and then click **Add New Item**.</span></span>  
  
2.  <span data-ttu-id="6ae89-123">Dans le **ajouter un nouvel élément** boîte de dialogue, sélectionnez **Service de données WCF**.</span><span class="sxs-lookup"><span data-stu-id="6ae89-123">In the **Add New Item** dialog box, select **WCF Data Service**.</span></span>  
  
3.  <span data-ttu-id="6ae89-124">Fournissez un nom pour le service, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="6ae89-124">Supply a name for the service, and then click **OK**.</span></span>  
  
     <span data-ttu-id="6ae89-125">Visual Studio crée le balisage XML et des fichiers de code pour le nouveau service.</span><span class="sxs-lookup"><span data-stu-id="6ae89-125">Visual Studio creates the XML markup and code files for the new service.</span></span> <span data-ttu-id="6ae89-126">La fenêtre de l'éditeur de code s'ouvre par défaut.</span><span class="sxs-lookup"><span data-stu-id="6ae89-126">By default, the code-editor window opens.</span></span>  
  
4.  <span data-ttu-id="6ae89-127">Dans le code du service de données, remplacez le commentaire `/* TODO: put your data source class name here */` dans la définition de la classe qui définit le service de données par le type qui est le conteneur d'entités du modèle de données, dans ce cas `NorthwindDataContext`.</span><span class="sxs-lookup"><span data-stu-id="6ae89-127">In the code for the data service, replace the comment `/* TODO: put your data source class name here */` in the definition of the class that defines the data service with the type that is the entity container of the data model, which in this case is `NorthwindDataContext`.</span></span>  
  
5.  <span data-ttu-id="6ae89-128">Dans le code du service de données, remplacez le code d'espace réservé dans la fonction `InitializeService` par le code suivant :</span><span class="sxs-lookup"><span data-stu-id="6ae89-128">In the code for the data service, replace the placeholder code in the `InitializeService` function with the following:</span></span>  
  
     [!code-csharp[Astoria Linq Provider#EnableAccess](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria linq provider/cs/northwind.svc.cs#enableaccess)]
     [!code-vb[Astoria Linq Provider#EnableAccess](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria linq provider/vb/northwind.svc.vb#enableaccess)]  
  
     <span data-ttu-id="6ae89-129">Cela permet aux clients autorisés d'accéder aux ressources pour les trois jeux d'entités spécifiés.</span><span class="sxs-lookup"><span data-stu-id="6ae89-129">This enables authorized clients to access resources for the three specified entity sets.</span></span>  
  
6.  <span data-ttu-id="6ae89-130">Pour tester le service de données Northwind.svc à l’aide d’un navigateur Web, suivez les instructions de la rubrique [l’accès au Service à partir d’un navigateur Web](../../../../docs/framework/data/wcf/accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md).</span><span class="sxs-lookup"><span data-stu-id="6ae89-130">To test the Northwind.svc data service by using a Web browser, follow the instructions in the topic [Accessing the Service from a Web Browser](../../../../docs/framework/data/wcf/accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ae89-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6ae89-131">See Also</span></span>  
 [<span data-ttu-id="6ae89-132">Comment : créer un Service de données à l’aide d’une Source de données ADO.NET Entity Framework</span><span class="sxs-lookup"><span data-stu-id="6ae89-132">How to: Create a Data Service Using an ADO.NET Entity Framework Data Source</span></span>](../../../../docs/framework/data/wcf/create-a-data-service-using-an-adonet-ef-data-wcf.md)  
 [<span data-ttu-id="6ae89-133">Comment : créer un Service de données à l’aide du fournisseur de réflexion</span><span class="sxs-lookup"><span data-stu-id="6ae89-133">How to: Create a Data Service Using the Reflection Provider</span></span>](../../../../docs/framework/data/wcf/create-a-data-service-using-rp-wcf-data-services.md)  
 [<span data-ttu-id="6ae89-134">Fournisseurs de Services de données</span><span class="sxs-lookup"><span data-stu-id="6ae89-134">Data Services Providers</span></span>](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)
