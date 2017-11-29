---
title: "Appel des opérations de service (WCF Data Services)"
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
ms.assetid: 1767f3a7-29d2-4834-a763-7d169693fa8b
caps.latest.revision: "4"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: e43fbe2002c19b8203ff048b4200dcfaad27afe0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="calling-service-operations-wcf-data-services"></a>Appel des opérations de service (WCF Data Services)
[!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] définit les opérations de service d'un service de données. [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] vous permet de définir ces opérations sous forme de méthodes dans le service de données. Comme les autres ressources du service de données, ces opérations de service sont adressées via les URI. Une opération de service peut retourner des collections de types d'entité, des instances uniques de type d'entité et des types primitifs, comme des entiers et des chaînes. Une opération de service peut également retourner `null` (`Nothing` en Visual Basic). La bibliothèque cliente [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] peut être utilisée pour accéder aux opérations de service qui prennent en charge les requêtes HTTP GET. Ces types d'opérations de service sont définis en tant que méthodes ayant <xref:System.ServiceModel.Web.WebGetAttribute> appliqué. Pour plus d’informations, consultez [les opérations de Service](../../../../docs/framework/data/wcf/service-operations-wcf-data-services.md).  
  
 Les opérations de service sont exposées dans les métadonnées retournées par un service de données qui implémente [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]. Dans les métadonnées, les opérations de service sont représentées sous la forme d'éléments `FunctionImport`. Lors de la génération du <xref:System.Data.Services.Client.DataServiceContext>fortement typé, les outils Ajouter une référence de service et DataSvcUtil.exe ignorent cet élément. De ce fait, vous ne trouverez pas de méthode dans le contexte pouvant être utilisée pour appeler une opération de service directement. Toutefois, vous pouvez encore utiliser le client [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] pour appeler les opérations de service de l'une des deux façons suivantes :  
  
-   En appelant la méthode <xref:System.Data.Services.Client.DataServiceContext.Execute%2A> sur <xref:System.Data.Services.Client.DataServiceContext> et en fournissant l'URI de l'opération de service, ainsi que tous paramètres. Cette méthode est utilisée pour appeler toute opération de service GET.  
  
-   À l'aide de la méthode <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> sur <xref:System.Data.Services.Client.DataServiceContext> pour créer un objet <xref:System.Data.Services.Client.DataServiceQuery%601>. En appelant <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A>, le nom de l'opération de service est fourni au paramètre `entitySetName`. Cette méthode retourne un objet <xref:System.Data.Services.Client.DataServiceQuery%601> qui appelle l'opération de service si elle est énumérée ou lorsque la méthode <xref:System.Data.Services.Client.DataServiceQuery%601.Execute%2A> est appelée. Cette méthode est utilisée pour appeler les opérations de service GET qui retournent une collection. Un seul paramètre peut être fourni à l'aide de la méthode <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A>. L'objet <xref:System.Data.Services.Client.DataServiceQuery%601> retourné par cette méthode peut être davantage composé comme n'importe quel objet de requête. Pour plus d’informations, consultez [interrogation du Service de données](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md).  
  
## <a name="considerations-for-calling-service-operations"></a>Considérations sur l'appel des opérations de service  
 Les considérations suivantes s'appliquent lorsque vous utilisez le client [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] pour appeler des opérations de service.  
  
-   Lors de l’accès au service de données de façon asynchrone, vous devez utiliser les équivalents asynchrones <xref:System.Data.Services.Client.DataServiceContext.BeginExecute%2A> / <xref:System.Data.Services.Client.DataServiceContext.EndExecute%2A> méthodes sur <xref:System.Data.Services.Client.DataServiceContext> ou <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> / <xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A> méthodes sur <xref:System.Data.Services.Client.DataServiceQuery%601>.  
  
-   La bibliothèque cliente [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] ne peut pas matérialiser les résultats d'une opération de service qui retourne une collection de types primitifs.  
  
-   La bibliothèque cliente [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] ne prend pas en charge les opérations de service POST appelantes. Les opérations de service qui sont appelées par une demande HTTP POST sont définies à l'aide du <xref:System.ServiceModel.Web.WebInvokeAttribute> avec le paramètre `Method="POST"`. Pour appeler une opération de service à l'aide d'une requête HTTP POST, vous devez plutôt utiliser <xref:System.Net.HttpWebRequest>.  
  
