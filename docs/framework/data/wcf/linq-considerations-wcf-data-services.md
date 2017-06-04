---
title: "Consid&#233;rations sur LINQ (WCF Data Services) | Microsoft Docs"
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
  - "WCF Data Services, LINQ"
  - "interroger le service de données (services de données WCF)"
  - "Services de données WCF, interrogation"
ms.assetid: cc4ec9e9-348f-42a6-a78e-1cd40e370656
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# Consid&#233;rations sur LINQ (WCF Data Services)
Cette rubrique fournit des informations sur la façon dont les requêtes LINQ sont composées et exécutées lorsque vous utilisez le client [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] et décrit les restrictions d'utilisation de LINQ pour interroger un service de données qui implémente [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)]. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]composer et exécuter des requêtes sur un [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]-service de données, consultez la page [interrogation du Service de données](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md).  
  
## <a name="composing-linq-queries"></a>Composition de requêtes LINQ  
 LINQ vous permet de composer des requêtes par rapport à une collection d’objets qui implémente <xref:System.Collections.Generic.IEnumerable%601>. Les deux le **ajouter une référence de Service** boîte de dialogue de [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] et l’outil DataSvcUtil.exe sont utilisés pour générer la représentation d’une [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] service comme une classe de conteneur d’entités qui hérite de <xref:System.Data.Services.Client.DataServiceContext>, ainsi que les objets qui représentent les entités retournées dans les flux. Ces outils génèrent également des propriétés sur la classe de conteneur d’entités des collections qui sont exposées en tant que flux par le service. Chacune de ces propriétés de la classe qui encapsule le service de données retourne un <xref:System.Data.Services.Client.DataServiceQuery%601>. Étant donné que la <xref:System.Data.Services.Client.DataServiceQuery%601> la classe implémente le <xref:System.Linq.IQueryable%601> interface définie par LINQ, vous pouvez composer une requête LINQ sur des flux exposés par le service de données, qui sont traduites par la bibliothèque cliente en une demande de requête URI qui est envoyé au service de données lors de l’exécution.  
  
