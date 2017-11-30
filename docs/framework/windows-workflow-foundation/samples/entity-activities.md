---
title: "Activités d'entités"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c04f7413-7fb8-40c6-819e-dc92b145b62e
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6a3f50999e80cea0cf2d3e8280abe4204076e653
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="entity-activities"></a><span data-ttu-id="85e7b-102">Activités d'entités</span><span class="sxs-lookup"><span data-stu-id="85e7b-102">Entity Activities</span></span>
<span data-ttu-id="85e7b-103">Cet exemple montre comment utiliser ADO.NET Entity Framework avec [!INCLUDE[wf2](../../../../includes/wf2-md.md)] pour simplifier l'accès aux données.</span><span class="sxs-lookup"><span data-stu-id="85e7b-103">This sample shows how to use the ADO.NET Entity Framework with [!INCLUDE[wf2](../../../../includes/wf2-md.md)] to simplify data access.</span></span>  
  
 <span data-ttu-id="85e7b-104">ADO.NET Entity Framework permet aux développeurs d'utiliser des données sous forme d'objets spécifiques au domaine, de propriétés et de relations, telles Customers, Orders, Order Details et les relations entre ces entités.</span><span class="sxs-lookup"><span data-stu-id="85e7b-104">The ADO.NET Entity Framework enables developers to work with data in the form of domain-specific objects, properties and relationships such as Customers, Orders, Order Details and the relationships between these entities.</span></span> <span data-ttu-id="85e7b-105">Pour ce faire, ADO.NET Entity Framework fournit un niveau d’abstraction qui permet la programmation sur un modèle d’application conceptuel au lieu d’une programmation directe sur un schéma de stockage relationnel.</span><span class="sxs-lookup"><span data-stu-id="85e7b-105">The ADO.NET Entity Framework does this by providing a level of abstraction that enables programming against a conceptual application model instead of programming directly against a relational storage schema.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="85e7b-106">ADO.NET Entity Framework, consultez [ADO.NET Entity Framework](http://go.microsoft.com/fwlink/?LinkId=165549).</span><span class="sxs-lookup"><span data-stu-id="85e7b-106"> the ADO.NET Entity Framework see [ADO.NET Entity Framework](http://go.microsoft.com/fwlink/?LinkId=165549).</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="85e7b-107">Détails de l'exemple</span><span class="sxs-lookup"><span data-stu-id="85e7b-107">Sample details</span></span>  
 <span data-ttu-id="85e7b-108">Cet exemple utilise la base de données `Northwind` et inclut des scripts pour la création et la suppression de la base de données `Northwind` (Setup.cmd et Cleanup.cmd).</span><span class="sxs-lookup"><span data-stu-id="85e7b-108">This sample uses the `Northwind` database and includes scripts for creating and removing the `Northwind` database (Setup.cmd and Cleanup.cmd).</span></span> <span data-ttu-id="85e7b-109">Les projets dans cet exemple incluent un Entity Data Model basé sur la base de données `Northwind`.</span><span class="sxs-lookup"><span data-stu-id="85e7b-109">The projects in this sample include an Entity Data Model based on the `Northwind` database.</span></span> <span data-ttu-id="85e7b-110">Vous pouvez rechercher le modèle en ouvrant le fichier `Northwind.edmx` inclus dans le projet.</span><span class="sxs-lookup"><span data-stu-id="85e7b-110">You can find the model by opening the `Northwind.edmx` file that is included in the project.</span></span> <span data-ttu-id="85e7b-111">Il s'agit du modèle qui définit la forme des objets accessibles à l'aide d'ADO.NET Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="85e7b-111">This is the model that defines the shape of the objects that can be accessed using the ADO.NET Entity Framework.</span></span>  
  
 <span data-ttu-id="85e7b-112">Les activités suivantes sont incluses dans cet exemple :</span><span class="sxs-lookup"><span data-stu-id="85e7b-112">The following activities are included in this sample:</span></span>  
  
-   <span data-ttu-id="85e7b-113">`EntitySQLQuery` : l'activité `EntitySQLQuery` vous permet de récupérer des objets de la base de données selon une chaîne de requête Entity SQL.</span><span class="sxs-lookup"><span data-stu-id="85e7b-113">`EntitySQLQuery`: The `EntitySQLQuery` activity allows you to retrieve objects from the database based on an Entity SQL query string.</span></span> <span data-ttu-id="85e7b-114">Entity SQL est un langage indépendant du stockage qui est similaire à SQL et vous permet de spécifier des requêtes selon le modèle conceptuel et les entités qui font partie du modèle ou du domaine.</span><span class="sxs-lookup"><span data-stu-id="85e7b-114">Entity SQL is a store independent language that is similar to SQL and it allows you to specify queries based on the conceptual model and the entities that are a part of the model or domain.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="85e7b-115">Langage Entity SQL, consultez [langage Entity SQL](http://go.microsoft.com/fwlink/?LinkId=165646).</span><span class="sxs-lookup"><span data-stu-id="85e7b-115"> Entity SQL Language, see [Entity SQL Language](http://go.microsoft.com/fwlink/?LinkId=165646).</span></span>  
  
-   <span data-ttu-id="85e7b-116">`EntityLinqQuery` : cette activité vous permet de récupérer des objets de la base de données selon une requête LINQ ou un prédicat.</span><span class="sxs-lookup"><span data-stu-id="85e7b-116">`EntityLinqQuery`: This activity allows you to retrieve objects from the database based on a LINQ query or predicate.</span></span>  
  
-   <span data-ttu-id="85e7b-117">`EntityAdd` : l'activité `EntityAdd` vous permet d'ajouter une entité ou une collection d'entités à la base de données.</span><span class="sxs-lookup"><span data-stu-id="85e7b-117">`EntityAdd`: The `EntityAdd` activity allows you to add an entity or a collection of entities to the database.</span></span>  
  
-   <span data-ttu-id="85e7b-118">`EntityDelete` : l'activité `EntityDelete` vous permet de supprimer une entité ou une collection d'entités de la base de données.</span><span class="sxs-lookup"><span data-stu-id="85e7b-118">`EntityDelete`: The `EntityDelete` activity allows you to delete an entity or a collection of entities from the database.</span></span>  
  
-   <span data-ttu-id="85e7b-119">`ObjectContextScope` : les activités indiquées précédemment peuvent être utilisées uniquement dans une instance d'activité `ObjectContextScope` contenant.</span><span class="sxs-lookup"><span data-stu-id="85e7b-119">`ObjectContextScope`: The previously mentioned activities can only be used within a containing `ObjectContextScope` activity instance.</span></span> <span data-ttu-id="85e7b-120">L'activité `ObjectContextScope` configure la connexion à la base de données.</span><span class="sxs-lookup"><span data-stu-id="85e7b-120">The `ObjectContextScope` activity sets up the connection to the database.</span></span> <span data-ttu-id="85e7b-121">Elle requiert une chaîne de connexion (passée ou récupérée à l'aide d'un paramètre de fichier de configuration).</span><span class="sxs-lookup"><span data-stu-id="85e7b-121">It requires a connection string (that is either passed in or retrieved using a configuration file setting).</span></span> <span data-ttu-id="85e7b-122">L'activité `ObjectContextScope` facilite l'exécution d'un groupe d'opérations connexes sur les entités.</span><span class="sxs-lookup"><span data-stu-id="85e7b-122">The `ObjectContextScope` activity makes it easy to perform a group of related operations on entities.</span></span> <span data-ttu-id="85e7b-123">Étant donné que cette portée gère une connexion active, il s'agit d'une portée de non-persistance.</span><span class="sxs-lookup"><span data-stu-id="85e7b-123">Because this scope maintains an active connection, it is a No Persist scope.</span></span> <span data-ttu-id="85e7b-124">De plus, lorsque l'activité `ObjectContextScope` s'arrête, toutes les modifications apportées aux objets récupérés à l'aide des activités d'entités dans cette portée sont automatiquement rendues persistantes dans la base de données, et aucune action explicite ou suivante n'est requise pour enregistrer les objets dans la base de données.</span><span class="sxs-lookup"><span data-stu-id="85e7b-124">In addition, when the `ObjectContextScope` activity exits, any changes that are made to objects retrieved using Entity Activities within that scope automatically get persisted back to the database, and no explicit or subsequent action is required to save objects back to the database.</span></span>  
  
## <a name="using-the-entity-activities"></a><span data-ttu-id="85e7b-125">Utilisation des activités d'entités</span><span class="sxs-lookup"><span data-stu-id="85e7b-125">Using the entity activities</span></span>  
 <span data-ttu-id="85e7b-126">Les extraits de code suivants montrent comment utiliser les activités d'entités présentées dans cet exemple.</span><span class="sxs-lookup"><span data-stu-id="85e7b-126">The following code snippets demonstrate how to use the entity activities presented in this sample.</span></span>  
  
### <a name="entitysql"></a><span data-ttu-id="85e7b-127">EntitySql</span><span class="sxs-lookup"><span data-stu-id="85e7b-127">EntitySql</span></span>  
 <span data-ttu-id="85e7b-128">L'extrait de code ci-dessous montre comment interroger tous les clients dans Londres triés par nom et comment effectuer une itération au sein de la liste de clients.</span><span class="sxs-lookup"><span data-stu-id="85e7b-128">The code snippet below shows how to query all customers in London sorted by name and how to iterate through the list of customers.</span></span>  
  
```  
Variable<IEnumerable<Customer>> londonCustomers = new Variable<IEnumerable<Customer>>();  
DelegateInArgument<Customer> iterationVariable = new DelegateInArgument<Customer>();  
  
// create and return the workflow  
return new ObjectContextScope  
{  
    ConnectionString = new InArgument<string>(connStr),  
    ContainerName = "NorthwindEntities",  
    Variables = { londonCustomers },  
    Body = new Sequence  
        {  
            Activities =   
                {               
                    new WriteLine { Text = "Executing query" },                            
                    // query for all customers that are in london   
                    new EntitySqlQuery<Customer>  
                    {  
                        EntitySql =  @"SELECT VALUE Customer   
                                        FROM NorthwindEntities.Customers AS Customer   
                                        WHERE Customer.City = 'London'   
                                        ORDER BY Customer.ContactName",  
                        Result = londonCustomers  
                    },  
  
                    // iterate through the list of customers and display them   
                    new ForEach<Customer>  
                    {                                      
                        Values = londonCustomers,  
                        Body = new ActivityAction<Customer>  
                        {  
                            Argument = iterationVariable,  
                            Handler = new WriteLine   
                            {   
                                  Text = new InArgument<String>(e =>    
                                              iterationVariable.Get(e).ContactName)   
                            }  
                        }  
                    }  
                }  
        }                 
};     
```  
  
### <a name="entitylinqquery"></a><span data-ttu-id="85e7b-129">EntityLinqQuery</span><span class="sxs-lookup"><span data-stu-id="85e7b-129">EntityLinqQuery</span></span>  
 <span data-ttu-id="85e7b-130">L'extrait de code ci-dessous montre comment interroger tous les clients dans Londres et comment effectuer une itération au sein de la liste résultante de clients.</span><span class="sxs-lookup"><span data-stu-id="85e7b-130">The code snippet below shows how to query all customers in London and how to iterate through the resulting list of customers.</span></span>  
  
```  
Variable<IEnumerable<Customer>> londonCustomers = new Variable<IEnumerable<Customer>>() { Name = "LondonCustomers" };  
DelegateInArgument<Customer> iterationVariable = new DelegateInArgument<Customer>() { Name = "iterationVariable" };  
  
return new ObjectContextScope  
{  
    ConnectionString = new InArgument<string>(connStr),  
    ContainerName = "NorthwindEntities",  
    Variables = { londonCustomers },  
    Body = new Sequence  
    {  
        Activities =   
        {               
            // return all the customers that match with the provided Linq predicate  
            new EntityLinqQuery<Customer>  
            {   
                Predicate = new LambdaValue<Func<Customer, bool>>(  
                          ctx => new Func<Customer, bool>(c => c.City.Equals("London"))),                              
                Result = londonCustomers  
            },  
  
            // iterate through the list of customers and display in the console  
            new ForEach<Customer>  
            {                                      
                Values = londonCustomers,  
                Body = new ActivityAction<Customer>  
                {  
                    Argument = iterationVariable,  
                    Handler = new WriteLine   
                    {   
                        Text = new InArgument<String>(e =>   
                                      iterationVariable.Get(e).ContactName)   
                    }  
                }  
            }  
        }  
    }  
};  
```  
  
### <a name="entityadd"></a><span data-ttu-id="85e7b-131">EntityAdd</span><span class="sxs-lookup"><span data-stu-id="85e7b-131">EntityAdd</span></span>  
 <span data-ttu-id="85e7b-132">L'extrait de code ci-dessous montre comment ajouter un enregistrement OrderDetail à un Order existant.</span><span class="sxs-lookup"><span data-stu-id="85e7b-132">The code snippet below shows how to add an OrderDetail record to an existing Order.</span></span>  
  
```  
Variable<IEnumerable<Order>> orders = new Variable<IEnumerable<Order>>();  
Variable<IEnumerable<OrderDetail>> orderDetails = new Variable<IEnumerable<OrderDetail>>();  
Variable<Order> order = new Variable<Order>();  
Variable<OrderDetail> orderDetail = new Variable<OrderDetail>();              
  
return new ObjectContextScope  
{  
    Variables = { order, orders, orderDetail, orderDetails },  
    ContainerName = "NorthwindEntities",  
    ConnectionString = new InArgument<string>(connStr),                  
    Body = new Sequence  
    {                      
        Activities =   
        {                            
           // get the order where we want to add the detail  
           new EntitySqlQuery<Order>  
           {  
               EntitySql =    
                    @"SELECT VALUE [Order]  
                      FROM NorthwindEntities.Orders as [Order]  
                      WHERE Order.OrderID == 10249",  
               Result = orders  
           },  
  
           // store the order in a variable  
           new Assign<Order>   
           {  
               To = new OutArgument<Order>(order),  
               Value = new InArgument<Order>(c => orders.Get(c).First<Order>())  
           },  
  
           // add the detail to the order  
           new EntityAdd<OrderDetail>  
           {  
               Entity = new InArgument<OrderDetail>(c =>   
                                         new OrderDetail {   
                                                  OrderID=10249, ProductID=11,   
                                                  Quantity=1, UnitPrice = 15,   
                                                  Discount = 0, Order = order.Get(c) })  
           }  
        }  
    }  
};  
```  
  
### <a name="entitydelete"></a><span data-ttu-id="85e7b-133">EntityDelete</span><span class="sxs-lookup"><span data-stu-id="85e7b-133">EntityDelete</span></span>  
 <span data-ttu-id="85e7b-134">L'extrait de code ci-dessous montre comment supprimer un enregistrement OrderDetail existant dans un Order (s'il existe).</span><span class="sxs-lookup"><span data-stu-id="85e7b-134">The code snippet below shows how to delete an existing OrderDetail record in an Order (if it exists).</span></span>  
  