-   Vous ne pouvez pas utiliser <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> pour appeler une opération de service GET qui retourne un résultat unique, d'entité ou de type primitif, ou qui requiert plusieurs paramètres d'entrée. Vous devez à la place appeler la méthode <xref:System.Data.Services.Client.DataServiceContext.Execute%2A>.  
  
-   Envisagez de créer une méthode d'extension pour la classe partielle fortement typée <xref:System.Data.Services.Client.DataServiceContext>, générée par les outils, qui utilise la méthode <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> ou <xref:System.Data.Services.Client.DataServiceContext.Execute%2A> pour appeler une opération de service. Cela vous permet d'appeler les opérations de service directement à partir du contexte. Pour plus d’informations, voir le blog [opérations de Service et le Client WCF Data Services](http://go.microsoft.com/fwlink/?LinkId=215668).  
  
-   Quand vous utilisez <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> pour appeler une opération de service, les caractères de la bibliothèque cliente fournis à l'objet <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> sont automatiquement mis en échappement via un encodage avec le signe % des caractères réservés, comme l'esperluette (&) et la mise en échappement des guillemets simples dans les chaînes. Toutefois, lorsque vous appelez l’une de le *Execute* méthodes pour appeler une opération de service, vous devez penser à effectuer cette opération de toutes les valeurs de chaîne fournie par l’utilisateur. Les guillemets simples des URI sont placés dans une séquence d'échappement comme guillemets doubles.  
  
## <a name="examples-of-calling-service-operations"></a>Exemples d'appel d'opérations de service  
 Cette section contient les exemples suivants sur la façon d'appeler des opérations de service à l'aide de la bibliothèque cliente [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] :  
  
-   [Appel d’Execute&lt;T&gt; pour retourner une Collection d’entités](../../../../docs/framework/data/wcf/calling-service-operations-wcf-data-services.md#ExecuteIQueryable)  
  
-   [Utilisation de CreateQuery&lt;T&gt; pour retourner une Collection d’entités](../../../../docs/framework/data/wcf/calling-service-operations-wcf-data-services.md#CreateQueryIQueryable)  
  
-   [Appel d’Execute&lt;T&gt; pour retourner une seule entité](../../../../docs/framework/data/wcf/calling-service-operations-wcf-data-services.md#ExecuteSingleEntity)  
  
-   [Appel d’Execute&lt;T&gt; pour retourner une Collection de valeurs primitives](../../../../docs/framework/data/wcf/calling-service-operations-wcf-data-services.md#ExecutePrimitiveCollection)  
  
-   [Appel d’Execute&lt;T&gt; pour retourner une seule valeur Primitive](../../../../docs/framework/data/wcf/calling-service-operations-wcf-data-services.md#ExecutePrimitiveValue)  
  
-   [Appel d’une opération de Service qui ne retourne aucune donnée](../../../../docs/framework/data/wcf/calling-service-operations-wcf-data-services.md#ExecuteVoid)  
  
-   [Appel de façon asynchrone une opération de Service](../../../../docs/framework/data/wcf/calling-service-operations-wcf-data-services.md#ExecuteAsync)  
  
<a name="ExecuteIQueryable"></a>   
### <a name="calling-executet-to-return-a-collection-of-entities"></a>Appel d’Execute\<T > pour retourner une Collection d’entités  
 L'exemple suivant appelle une opération de service nommée GetOrdersByCity, qui accepte un paramètre de chaîne `city` et retourne un <xref:System.Linq.IQueryable%601> :  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationIQueryable](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#callserviceoperationiqueryable)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationIQueryable](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#callserviceoperationiqueryable)]  
  
 Dans cet exemple, l'opération de service retourne une collection d'objets `Order` avec les objets `Order_Detail` associés.  
  
<a name="CreateQueryIQueryable"></a>   
### <a name="using-createqueryt-to-return-a-collection-of-entities"></a>Utilisation de CreateQuery\<T > pour retourner une Collection d’entités  
 L'exemple suivant utilise <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> pour retourner un <xref:System.Data.Services.Client.DataServiceQuery%601>, utilisé pour appeler la même opération de service GetOrdersByCity :  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationCreateQuery](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#callserviceoperationcreatequery)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationCreateQuery](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#callserviceoperationcreatequery)]  
  
 Dans cet exemple, la méthode <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> est utilisée pour ajouter le paramètre à la requête et la méthode <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> est utilisée pour inclure les objets Order_Details associés dans les résultats.  
  
<a name="ExecuteSingleEntity"></a>   
### <a name="calling-executet-to-return-a-single-entity"></a>Appel d’Execute\<T > pour retourner une seule entité  
 L'exemple suivant appelle une opération de service nommée GetNewestOrder, qui retourne une seule entité Order :  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationSingleEntity](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#callserviceoperationsingleentity)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationSingleEntity](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#callserviceoperationsingleentity)]  
  
 Dans cet exemple, la méthode <xref:System.Linq.Enumerable.FirstOrDefault%2A> permet de demander l'exécution d'une seule entité Order.  
  
<a name="ExecutePrimitiveCollection"></a>   
### <a name="calling-executet-to-return-a-collection-of-primitive-values"></a>Appel d’Execute\<T > pour retourner une Collection de valeurs primitives  
 L’exemple suivant appelle une opération de service qui retourne une collection de valeurs de chaîne :  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationEnumString](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#callserviceoperationenumstring)]  
  
<a name="ExecutePrimitiveValue"></a>   
### <a name="calling-executet-to-return-a-single-primitive-value"></a>Appel d’Execute\<T > pour retourner une seule valeur Primitive  
 L'exemple suivant appelle une opération de service qui retourne une valeur de chaîne unique :  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationSingleInt](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#callserviceoperationsingleint)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationSingleInt](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#callserviceoperationsingleint)]  
  
 Dans cet exemple également, la méthode <xref:System.Linq.Enumerable.FirstOrDefault%2A> permet de demander l'exécution d'une seule valeur entière.  
  
<a name="ExecuteVoid"></a>   
### <a name="calling-a-service-operation-that-returns-no-data"></a>Appel d'une opération de service qui ne retourne pas de données  
 L'exemple suivant appelle une opération de service qui ne retourne aucune donnée :  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationVoid](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#callserviceoperationvoid)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationVoid](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#callserviceoperationvoid)]  
  
 Étant donné qu'aucune donnée n'est retournée, la valeur de l'exécution n'est pas assignée. Le seul élément indiquant que la requête a réussi est qu'aucune exception <xref:System.Data.Services.Client.DataServiceQueryException> n'est levée.  
  
<a name="ExecuteAsync"></a>   
### <a name="calling-a-service-operation-asynchronously"></a>Appel d'une opération de service de façon asynchrone  
 L'exemple suivant appelle une opération de service de façon asynchrone en appelant <xref:System.Data.Services.Client.DataServiceContext.BeginExecute%2A> et <xref:System.Data.Services.Client.DataServiceContext.EndExecute%2A> :  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationAsync](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#callserviceoperationasync)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationAsync](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#callserviceoperationasync)]  
  
 [!code-csharp[Astoria Northwind Client#OnAsyncExecutionComplete](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#onasyncexecutioncomplete)]
 [!code-vb[Astoria Northwind Client#OnAsyncExecutionComplete](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#onasyncexecutioncomplete)]  
  
 Étant donné qu'aucune donnée n'est retournée, la valeur retournée par l'exécution n'est pas assignée. Le seul élément indiquant que la requête a réussi est qu'aucune exception <xref:System.Data.Services.Client.DataServiceQueryException> n'est levée.  
  
 L'exemple suivant appelle la même opération de service de façon asynchrone à l'aide de <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> :  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationQueryAsync](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#callserviceoperationqueryasync)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationQueryAsync](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#callserviceoperationqueryasync)]  
  
 [!code-csharp[Astoria Northwind Client#OnAsyncQueryExecutionComplete](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#onasyncqueryexecutioncomplete)]
 [!code-vb[Astoria Northwind Client#OnAsyncQueryExecutionComplete](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#onasyncqueryexecutioncomplete)]  
  
## <a name="see-also"></a>Voir aussi  
 [Bibliothèque cliente WCF Data Services](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
