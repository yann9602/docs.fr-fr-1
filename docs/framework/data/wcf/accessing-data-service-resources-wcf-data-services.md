---
title: "Acc&#232;s aux ressources de service de donn&#233;es (WCF Data Services) | Microsoft Docs"
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
  - "mise en route, Services de données WCF"
  - "interrogation du service de données [WCF Data Service]"
  - "Services de données WCF, accès aux données"
  - "Services de données WCF, mise en route"
  - "Services de données WCF, interroger"
ms.assetid: 9665ff5b-3e3a-495d-bf83-d531d5d060ed
caps.latest.revision: 3
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# Acc&#232;s aux ressources de service de donn&#233;es (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] prend en charge le protocole [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] pour exposer vos données sous forme de flux avec des ressources adressables par des URI.  Ces ressources sont représentées selon les conventions relation\-entité de l'[Entity Data Model](../../../../docs/framework/data/adonet/entity-data-model.md).  Dans ce modèle, les entités représentent des unités opérationnelles de données qui sont des types de données dans un domaine d'application, par exemple les clients, ordres, éléments et produits.  Les données d'entité sont accessibles et modifiées au moyen de la sémantique REST \(Representational State Transfer\), en particulier les verbes HTTP standard GET, PUT, POST et DELETE.  
  
## Adressage des ressources  
 Dans [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)], vous adressez toutes les données exposées par le modèle de données à l'aide d'un URI.  Par exemple, l'URI suivant retourne un flux qui est le jeu d'entités Customers, lequel contient des entrées pour toutes les instances du type d'entité Customers :  
  
```  
http://services.odata.org/Northwind/Northwind.svc/Customers  
```  
  
 Les entités ont des propriétés spéciales appelées des clés d'entité.  Une clé d'entité est utilisée pour identifier uniquement une entité unique dans un jeu d'entités.  Cela vous permet d'adresser une instance spécifique d'un type d'entité dans le jeu d'entités.  Par exemple, l'URI suivant retourne une entrée pour une instance spécifique du type d'entité Customer dont la valeur de clé est `ALFKI`:  
  
```  
http://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')  
```  
  
 Les propriétés primitives et complexes d'une instance d'entité peuvent également être adressées individuellement.  Par exemple, l'URI suivant retourne un élément XML qui contient la valeur de propriété `ContactName` pour un client spécifique :  
  
```  
http://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')/ContactName  
```  
  
 Lorsque vous incluez le point de terminaison `$value` dans l'URI précédent, seule la valeur de la propriété primitive est retournée dans le message de réponse.  L'exemple suivant retourne uniquement la chaîne « Maria Anders » sans l'élément XML :  
  
```  
http://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')/ContactName/$value  
```  
  
 Les associations définissent dans le modèle de données les relations entre les entités.  Ces associations vous permettent d'adresser des jeux d'entités connexes à l'aide des propriétés de navigation d'une instance d'entité.  Une propriété de navigation peut soit retourner une entité connexe unique, dans le cas d'une relation plusieurs\-à\-un, soit un jeu d'entités connexes, dans le cas d'une relation un\-à\-plusieurs.  Par exemple, l'URI suivant retourne un flux qui constitue le jeu de toutes les commandes associées à un client spécifique :  
  
```  
http://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')/Orders  
```  
  
 Les relations, qui sont habituellement bidirectionnelles, sont représentées par une paire de propriétés de navigation.  Inversement à la relation de l'exemple précédent, l'URI suivant retourne une référence à l'entité Customer à laquelle appartient une entité Order spécifique :  
  
```  
http://services.odata.org/Northwind/Northwind.svc/Orders(10643)/Customer  
```  
  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] vous permet également d'adresser des ressources selon les résultats d'expressions de requête.  Cela permet de filtrer des jeux de ressources en fonction d'une expression évaluée.  Par exemple, l'URI suivant filtre les ressources pour retourner uniquement les ordres du client spécifié expédiés depuis le 22 septembre 1997 :  
  
```  
http://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')/Orders?$filter=ShippedDate gt datetime'1997-09-22T00:00:00'  
```  
  
 Pour plus d'informations, consultez [OData : conventions pour les URI](http://go.microsoft.com/fwlink/?LinkId=185564).  
  
## Option de requête système  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] définit un jeu d'options de requêtes système que vous pouvez utiliser pour effectuer des opérations de requête classiques d'après des ressources, comme le filtrage, le tri ou la pagination.  Par exemple, l'URI suivant retourne le jeu de toutes les entités `Order`, avec les entités `Order_Detail` connexes dont les codes postaux ne se terminent pas par `100` :  
  
```  
http://services.odata.org/Northwind/Northwind.svc/Orders?$filter=not endswith(ShipPostalCode,'100')&$expand=Order_Details&$orderby=ShipCity  
```  
  
 Les entrées du flux retourné sont également classées selon la valeur de la propriété ShipCity des commandes.  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] prend en charge les options de requêtes système [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] suivantes :  
  
