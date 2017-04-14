---
title: "Interrogation du service de donn&#233;es (WCF Data Services) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-oob"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Services de données WCF, accès aux données"
  - "Services de données WCF, bibliothèque cliente"
  - "Services de données WCF, interroger"
ms.assetid: 823e9444-27aa-4f1f-be8e-0486d67f54c0
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# Interrogation du service de donn&#233;es (WCF Data Services)
La bibliothèque cliente [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] vous permet d'exécuter des requêtes sur un service de données à l'aide de modèles de programmation [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] familiers, notamment LINQ \(Language Integrated Query\).  La bibliothèque cliente traduit une requête, définie sur le client comme une instance de la classe <xref:System.Data.Services.Client.DataServiceQuery%601>, en un message de demande HTTP GET.  La bibliothèque reçoit le message de réponse et le traduit en instances des classes de service de données client.  Ces classes sont suivies par le <xref:System.Data.Services.Client.DataServiceContext> auquel la <xref:System.Data.Services.Client.DataServiceQuery%601> appartient.  
  
## Requêtes du service de données  
 La classe générique <xref:System.Data.Services.Client.DataServiceQuery%601> représente une requête qui retourne une collection de zéro, une ou plusieurs instances de type d'entité.  Une requête du service de données appartient toujours à un contexte du service de données existant.  Ce contexte conserve les informations relatives à l'URI de service et aux métadonnées qui sont requises pour composer et exécuter la requête.  
  
 Lorsque vous utilisez la boîte de dialogue **Ajouter une référence de service** pour ajouter un service de données à une application cliente basée sur [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], une classe de conteneur d'entités qui hérite de la classe <xref:System.Data.Services.Client.DataServiceContext> est créée.  Cette classe inclut des propriétés qui retournent des instances <xref:System.Data.Services.Client.DataServiceQuery%601> typées.  Il y a une propriété pour chaque jeu d'entités exposé par le service de données.  Ces propriétés simplifient la création d'une instance d'un <xref:System.Data.Services.Client.DataServiceQuery%601> typé.  
  
 Une requête est exécutée dans les scénarios suivants :  
  