```  
Variable<IEnumerable<OrderDetail>> orderDetails = new Variable<IEnumerable<OrderDetail>>();              
  
return new ObjectContextScope  
{  
    Variables = { orderDetails },  
    ConnectionString = new InArgument<string>(connStr),  
    ContainerName = "NorthwindEntities",  
    Body = new Sequence  
    {  
        Activities =   
        {               
            // find the entitiy to be deleted (order detail for product 11 in order 10249)  
            new EntitySqlQuery<OrderDetail>  
            {  
                EntitySql = @"SELECT VALUE OrderDetail  
                                FROM NorthwindEntities.OrderDetails as OrderDetail  
                               WHERE OrderDetail.OrderID == 10249   
                                 AND OrderDetail.ProductID == 11",  
                Result = orderDetails  
            },  
  
            // if the order detail is found, delete it, otherwise, display a message  
            new If  
            {  
                Condition = new InArgument<bool>(c=>orderDetails.Get(c).Count() > 0),  
                Then = new Sequence  
                {   
                    Activities =   
                    {                                      
                        new EntityDelete<OrderDetail>  
                        {  
                            Entity = new InArgument<OrderDetail>(c =>   
                                              orderDetails.Get(c).First<OrderDetail>())  
                        },  
                    }  
                },                              
                Else = new WriteLine { Text = "Order Detail for Deleting not found" }                              
            }                                                  
        }  
    }  
};  
```  
  