|Option de requête|Description|  
|-----------------------|-----------------|  
|`$orderby`|Définit un ordre de tri par défaut pour les entités du flux retourné.  La requête suivante classe le flux des clients retournés par comté et ville :<br /><br /> `http://services.odata.org/Northwind/Northwind.svc/Customers?$orderby=Country,City`<br /><br /> Pour plus d'informations, consultez [OData : option de requête système OrderBy \($orderby\)](http://go.microsoft.com/fwlink/?LinkId=186968).|  
|`$top`|Spécifie le nombre d'entités à inclure dans le flux retourné.  L'exemple suivant ignore les 10 premiers clients, puis retourne les 10 suivants :<br /><br /> `http://services.odata.org/Northwind/Northwind.svc/Customers?$skip=10&$top=10`<br /><br /> Pour plus d'informations, consultez [OData : option de requête système Top \($top\)](http://go.microsoft.com/fwlink/?LinkId=186969).|  
|`$skip`|Spécifie le nombre d'entités à ignorer avant de commencer à retourner des entités dans le flux.  L'exemple suivant ignore les 10 premiers clients, puis retourne les 10 suivants :<br /><br /> `http://services.odata.org/Northwind/Northwind.svc/Customers?$skip=10&$top=10`<br /><br /> Pour plus d'informations, consultez [OData : option de requête système Skip \($skip\)](http://go.microsoft.com/fwlink/?LinkId=186971).|  
|`$filter`|Définit une expression qui filtre les entités retournées dans le flux selon des critères spécifiques.  Cette option de requête prend en charge un jeu d'opérateurs logiques de comparaison, d'opérateurs arithmétiques et de fonctions de requête prédéfinies utilisés pour évaluer l'expression de filtre.  L'exemple suivant retourne toutes les commandes dont les codes postaux ne se terminent pas par 100 :<br /><br /> `http://services.odata.org/Northwind/Northwind.svc/Orders?$filter=not endswith(ShipPostalCode,'100')`<br /><br /> Pour plus d'informations, consultez [OData : option de requête système Filter \($filter\)](http://go.microsoft.com/fwlink/?LinkId=186972).|  
|`$expand`|Spécifie les entités connexes retournées par la requête.  Les entités connexes sont incluses comme un flux ou comme une entrée inline avec l'entité retournée par la requête.  L'exemple suivant retourne la commande du client « ALFKI » avec le détail des articles de chaque commande :<br /><br /> `http://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')/Orders?$expand=Order_Details`<br /><br /> Pour plus d'informations, consultez [OData : option de requête système Expand \($expand\)](http://go.microsoft.com/fwlink/?LinkId=186973).|  
|`$select`|Spécifie une projection qui définit les propriétés de l'entité retournées dans la projection.  Par défaut, toutes les propriétés d'une entité sont retournées dans un flux.  La requête suivante retourne uniquement trois propriétés de l'entité `Customer` :<br /><br /> `http://services.odata.org/Northwind/Northwind.svc/Customers?$select=CustomerID,CompanyName,City`<br /><br /> Pour plus d'informations, consultez [OData : option de requête système Select \($select\)](http://go.microsoft.com/fwlink/?LinkId=186076).|  
|`$inlinecount`|Demande qu'un décompte du nombre d'entités retournées dans le flux soit inclus avec le flux.  Pour plus d'informations, consultez [OData : option de requête système Inlinecount \($inlinecount\)](http://go.microsoft.com/fwlink/?LinkId=186975).|  
  
## Adressage de relations  
 En plus d'adresser des jeux d'entités et des instances d'entité, [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] vous permet d'adresser les associations qui représentent des relations entre des entités.  Cette fonctionnalité est nécessaire pour créer ou modifier une relation entre deux instances d'entité, telles que l'expéditeur associé à un ordre donné dans l'exemple de base de données Northwind.  [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] prend en charge un opérateur `$link` pour adresser spécifiquement les associations entre des entités.  Par exemple, l'URI suivant est spécifié dans un message de demande HTTP PUT pour remplacer l'expéditeur pour l'ordre spécifié par un nouvel expéditeur.  
  
```  
http://services.odata.org/Northwind/Northwind.svc/Orders(10643)/$links/Shipper  
```  
  
 Pour plus d'informations, consultez [OData : adressage des liens entre des entrées](http://go.microsoft.com/fwlink/?LinkId=187351).  
  
## Consommation du flux retourné  
 L'URI d'une ressource [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] vous permet d'adresser des données d'entité exposées par le service.  Lorsque vous entrez un URI dans le champ d'adresse d'un navigateur Web, une représentation du flux [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] de la ressource demandée est retournée.  Pour plus d'informations, consultez la rubrique [Démarrage rapide WCF Data Services](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  Même si un navigateur Web peut être utile pour vérifier qu'une ressource du service de données retourne les données attendues, les services de données de production qui peuvent également créer, mettre à jour et supprimer les données sont généralement accessibles via le code d'application ou les langages de script d'une page Web.  Pour plus d'informations, consultez [Utilisation d'un service de données dans une application cliente](../../../../docs/framework/data/wcf/using-a-data-service-in-a-client-application-wcf-data-services.md).  
  
## Voir aussi  
 [Site web du protocole Open Data](http://go.microsoft.com/fwlink/?LinkID=182204)