-   Lorsque les résultats sont énumérés implicitement, tel que :  
  
    -   Lorsqu'une propriété sur <xref:System.Data.Services.Client.DataServiceContext> qui représente un jeu d'entités est énumérée, comme pendant une boucle `foreach` \(C\#\) ou `For Each` \([!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)]\).  
  
    -   Lorsque la requête est assignée à une collection `List`.  
  
-   Lorsque la méthode <xref:System.Data.Services.Client.DataServiceQuery%601.Execute%2A> ou <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> est explicitement appelée.  
  
-   Lorsqu'un opérateur d'exécution de requête LINQ, tel que <xref:System.Linq.Enumerable.First%2A> ou <xref:System.Linq.Enumerable.Single%2A> est appelé.  
  
 La requête suivante, lorsqu'elle est exécutée, retourne toutes les entités `Customers` dans le service de données Northwind :  
  
 [!code-csharp[Astoria Northwind Client#GetAllCustomersSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#getallcustomersspecific)]
 [!code-vb[Astoria Northwind Client#GetAllCustomersSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#getallcustomersspecific)]  
  
 Pour plus d'informations, consultez [Procédure : exécuter des requêtes de service des données](../../../../docs/framework/data/wcf/how-to-execute-data-service-queries-wcf-data-services.md).  
  
 Le client [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] prend en charge les requêtes d'objets à liaison tardive, comme lorsque vous utilisez le type *dynamic* en C\#.  Toutefois, pour de bonnes performances, vous devriez toujours composer des requêtes fortement typées sur le service de données.  La type <xref:System.Tuple> et les objets dynamiques ne sont pas pris en charge par le client.  
  
## Requêtes LINQ  
 Étant donné que la classe <xref:System.Data.Services.Client.DataServiceQuery%601> implémente l'interface <xref:System.Linq.IQueryable%601> définie par LINQ, la bibliothèque cliente [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] est en mesure de transformer des requêtes LINQ sur des données de jeu d'entités en un URI qui représente une expression de requête évalué par rapport à une ressource du service de données.  L'exemple suivant est une requête LINQ équivalente à l'instance <xref:System.Data.Services.Client.DataServiceQuery%601> précédente qui retourne des `Orders` ayant un coût de fret supérieur à $30 et classe les résultats par coût de fret :  
  
 [!code-csharp[Astoria Northwind Client#AddQueryOptionsLinqSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#addqueryoptionslinqspecific)]
 [!code-vb[Astoria Northwind Client#AddQueryOptionsLinqSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#addqueryoptionslinqspecific)]  
  
 Cette requête LINQ est traduite par l'URI de requête suivant exécuté sur le service de données [démarrage rapide](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md) basé sur Northwind :  
  
```  
http://localhost:12345/Northwind.svc/Orders?Orderby=ShippedDate&?filter=Freight gt 30  
```  
  
> [!NOTE]
>  L'ensemble de requêtes pouvant être exprimées dans la syntaxe LINQ est plus étendu que dans la syntaxe d'URI REST \(Representational State Transfer\) utilisée par les services de données.  <xref:System.NotSupportedException> est levée lorsque la requête ne peut pas être mappée à un URI dans le service de données cible.  
  
 Pour plus d'informations, consultez [Considérations sur LINQ](../../../../docs/framework/data/wcf/linq-considerations-wcf-data-services.md).  
  
## Ajout d'options de requête  
 Les requêtes du service de données prennent en charge toutes les options de requête fournies par [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)].  Vous appelez la méthode <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> pour ajouter les options de requête à une instance <xref:System.Data.Services.Client.DataServiceQuery%601>.  <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> retourne une nouvelle instance <xref:System.Data.Services.Client.DataServiceQuery%601> qui est équivalente à la requête d'origine mais avec le nouveau jeu d'options de requête.  La requête suivante, en cas d'exécution, retourne les `Orders` qui sont filtrées par la valeur `Freight` et classées par `OrderID`, dans l'ordre descendant :  
  
 [!code-csharp[Astoria Northwind Client#AddQueryOptionsSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#addqueryoptionsspecific)]
 [!code-vb[Astoria Northwind Client#AddQueryOptionsSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#addqueryoptionsspecific)]  
  
 Vous pouvez utiliser l'option de requête `$orderby` pour organiser et filtrer une requête en fonction d'une seule propriété, comme dans l'exemple suivant qui filtre et organise les objets `Orders` retournés en fonction de la valeur de la propriété `Freight` :  
  
 [!code-csharp[Astoria Northwind Client#OrderWithFilter](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#orderwithfilter)]
 [!code-vb[Astoria Northwind Client#OrderWithFilter](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#orderwithfilter)]  
  
 Vous pouvez appeler consécutivement la méthode <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> pour construire des expressions de requête complexes.  Pour plus d'informations, consultez [Procédure : ajouter des options de requête à une requête de service des données](../../../../docs/framework/data/wcf/how-to-add-query-options-to-a-data-service-query-wcf-data-services.md).  
  
 Les options de requête fournissent une autre méthode pour exprimer les composants syntactiques d'une requête LINQ.  Pour plus d'informations, consultez [Considérations sur LINQ](../../../../docs/framework/data/wcf/linq-considerations-wcf-data-services.md).  
  
> [!NOTE]
>  L'option de requête `$select` ne peut pas être ajoutée à un URI de requête à l'aide de la méthode <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A>.  Nous vous recommandons d'utiliser la méthode LINQ <xref:System.Linq.Enumerable.Select%2A> pour que le client génère l'option de requête `$select` dans l'URI de requête.  
  
<a name="executingQueries"></a>   
## Exécution du client et exécution du serveur  
 Le client exécute une requête en deux parties.  Lorsque cela est possible, les expressions dans une requête sont d'abord évaluées sur le client, puis une requête basée sur l'URI est générée et envoyée au service de données pour être évaluée par rapport aux données dans le service.  Prenons la requête LINQ suivante :  
  
 [!code-csharp[Astoria Northwind Client#LinqQueryClientEvalSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#linqqueryclientevalspecific)]
 [!code-vb[Astoria Northwind Client#LinqQueryClientEvalSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#linqqueryclientevalspecific)]  
  
 Dans cet exemple, l'expression `(basePrice – (basePrice * discount))` est évaluée sur le client.  À cause de cela, l'URI de requête réel `http://localhost:12345/northwind.svc/Products()?$filter=(UnitPrice gt 90.00M) and substringof('bike',ProductName)` transmis au service de données contient la valeur décimale `90` déjà calculée dans la clause de filtre.  Les autres parties de l'expression de filtrage, y compris l'expression de la sous\-chaîne, sont évaluées par le service de données.  Les expressions qui sont évaluées sur le client suivent la sémantique CLR \(Common Language Runtime\), tandis que les expressions transmises au service de données reposent sur l'implémentation du protocole [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] dans le service de données.  Vous devriez également tenir compte des scénarios où cette évaluation séparée peut entraîner des résultats inattendus, comme quand le client et le service exécutent des évaluations basées sur le temps dans différents fuseaux horaires.  
  
## Réponses aux requêtes  
 En cas d'exécution, <xref:System.Data.Services.Client.DataServiceQuery%601> retourne un <xref:System.Collections.Generic.IEnumerable%601> du type d'entité demandé.  Ce résultat de requête peut être converti en un objet <xref:System.Data.Services.Client.QueryOperationResponse%601>, comme dans l'exemple suivant :  
  
 [!code-csharp[Astoria Northwind Client#GetResponseSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#getresponsespecific)]
 [!code-vb[Astoria Northwind Client#GetResponseSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#getresponsespecific)]  
  
 Les instances de type d'entité qui représentent des entités dans le service de données sont créées sur le client par le biais d'un processus appelé matérialisation d'objets.  Pour plus d'informations, consultez [Matérialisation d'objets](../../../../docs/framework/data/wcf/object-materialization-wcf-data-services.md).  L'objet <xref:System.Data.Services.Client.QueryOperationResponse%601> implémente <xref:System.Collections.Generic.IEnumerable%601> pour fournir un accès aux résultats de la requête.  
  
 <xref:System.Data.Services.Client.QueryOperationResponse%601> a également les membres suivants qui vous permettent d'accéder à des informations supplémentaires sur un résultat de requête :  
  
-   <xref:System.Data.Services.Client.OperationResponse.Error%2A>\- affiche une erreur résultant de l'opération, le cas échéant.  
  
-   <xref:System.Data.Services.Client.OperationResponse.Headers%2A>\- contient la collection d'en\-têtes de réponse HTTP associée à la réponse à la requête.  
  
-   <xref:System.Data.Services.Client.QueryOperationResponse.Query%2A> \- obtient l'instance <xref:System.Data.Services.Client.DataServiceQuery%601> originale qui a créé le <xref:System.Data.Services.Client.QueryOperationResponse%601>.  
  
-   <xref:System.Data.Services.Client.OperationResponse.StatusCode%2A> \- obtient le code de réponse HTTP pour la réponse à la requête.  
  
-   <xref:System.Data.Services.Client.QueryOperationResponse%601.TotalCount%2A>\- place le nombre total d'entités dans le jeu d'entités lorsque la méthode <xref:System.Data.Services.Client.DataServiceQuery%601.IncludeTotalCount%2A> a été appelée sur le <xref:System.Data.Services.Client.DataServiceQuery%601>.  
  
-   <xref:System.Data.Services.Client.QueryOperationResponse.GetContinuation%2A>\- retourne un objet <xref:System.Data.Services.Client.DataServiceQueryContinuation> qui contient l'URI de la page suivante de résultats.  
  
 Par défaut, [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] retourne seulement les données sélectionnées explicitement par l'URI de requête.  Cela vous permet de charger explicitement des données supplémentaires à partir du service de données lorsque cela est nécessaire.  Une demande est envoyée au service de données chaque fois vous chargez explicitement des données à partir du service de données.  Les données qui peuvent être chargées explicitement incluent des entités associées, des données de réponse paginées et des flux de données binaires.  
  
> [!NOTE]
>  Étant donné qu'un service de données peut retourner une réponse paginée, nous recommandons que votre application utilise le modèle de programmation pour gérer une réponse du service de données paginée.  Pour plus d'informations, consultez [Chargement de contenu différé](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md).  
  
 La quantité de données retournée par une requête peut également être réduite en spécifiant que seules certaines propriétés d'une entité doivent être retournées dans la réponse.  Pour plus d'informations, consultez [Projections de requête](../../../../docs/framework/data/wcf/query-projections-wcf-data-services.md).  
  
## Obtenir un décompte du nombre total d'entités d'un jeu  
 Dans certains scénarios, il est utile de connaître le nombre total d'entités d'un jeu d'entités et pas simplement le nombre retourné par la requête.  Appelez la méthode <xref:System.Data.Services.Client.DataServiceQuery%601.IncludeTotalCount%2A> sur l'instance <xref:System.Data.Services.Client.DataServiceQuery%601> pour demander que le nombre total d'entités du jeu soit inclus dans le résultat de la requête.  Dans ce cas, la propriété <xref:System.Data.Services.Client.QueryOperationResponse%601.TotalCount%2A> du <xref:System.Data.Services.Client.QueryOperationResponse%601> retourné renvoie le nombre total d'entités du jeu.  
  
 Vous pouvez également obtenir uniquement le nombre total d'entités du jeu comme un <xref:System.Int32> ou comme une valeur <xref:System.Int64> en appelant les méthodes <xref:System.Linq.Enumerable.Count%2A> ou <xref:System.Linq.Enumerable.LongCount%2A> respectivement.  Lorsque ces méthodes sont appelées, le <xref:System.Data.Services.Client.QueryOperationResponse%601> n'est pas retourné ; seule la valeur du compteur est retournée.  Pour plus d'informations, consultez [Procédure : déterminer le nombre d'entités retournées par une requête](../../../../docs/framework/data/wcf/number-of-entities-returned-by-a-query-wcf.md).  
  
## Dans cette section  
 [Projections de requête](../../../../docs/framework/data/wcf/query-projections-wcf-data-services.md)  
  
 [Matérialisation d'objets](../../../../docs/framework/data/wcf/object-materialization-wcf-data-services.md)  
  
 [Considérations sur LINQ](../../../../docs/framework/data/wcf/linq-considerations-wcf-data-services.md)  
  
 [Procédure : exécuter des requêtes de service des données](../../../../docs/framework/data/wcf/how-to-execute-data-service-queries-wcf-data-services.md)  
  
 [Procédure : ajouter des options de requête à une requête de service des données](../../../../docs/framework/data/wcf/how-to-add-query-options-to-a-data-service-query-wcf-data-services.md)  
  
 [Procédure : déterminer le nombre d'entités retournées par une requête](../../../../docs/framework/data/wcf/number-of-entities-returned-by-a-query-wcf.md)  
  
 [Procédure : spécifier les informations d'identification du client pour une demande de service de données](../../../../docs/framework/data/wcf/specify-client-creds-for-a-data-service-request-wcf.md)  
  
 [Procédure : définir des en\-têtes dans la demande cliente](../../../../docs/framework/data/wcf/how-to-set-headers-in-the-client-request-wcf-data-services.md)  
  
 [Procédure : projeter des résultats de requête](../../../../docs/framework/data/wcf/how-to-project-query-results-wcf-data-services.md)  
  
## Voir aussi  
 [Bibliothèque cliente de WCF Data Services](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)