## <a name="to-use-this-sample"></a><span data-ttu-id="85e7b-135">Pour utiliser cet exemple</span><span class="sxs-lookup"><span data-stu-id="85e7b-135">To use this sample</span></span>  
 <span data-ttu-id="85e7b-136">Vous devez créer la base de données `Northwind` dans votre instance SQL Server Express locale avant d'exécuter cet exemple.</span><span class="sxs-lookup"><span data-stu-id="85e7b-136">You must create the `Northwind` database in your local SQL server Express instance before running this sample.</span></span>  
  
#### <a name="to-set-up-the-northwind-database"></a><span data-ttu-id="85e7b-137">Pour configurer la base de données Northwind</span><span class="sxs-lookup"><span data-stu-id="85e7b-137">To set up the Northwind database</span></span>  
  
1.  <span data-ttu-id="85e7b-138">Ouvrez une invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="85e7b-138">Open a command prompt.</span></span>  
  
2.  <span data-ttu-id="85e7b-139">Dans la nouvelle fenêtre d’invite de commandes, accédez au dossier EntityActivities\CS.</span><span class="sxs-lookup"><span data-stu-id="85e7b-139">In the new command prompt window, navigate to the EntityActivities\CS folder.</span></span>  
  
3.  <span data-ttu-id="85e7b-140">Type `setup.cmd` et appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="85e7b-140">Type `setup.cmd` and press ENTER.</span></span>  
  