> [!IMPORTANT]
>  L'ensemble de requêtes pouvant être exprimées dans la syntaxe LINQ est plus étendu que dans la syntaxe d'URI utilisée par les services de données [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]. A <xref:System.NotSupportedException> est déclenché lorsque la requête ne peut pas être mappée à un URI dans le service de données cible. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]le [des méthodes LINQ non prises en charge](../../../../docs/framework/data/wcf/linq-considerations-wcf-data-services.md#unsupportedMethods) dans cette rubrique.  
  
 L'exemple suivant est une requête LINQ qui retourne des `Orders` ayant un coût de fret supérieur à $30 et trie les résultats par date d'expédition, en commençant par la dernière :  
  
  [Astoria NorthwindClient #AddQueryOptionsLinqSpecific](../../../../amples/snippets/xml/VS_Snippets_Misc/astoria northwind service/astoria.vsmdi NorthwindClient#AddQueryOptionsLinqSpecific)]  
  
 Cette requête LINQ est traduite dans la requête URI qui est exécutée sur la station de travail Northwind [quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md) service de données :  
  
```  
http://localhost:12345/Northwind.svc/Orders?Orderby=ShippedDate&?filter=Freight gt 30  
```  
  
 Pour obtenir des informations plus générales sur LINQ, consultez [LINQ (Language-Integrated Query)](../Topic/LINQ%20\(Language-Integrated%20Query\).md).  
  
 LINQ vous permet de composer des requêtes en utilisant aussi bien la syntaxe déclarative spécifique au langage, illustrée dans l'exemple précédent, qu'un ensemble de méthodes de requête qu'on nomme opérateurs de requête standard. Une requête équivalente à l'exemple précédent peut être composée en utilisant uniquement la syntaxe reposant sur une méthode, comme illustré dans l'exemple suivant :  
  
  [Astoria NorthwindClient #AddQueryOptionsLinqExpressionSpecific](../../../../amples/snippets/xml/VS_Snippets_Misc/astoria northwind service/astoria.vsmdi NorthwindClient#AddQueryOptionsLinqExpressionSpecific)]  
  
 Le client [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] peut traduire ces deux types de requêtes composées dans un URI de requête, et vous pouvez étendre une requête LINQ en ajoutant des méthodes de requête à une expression de requête. Lorsque vous composez des requêtes LINQ en ajoutant une syntaxe de méthode à une expression de requête ou un <xref:System.Data.Services.Client.DataServiceQuery%601>, les opérations sont ajoutées à l’URI de requête dans l’ordre dans lequel les méthodes sont appelées. Cela équivaut à appeler le <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> pour ajouter chaque option de requête à l’URI de requête.  
  
## <a name="executing-linq-queries"></a>Exécution de requêtes LINQ  
 Certain LINQ méthodes de requête, tel que <xref:System.Linq.Enumerable.First%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29> ou <xref:System.Linq.Enumerable.Single%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29>, lorsqu’il est ajouté à la requête, la requête à exécuter. L'exécution de la requête est également déclenchée lorsque les résultats sont énumérés implicitement, comme lors d'une boucle `foreach` ou lorsque la requête est attribuée à une collection `List`. Pour plus d’informations, consultez [interrogation du Service de données](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md).  
  
 Le client exécute une requête LINQ en deux parties. Lorsque cela est possible, les expressions LINQ dans une requête sont d'abord évaluées sur le client, puis une requête basée surl' URI est générée et envoyée au service de données pour être évaluée par rapport aux données dans le service. Pour plus d’informations, consultez la section [Client / serveur exécution](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md#executingQueries) dans [interrogation du Service de données](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md).  
  
 Lorsqu'une requête LINQ ne peut pas être traduite dans un URI de requête compatible avec [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)], une exception est levée en cas de tentative d'exécution. Pour plus d’informations, consultez [interrogation du Service de données](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md).  
  
## <a name="linq-query-examples"></a>Exemples de requêtes LINQ  
 Les exemples des sections qui suivent illustrent les types de requêtes LINQ pouvant être exécutés sur un service [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)].  
  
<a name="filtering"></a>   
### <a name="filtering"></a>Filtrage  
 Les exemples de requêtes LINQ de cette section filtrent les données dans le flux retourné par le service.  
  
 Les exemples suivants illustrent des requêtes équivalentes qui filtrent les entités `Orders` retournées afin que seules les commandes ayant un coût de fret supérieur à $30 soient retournées :  
  
-   Utilisation de la syntaxe de requête LINQ :  
  
      [Astoria NorthwindClient #LinqWhereClauseSpecific](../../../../amples/snippets/xml/VS_Snippets_Misc/astoria northwind service/astoria.vsmdi NorthwindClient#LinqWhereClauseSpecific)]  
  
-   Utilisation des méthodes de requête LINQ :  
  
      [Astoria NorthwindClient #LinqWhereMethodSpecific](../../../../amples/snippets/xml/VS_Snippets_Misc/astoria northwind service/astoria.vsmdi NorthwindClient#LinqWhereMethodSpecific)]  
  
-   Option `$filter` de la chaîne de requête d'URI :  
  
      [Astoria NorthwindClient #ExplicitQueryWhereMethodSpecific](../../../../amples/snippets/xml/VS_Snippets_Misc/astoria northwind service/astoria.vsmdi NorthwindClient#ExplicitQueryWhereMethodSpecific)]  
  
 Tous les exemples précédents sont convertis vers l'URI de requête : `http://localhost:12345/northwind.svc/Orders()?$filter=Freight gt 30M`.  
  
<a name="sorting"></a>   
### <a name="sorting"></a>Tri  
 Les exemples suivants illustrent des requêtes équivalentes qui trient les données retournées par nom de société, code postal et ordre descendant :  
  
-   Utilisation de la syntaxe de requête LINQ :  
  
      [Astoria NorthwindClient #LinqOrderByClauseSpecific](../../../../amples/snippets/xml/VS_Snippets_Misc/astoria northwind service/astoria.vsmdi NorthwindClient#LinqOrderByClauseSpecific)]  
  
-   Utilisation des méthodes de requête LINQ :  
  
      [Astoria NorthwindClient #LinqOrderByMethodSpecific](../../../../amples/snippets/xml/VS_Snippets_Misc/astoria northwind service/astoria.vsmdi NorthwindClient#LinqOrderByMethodSpecific)]  
  
-   Option `$orderby` de la chaîne de requête d'URI :  
  
      [Astoria NorthwindClient #ExplicitQueryOrderByMethodSpecific](../../../../amples/snippets/xml/VS_Snippets_Misc/astoria northwind service/astoria.vsmdi NorthwindClient#ExplicitQueryOrderByMethodSpecific)]  
  
 Tous les exemples précédents sont convertis vers l'URI de requête : `http://localhost:12345/northwind.svc/Customers()?$orderby=CompanyName,PostalCode desc`.  
  
<a name="projection"></a>   
### <a name="projection"></a>Projection  
 Les exemples suivants illustrent des requêtes équivalentes qui projettent les données retournées dans le type plus restreint `CustomerAddress`.  
  
-   Utilisation de la syntaxe de requête LINQ :  
  
      [Astoria NorthwindClient #LinqSelectClauseSpecific](../../../../amples/snippets/xml/VS_Snippets_Misc/astoria northwind service/astoria.vsmdi NorthwindClient#LinqSelectClauseSpecific)]  
  
-   Utilisation des méthodes de requête LINQ :  
  
      [Astoria NorthwindClient #LinqSelectMethodSpecific](../../../../amples/snippets/xml/VS_Snippets_Misc/astoria northwind service/astoria.vsmdi NorthwindClient#LinqSelectMethodSpecific)]  
  
> [!NOTE]
>  Le `$select` option de requête ne peut pas être ajoutée à un URI de requête à l’aide de la <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> (méthode). Nous vous recommandons d’utiliser LINQ <xref:System.Linq.Enumerable.Select%2A> méthode que le client génère les `$select` option dans l’URI de demande de requête.\</TSource, TResult>  
  
 Les deux exemples précédents sont traduits dans l'URI de requête : `"http://localhost:12345/northwind.svc/Customers()?$filter=Country eq 'GerGerm'&$select=CustomerID,Address,City,Region,PostalCode,Country"`.  
  
<a name="paging"></a>   
### <a name="client-paging"></a>Pagination du client  
 Les exemples suivants illustrent des requêtes équivalentes qui génèrent une page d'entités de commande triées incluant 25 commandes, en ignorant les 50 premières commandes :  
  
-   Application des méthodes de requête à une requête LINQ :  
  
      [Astoria NorthwindClient #LinqSkipTakeMethodSpecific](../../../../amples/snippets/xml/VS_Snippets_Misc/astoria northwind service/astoria.vsmdi NorthwindClient#LinqSkipTakeMethodSpecific)]  
  
-   Options de chaîne de requête d'URI `$skip` et `$top` :  
  
      [Astoria NorthwindClient #ExplicitQuerySkipTakeMethodSpecific](../../../../amples/snippets/xml/VS_Snippets_Misc/astoria northwind service/astoria.vsmdi NorthwindClient#ExplicitQuerySkipTakeMethodSpecific)]  
  
 Les deux exemples précédents sont traduits dans l'URI de requête : `http://localhost:12345/northwind.svc/Orders()?$orderby=OrderDate desc&$skip=50&$top=25`.  
  
<a name="expand"></a>   
### <a name="expand"></a>Expand  
 Lorsque vous interrogez un service de données [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)], vous pouvez demander que les entités liées à l'entité cible par la requête soient incluses dans le flux retourné. Le <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> méthode est appelée sur le <xref:System.Data.Services.Client.DataServiceQuery%601> du jeu d’entités ciblé par la requête LINQ, avec l’entité associée définie nom fourni en tant que la `path` paramètre. Pour plus d’informations, consultez [le chargement différé contenu](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md).  
  
 Les exemples suivants illustrent les différentes façons d’utiliser le <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> méthode dans une requête :  
  
-   Dans la syntaxe de requête LINQ :  
  
      [Astoria NorthwindClient #LinqQueryExpandSpecific](../../../../amples/snippets/xml/VS_Snippets_Misc/astoria northwind service/astoria.vsmdi NorthwindClient#LinqQueryExpandSpecific)]  
  
-   Avec les méthodes de requête LINQ :  
  
      [Astoria NorthwindClient #LinqQueryExpandMethodSpecific](../../../../amples/snippets/xml/VS_Snippets_Misc/astoria northwind service/astoria.vsmdi NorthwindClient#LinqQueryExpandMethodSpecific)]  
  
 Les deux exemples précédents sont traduits dans l'URI de requête : `http://localhost:12345/northwind.svc/Orders()?$filter=CustomerID eq 'ALFKI'&$expand=Order_Details`.  
  
<a name="unsupportedMethods"></a>   
## <a name="unsupported-linq-methods"></a>Méthodes LINQ non prises en charge  
 Le tableau suivant répertorie les classes de méthodes LINQ qui ne sont pas prises en charge et qui ne peuvent pas être incluses dans une requête exécutée sur un service [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] :  
  
|Type d'opération|Méthode non prise en charge|  
|--------------------|------------------------|  
|Opérateurs de jeu|Tous les opérateurs de jeu sont pris en charge sur un <xref:System.Data.Services.Client.DataServiceQuery%601>, qui inclus les éléments suivants :<br /><br /> -   <xref:System.Linq.Enumerable.All%2A><br />-   <xref:System.Linq.Enumerable.Any%2A><br />-   <xref:System.Linq.Enumerable.Concat%2A><br />-   <xref:System.Linq.Enumerable.DefaultIfEmpty%2A><br />-   <xref:System.Linq.Enumerable.Distinct%2A><br />-   <xref:System.Linq.Enumerable.Except%2A><br />-   <xref:System.Linq.Enumerable.Intersect%2A><br />-   <xref:System.Linq.Enumerable.Union%2A><br />-   <xref:System.Linq.Enumerable.Zip%2A>\</TFirst, TSecond, TResult>|  
|Opérations de tri|L’opérateur de tri suivants nécessitent <xref:System.Collections.Generic.IComparer%601> sont pris en charge par rapport à un <xref:System.Data.Services.Client.DataServiceQuery%601>:<br /><br /> -   <xref:System.Linq.Enumerable.OrderBy%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%2CSystem.Collections.Generic.IComparer%7B%60%601%7D%29> </TSource, TKey> </TSource, TKey><br />-   <xref:System.Linq.Enumerable.OrderByDescending%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%2CSystem.Collections.Generic.IComparer%7B%60%601%7D%29> \</TSource, TKey> \</TSource, TKey><br />-   <xref:System.Linq.Enumerable.ThenBy%60%602%28System.Linq.IOrderedEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%2CSystem.Collections.Generic.IComparer%7B%60%601%7D%29> </TSource, TKey> </TSource, TKey><br />-   <xref:System.Linq.Enumerable.ThenByDescending%60%602%28System.Linq.IOrderedEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%2CSystem.Collections.Generic.IComparer%7B%60%601%7D%29> \</TSource, TKey> \</TSource, TKey>|  
|Opérateurs de projection et de filtrage|Les opérateurs de filtrage qui acceptent un argument positionnel projection suivante sont non pris en charge par rapport à un <xref:System.Data.Services.Client.DataServiceQuery%601>:<br /><br /> -   <xref:System.Linq.Enumerable.Join%60%604%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%2CSystem.Func%7B%60%600%2C%60%602%7D%2CSystem.Func%7B%60%601%2C%60%602%7D%2CSystem.Func%7B%60%600%2C%60%601%2C%60%603%7D%2CSystem.Collections.Generic.IEqualityComparer%7B%60%602%7D%29> </TOuter, TInner, TResult> </TInner, TKey> </TOuter, TKey> </TOuter, TInner, TKey, TResult><br />-   <xref:System.Linq.Enumerable.Select%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Int32%2C%60%601%7D%29> </TSource, Int32, TResult> </TSource, TResult><br />-   <xref:System.Linq.Enumerable.SelectMany%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%7D%29> </TSource, TResult><br />-   <xref:System.Linq.Enumerable.SelectMany%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Int32%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%7D%29> </TSource, TResult><br />-   <xref:System.Linq.Enumerable.SelectMany%60%603%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%7D%2CSystem.Func%7B%60%600%2C%60%601%2C%60%602%7D%29> \</TSource, TCollection, TResult> \</TSource, TCollection, TResult><br />-   <xref:System.Linq.Enumerable.SelectMany%60%603%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Int32%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%7D%2CSystem.Func%7B%60%600%2C%60%601%2C%60%602%7D%29> </TSource, TCollection, TResult> </TSource, TCollection, TResult><br />-   <xref:System.Linq.Enumerable.Where%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Int32%2CSystem.Boolean%7D%29> \</TSource, Int32, Boolean>|  
|Opérateurs de groupement|Tous les opérateurs de groupement sont pris en charge par rapport à un <xref:System.Data.Services.Client.DataServiceQuery%601>, y compris les éléments suivants :<br /><br /> -   <xref:System.Linq.Enumerable.GroupBy%2A>\</TSource, TKey><br />-   <xref:System.Linq.Enumerable.GroupJoin%2A>\</TOuter, TInner, TKey, TResult><br /><br /> Les opérations de groupement doivent être exécutées sur le client.|  
|Opérateurs d'agrégation|Toutes les opérations d’agrégation sont pris en charge par rapport à un <xref:System.Data.Services.Client.DataServiceQuery%601>, y compris les éléments suivants :<br /><br /> -   <xref:System.Linq.Enumerable.Aggregate%2A><br />-   <xref:System.Linq.Enumerable.Average%2A><br />-   <xref:System.Linq.Enumerable.Count%2A><br />-   <xref:System.Linq.Enumerable.LongCount%2A><br />-   <xref:System.Linq.Enumerable.Max%2A><br />-   <xref:System.Linq.Enumerable.Min%2A><br />-   <xref:System.Linq.Enumerable.Sum%2A><br /><br /> Les opérations d'agrégation doivent soit être exécutées sur le client, soit être encapsulées par une opération de service.|  
|Opérateurs de pagination|Les opérateurs de pagination suivants ne sont pas pris en charge par rapport à un <xref:System.Data.Services.Client.DataServiceQuery%601>:<br /><br /> -   <xref:System.Linq.Enumerable.ElementAt%2A><br />-   <xref:System.Linq.Enumerable.Last%2A><br />-   <xref:System.Linq.Enumerable.LastOrDefault%2A><br />-   <xref:System.Linq.Enumerable.SkipWhile%2A><br />-   <xref:System.Linq.Enumerable.TakeWhile%2A> **Remarque :** des opérateurs de pagination qui sont exécutées sur une séquence vide retournent la valeur null.|  
|Autres opérateurs|Les éléments suivants d’autres opérateurs ne sont pas pris en charge par rapport à un <xref:System.Data.Services.Client.DataServiceQuery%601>:<br /><br /> 1.  <xref:System.Linq.Enumerable.Empty%2A><br />2.  <xref:System.Linq.Enumerable.Range%2A><br />3.  <xref:System.Linq.Enumerable.Repeat%2A><br />4.  <xref:System.Linq.Enumerable.ToDictionary%2A></TSource, TKey><br />5.  <xref:System.Linq.Enumerable.ToLookup%2A>\</TSource, TKey>|  
  
<a name="supportedExpressions"></a>   
## <a name="supported-expression-functions"></a>Fonctions d'expression prises en charge  
 Les méthodes et propriétés CLR (Common-Language Runtime) suivantes sont prises en charge car elles peuvent être traduites dans une expression de requête et incluses dans l'URI de la requête exécutée sur un service [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] :  
  
|<xref:System.String> membre|Fonction [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] prise en charge|  
|-----------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------|  
|<xref:System.String.Concat%28System.String%2CSystem.String%29>|`string concat(string p0, string p1)`|  
|<xref:System.String.Contains%28System.String%29>|`bool substringof(string p0, string p1)`|  
|<xref:System.String.EndsWith%28System.String%29>|`bool endswith(string p0, string p1)`|  
|<xref:System.String.IndexOf%28System.String%2CSystem.Int32%29>|`int indexof(string p0, string p1)`|  
|<xref:System.String.Length>|`int length(string p0)`|  
|<xref:System.String.Replace%28System.String%2CSystem.String%29>|`string replace(string p0, string find, string replace)`|  
|<xref:System.String.Substring%28System.Int32%29>|`string substring(string p0, int pos)`|  
|<xref:System.String.Substring%28System.Int32%2CSystem.Int32%29>|`string substring(string p0, int pos, int length)`|  
|<xref:System.String.ToLower>|`string tolower(string p0)`|  
|<xref:System.String.ToUpper>|`string toupper(string p0)`|  
|<xref:System.String.Trim>|`string trim(string p0)`|  
  
|<xref:System.DateTime> membre<sup>1</sup>|Fonction [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] prise en charge|  
|-------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------|  
|<xref:System.DateTime.Day>|`int day(DateTime p0)`|  
|<xref:System.DateTime.Hour>|`int hour(DateTime p0)`|  
|<xref:System.DateTime.Minute>|`int minute(DateTime p0)`|  
|<xref:System.DateTime.Month>|`int month(DateTime p0)`|  
|<xref:System.DateTime.Second>|`int second(DateTime p0)`|  
|<xref:System.DateTime.Year>|`int year(DateTime p0)`|  
  
 <sup>1</sup>l’équivalent propriétés date et heure de <xref:Microsoft.VisualBasic.DateAndTime?displayProperty=fullName>, ainsi que le <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A> méthode dans Visual Basic sont également acceptés.  
  
|<xref:System.Math> membre|Fonction [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] prise en charge|  
|---------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------|  
|<xref:System.Math.Ceiling%28System.Decimal%29>|`decimal ceiling(decimal p0)`|  
|<xref:System.Math.Ceiling%28System.Double%29>|`double ceiling(double p0)`|  
|<xref:System.Math.Floor%28System.Decimal%29>|`decimal floor(decimal p0)`|  
|<xref:System.Math.Floor%28System.Double%29>|`double floor(double p0)`|  
|<xref:System.Math.Round%28System.Decimal%29>|`decimal round(decimal p0)`|  
|<xref:System.Math.Round%28System.Double%29>|`double round(double p0)`|  
  
|<xref:> System.Linq.Expressions.Expression?qualifyHint=False&autoUpgrade=True membre|Fonction [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] prise en charge|  
|---------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------|  
|<xref:System.Linq.Expressions.Expression.TypeIs%28System.Linq.Expressions.Expression%2CSystem.Type%29>|`bool isof(type p0)`|  
  
 Le client peut également être en mesure d'évaluer les fonctions CLR supplémentaires sur le client. A <xref:System.NotSupportedException> est déclenché pour toute expression qui ne peut pas être évaluée sur le client et ne peut pas être convertie en un URI de demande valide pour l’évaluation sur le serveur.  
  
## <a name="see-also"></a>Voir aussi  
 [Interrogation du Service de données](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)   
 [Projections de requête](../../../../docs/framework/data/wcf/query-projections-wcf-data-services.md)   
 [Matérialisation d’objets](../../../../docs/framework/data/wcf/object-materialization-wcf-data-services.md)   
 [OData : Conventions d’URI](http://go.microsoft.com/fwlink/?LinkID=185564)