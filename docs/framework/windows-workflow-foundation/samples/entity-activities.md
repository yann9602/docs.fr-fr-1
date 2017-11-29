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
ms.openlocfilehash: cc1ddb69e69e603c4460ef6db1a60f4e2e650749
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="entity-activities"></a>Activités d'entités
Cet exemple montre comment utiliser ADO.NET Entity Framework avec [!INCLUDE[wf2](../../../../includes/wf2-md.md)] pour simplifier l'accès aux données.  
  
 ADO.NET Entity Framework permet aux développeurs d'utiliser des données sous forme d'objets spécifiques au domaine, de propriétés et de relations, telles Customers, Orders, Order Details et les relations entre ces entités. Pour ce faire, ADO.NET Entity Framework fournit un niveau d’abstraction qui permet la programmation sur un modèle d’application conceptuel au lieu d’une programmation directe sur un schéma de stockage relationnel. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]ADO.NET Entity Framework, consultez [ADO.NET Entity Framework](http://go.microsoft.com/fwlink/?LinkId=165549).  
  
## <a name="sample-details"></a>Détails de l'exemple  
 Cet exemple utilise la base de données `Northwind` et inclut des scripts pour la création et la suppression de la base de données `Northwind` (Setup.cmd et Cleanup.cmd). Les projets dans cet exemple incluent un Entity Data Model basé sur la base de données `Northwind`. Vous pouvez rechercher le modèle en ouvrant le fichier `Northwind.edmx` inclus dans le projet. Il s'agit du modèle qui définit la forme des objets accessibles à l'aide d'ADO.NET Entity Framework.  
  
 Les activités suivantes sont incluses dans cet exemple :  
  
-   `EntitySQLQuery` : l'activité `EntitySQLQuery` vous permet de récupérer des objets de la base de données selon une chaîne de requête Entity SQL. Entity SQL est un langage indépendant du stockage qui est similaire à SQL et vous permet de spécifier des requêtes selon le modèle conceptuel et les entités qui font partie du modèle ou du domaine. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Langage Entity SQL, consultez [langage Entity SQL](http://go.microsoft.com/fwlink/?LinkId=165646).  
  
-   `EntityLinqQuery` : cette activité vous permet de récupérer des objets de la base de données selon une requête LINQ ou un prédicat.  
  
-   `EntityAdd` : l'activité `EntityAdd` vous permet d'ajouter une entité ou une collection d'entités à la base de données.  
  
-   `EntityDelete` : l'activité `EntityDelete` vous permet de supprimer une entité ou une collection d'entités de la base de données.  
  
-   `ObjectContextScope` : les activités indiquées précédemment peuvent être utilisées uniquement dans une instance d'activité `ObjectContextScope` contenant. L'activité `ObjectContextScope` configure la connexion à la base de données. Elle requiert une chaîne de connexion (passée ou récupérée à l'aide d'un paramètre de fichier de configuration). L'activité `ObjectContextScope` facilite l'exécution d'un groupe d'opérations connexes sur les entités. Étant donné que cette portée gère une connexion active, il s'agit d'une portée de non-persistance. De plus, lorsque l'activité `ObjectContextScope` s'arrête, toutes les modifications apportées aux objets récupérés à l'aide des activités d'entités dans cette portée sont automatiquement rendues persistantes dans la base de données, et aucune action explicite ou suivante n'est requise pour enregistrer les objets dans la base de données.  
  
## <a name="using-the-entity-activities"></a>Utilisation des activités d'entités  
 Les extraits de code suivants montrent comment utiliser les activités d'entités présentées dans cet exemple.  
  
### <a name="entitysql"></a>EntitySql  
 L'extrait de code ci-dessous montre comment interroger tous les clients dans Londres triés par nom et comment effectuer une itération au sein de la liste de clients.  
  
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
  
### <a name="entitylinqquery"></a>EntityLinqQuery  
 L'extrait de code ci-dessous montre comment interroger tous les clients dans Londres et comment effectuer une itération au sein de la liste résultante de clients.  
  
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
  
### <a name="entityadd"></a>EntityAdd  
 L'extrait de code ci-dessous montre comment ajouter un enregistrement OrderDetail à un Order existant.  
  
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
  
### <a name="entitydelete"></a>EntityDelete  
 L'extrait de code ci-dessous montre comment supprimer un enregistrement OrderDetail existant dans un Order (s'il existe).  
  
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
  
## <a name="to-use-this-sample"></a>Pour utiliser cet exemple  
 Vous devez créer la base de données `Northwind` dans votre instance SQL Server Express locale avant d'exécuter cet exemple.  
  
#### <a name="to-set-up-the-northwind-database"></a>Pour configurer la base de données Northwind  
  
1.  Ouvrez une invite de commandes.  
  
2.  Dans la nouvelle fenêtre d’invite de commandes, accédez au dossier EntityActivities\CS.  
  
3.  Type `setup.cmd` et appuyez sur ENTRÉE.  
  
#### <a name="to-run-the-sample"></a>Pour exécuter l'exemple  
  
1.  À l'aide de [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], ouvrez le fichier solution EntityActivities.sln.  
  
2.  Pour générer la solution, appuyez sur Ctrl+Maj+B.  
  
3.  Pour exécuter la solution, appuyez sur Ctrl+F5.  
  
 Après avoir exécuté cet exemple, vous pouvez supprimer la base de données `Northwind`.  
  
#### <a name="to-uninstall-the-northwind-database"></a>Pour désinstaller la base de données Northwind  
  
1.  Ouvrez une invite de commandes.  
  
2.  Dans la nouvelle fenêtre d’invite de commandes, accédez au dossier EntityActivities\CS.  
  
3.  Type `cleanup.cmd` et appuyez sur ENTRÉE.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\EntityActivities`  
  
## <a name="see-also"></a>Voir aussi