#### <a name="to-run-the-sample"></a><span data-ttu-id="85e7b-141">Pour exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="85e7b-141">To run the sample</span></span>  
  
1.  <span data-ttu-id="85e7b-142">À l'aide de [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], ouvrez le fichier solution EntityActivities.sln.</span><span class="sxs-lookup"><span data-stu-id="85e7b-142">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open the EntityActivities.sln solution file.</span></span>  
  
2.  <span data-ttu-id="85e7b-143">Pour générer la solution, appuyez sur Ctrl+Maj+B.</span><span class="sxs-lookup"><span data-stu-id="85e7b-143">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="85e7b-144">Pour exécuter la solution, appuyez sur Ctrl+F5.</span><span class="sxs-lookup"><span data-stu-id="85e7b-144">To run the solution, press CTRL+F5.</span></span>  
  
 <span data-ttu-id="85e7b-145">Après avoir exécuté cet exemple, vous pouvez supprimer la base de données `Northwind`.</span><span class="sxs-lookup"><span data-stu-id="85e7b-145">After running this sample, you may want to remove the `Northwind` database.</span></span>  
  
#### <a name="to-uninstall-the-northwind-database"></a><span data-ttu-id="85e7b-146">Pour désinstaller la base de données Northwind</span><span class="sxs-lookup"><span data-stu-id="85e7b-146">To uninstall the Northwind database</span></span>  
  
1.  <span data-ttu-id="85e7b-147">Ouvrez une invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="85e7b-147">Open a command prompt.</span></span>  
  
2.  <span data-ttu-id="85e7b-148">Dans la nouvelle fenêtre d’invite de commandes, accédez au dossier EntityActivities\CS.</span><span class="sxs-lookup"><span data-stu-id="85e7b-148">In the new command prompt window, navigate to the EntityActivities\CS folder.</span></span>  
  
3.  <span data-ttu-id="85e7b-149">Type `cleanup.cmd` et appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="85e7b-149">Type `cleanup.cmd` and press ENTER.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="85e7b-150">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="85e7b-150">The samples may already be installed on your machine.</span></span> <span data-ttu-id="85e7b-151">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="85e7b-151">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="85e7b-152">Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="85e7b-152">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="85e7b-153">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="85e7b-153">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\EntityActivities`