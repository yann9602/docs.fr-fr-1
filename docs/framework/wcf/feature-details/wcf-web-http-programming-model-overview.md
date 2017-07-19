---
title: "Vue d&#39;ensemble du mod&#232;le de programmation Web HTTP WCF | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 381fdc3a-6e6c-4890-87fe-91cca6f4b476
caps.latest.revision: 45
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 45
---
# Vue d&#39;ensemble du mod&#232;le de programmation Web HTTP WCF
Le modèle de programmation Web HTTP [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] fournit les éléments de base requis pour générer des services Web HTTP avec [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].Les services Web HTTP [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sont conçus pour être accessibles à l'éventail de clients le plus large possible \(y compris les navigateurs Web\) et ont les spécifications uniques suivantes :  
  
-   **URI et traitement des URI** Les URI jouent un rôle central dans la conception de services Web HTTP.Le modèle de programmation Web HTTP [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] utilise les classes <xref:System.UriTemplate> et <xref:System.UriTemplateTable> pour fournir des fonctions de traitement des URI.  
  
-   **Prise en charge des opérations GET et POST** Les services Web HTTP utilisent le verbe GET pour la récupération des données, en plus de divers verbes de commande pour la modification de données et l'appel distant.Le modèle de programmation Web HTTP [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] utilise <xref:System.ServiceModel.Web.WebGetAttribute> et <xref:System.ServiceModel.Web.WebInvokeAttribute> pour associer des opérations de service à la fois à GET et à d'autres verbes HTTP tels que PUT, POST et DELETE.  
  
-   **Formats de données variés** Les services de style Web traitent de nombreux types de données en plus des messages SOAP.Le modèle de programmation Web HTTP [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] utilise <xref:System.ServiceModel.WebHttpBinding> et <xref:System.ServiceModel.Description.WebHttpBehavior> pour prendre en charge de nombreux formats de données différents, y compris des documents XML, l'objet de données JSON et les flux de données de contenu binaire tels que les images, les fichiers vidéo ou le texte brut.  
  
 Le modèle de programmation Web HTTP [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] étend la portée de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] pour prendre en charge des scénarios de style Web qui incluent des services Web HTTP, AJAX et JSON et les flux de syndication \(ATOM\/RSS\).[!INCLUDE[crabout](../../../../includes/crabout-md.md)] les services AJAX et JSON, consultez [Intégration d'AJAX et prise en charge de JSON](../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md).[!INCLUDE[crabout](../../../../includes/crabout-md.md)] la syndication, consultez [Vue d'ensemble de la syndication WCF](../../../../docs/framework/wcf/feature-details/wcf-syndication-overview.md).  
  
 Il n'existe aucune restriction supplémentaire sur les types de données qui peuvent être retournées à partir d'un service Web HTTP.Tout type sérialisable peut être retourné à partir d'une opération de service WEB HTTP.Parce que les opérations de service WEB HTTP peuvent être appelées par un navigateur Web, il existe une restriction sur les types de données pouvant être spécifiées dans une URL.Pour plus d'informations sur les types de données pris en charge par défaut, consultez la section **Paramètres de chaîne de requête UriTemplate et URL** ci dessous.Le comportement par défaut peut être modifié en fournissant votre propre implémentation T:System.ServiceModel.Dispatcher.QueryStringConverter, qui indique comment convertir les paramètres spécifiés dans une URL en type de paramètre réel.[!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<xref:System.ServiceModel.Dispatcher.QueryStringConverter>  
  
> [!CAUTION]
>  Les services écrits avec le modèle de programmation Web HTTP [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] n'utilisent pas les messages SOAP.SOAP n'étant pas utilisé, les fonctions de sécurité fournies par [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ne peuvent pas l'être non plus.Toutefois, vous pouvez utiliser la sécurité basée sur le transport en hébergeant votre service avec HTTPS.[!INCLUDE[crabout](../../../../includes/crabout-md.md)][!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] la sécurité, consultez [Vue d'ensemble de la sécurité](../../../../docs/framework/wcf/feature-details/security-overview.md)  
  
> [!WARNING]
>  L'installation d'une extension WebDAV pour IIS peut entraîner les services HTTP Web à retourner une erreur HTTP 405 lorsque l'extension WebDav essaie de gérer toutes les demandes PUT.Pour contourner ce problème, vous pouvez désinstaller l'extension WebDav ou désactiver l'extension WebDav pour votre site Web.[!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][IIS et WebDav](http://learn.iis.net/page.aspx/357/webdav-for-iis-70/)  
  
## Traitement des URI avec UriTemplate et UriTemplateTable  
 Les modèles URI fournissent une syntaxe efficace pour exprimer des larges jeux d'URI dont la structure est semblable.Par exemple, le modèle suivant exprime le jeu de tous les URI à trois segments qui commencent par "a" et se terminent par "c" sans tenir compte de la valeur du segment intermédiaire : a\/{segment}\/c  
  
 Ce modèle décrit des URI comme suit :  
  
-   a\/x\/c  
  
-   a\/y\/c  
  
-   a\/z\/c  
  
-   et ainsi de suite.  
  
 Dans ce modèle, la notation avec accolade \("{segment}"\) indique un segment variable au lieu d'une valeur littérale.  
  
 le .NET Framework fournit une API sur l'utilisation des modèles d'URI appelée <xref:System.UriTemplate>.`UriTemplates` vous permet d'effectuer les opérations suivantes :  
  
-   Vous pouvez appeler une des méthodes `Bind` avec un jeu de paramètres pour produire un *URI complètement fermé* qui correspond au modèle.Cela signifie que toutes les variables dans le modèle URI sont remplacées par des valeurs réelles.  
  
-   Vous pouvez appeler `Match`\(\) avec un URI candidat qui utilise un modèle pour décomposer les parties qui constituent un URI candidat et qui retourne un dictionnaire qui contient les différentes parties de l'URI libellé selon les variables du modèle.  
  
-   `Bind`\(\) et `Match`\(\) sont des inverses qui vous permettent d'appeler `Match`\( `Bind`\(x\)\) et de revenir dans le même environnement de démarrage.  
  
 Il arrive souvent \(surtout sur le serveur où la distribution d'une demande vers une opération de service basée sur l'URI est nécessaire\) de vouloir effectuer le suivi d'un jeu d'objets <xref:System.UriTemplate> dans une structure de données qui peut adresser indépendamment chacun des modèles contenus.<xref:System.UriTemplateTable> représente un ensemble de modèles d'URI et sélectionne la meilleure correspondance en fonction d'un ensemble de modèles et d'un URI candidat.Cela n'est pas lié à une pile de réseau particulière \([!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] inclus\) vous pouvez donc l'utiliser partout quand cela est nécessaire.  
  
 Le modèle de service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] utilise <xref:System.UriTemplate> et <xref:System.UriTemplateTable> pour associer des opérations de service à un jeu d'URI décrit par un <xref:System.UriTemplate>.Une opération de service est associée à un <xref:System.UriTemplate> à l'aide de <xref:System.ServiceModel.Web.WebGetAttribute> ou de <xref:System.ServiceModel.Web.WebInvokeAttribute>.[!INCLUDE[crabout](../../../../includes/crabout-md.md)]<xref:System.UriTemplate> et <xref:System.UriTemplateTable>, consultez [UriTemplate et UriTemplateTable](../../../../docs/framework/wcf/feature-details/uritemplate-and-uritemplatetable.md)  
  
## Attributs WebGet et WebInvoke  
 Les services Web HTTP [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] utilisent des verbes de récupération \(par exemple HTTP GET\) en plus de différents verbes de commande \(par exemple HTTP POST, PUT et DELETE\).Le modèle de programmation Web HTTP [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] autorise les développeurs de service à contrôler le modèle URI et le verbe associé à leurs opérations de service avec le <xref:System.ServiceModel.Web.WebGetAttribute> et <xref:System.ServiceModel.Web.WebInvokeAttribute>.<xref:System.ServiceModel.Web.WebGetAttribute> et <xref:System.ServiceModel.Web.WebInvokeAttribute> vous permettent de contrôler comment les opérations individuelles sont attachées aux URI et les méthodes HTTP associées à ces URI.Par exemple, ajouter <xref:System.ServiceModel.Web.WebGetAttribute> et <xref:System.ServiceModel.Web.WebInvokeAttribute> dans le code suivant.  
  
```  
[ServiceContract]  
interface ICustomer  
{  
  //"View It"  
  
  [WebGet]  
  Customer GetCustomer():  
  
  //"Do It"  
    [WebInvoke]  
  Customer UpdateCustomerName( string id,   
                               string newName );  
}  
```  
  
 Le code précédent vous permet d'effectuer les requêtes HTTP suivantes.  
  
 `GET /GetCustomer`  
  
 `POST /UpdateCustomerName`  
  
 <xref:System.ServiceModel.Web.WebInvokeAttribute> prend la valeur POST par défaut mais vous pouvez l'utiliser aussi pour d'autres verbes.  
  
```  
[ServiceContract]  
interface ICustomer  
{  
  //"View It" -> HTTP GET  
    [WebGet( UriTemplate="customers/{id}" )]  
  Customer GetCustomer( string id ):  
  
  //"Do It“ -> HTTP PUT  
  [WebInvoke( UriTemplate="customers/{id}", Method="PUT" )]  
  Customer UpdateCustomer( string id, Customer newCustomer );  
}  
```  
  
 Pour obtenir un exemple complet d'un service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] qui utilise le modèle de programmation Web HTTP [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], consultez [Procédure : créer un service Web HTTP WCF de base](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-wcf-web-http-service.md)  
  
## Paramètres de chaîne de requête UriTemplate et URL  
 Les services de style Web peuvent être appelés depuis un navigateur Web en tapant une URL associée à une opération de service.Ces opérations de service peuvent accepter des paramètres de chaîne de requête qui doivent être spécifiés sous forme de chaîne dans l'URL.Le tableau suivant affiche les types qui peuvent être passés dans une URL et le format utilisé.  
  
|Type|Format|  
|----------|------------|  
|<xref:System.Byte>|0 \- 255|  
|<xref:System.SByte>|\-128 \- 127|  
|<xref:System.Int16>|\-32768 \- 32767|  
|<xref:System.Int32>|\-2,147,483,648 \- 2,147,483,647|  
|<xref:System.Int64>|\-9,223,372,036,854,775,808 \- 9,223,372,036,854,775,807|  
|<xref:System.UInt16>|0 \- 65535|  
|<xref:System.UInt32>|0 \- 4,294,967,295|  
|<xref:System.UInt64>|0 \- 18,446,744,073,709,551,615|  
|<xref:System.Single>|\-3.402823e38 \- 3.402823e38 \(la notation d'exposant n'est pas requise\)|  
|<xref:System.Double>|\-1.79769313486232e308 \- 1.79769313486232e308 \(la notation d'exposant n'est pas requise\)|  
|<xref:System.Char>|Tout caractère unique|  
|<xref:System.Decimal>|Tout décimal en notation standard \(aucun exposant\)|  
|<xref:System.Boolean>|True ou False \(ne respecte pas la casse\)|  
|<xref:System.String>|Toute chaîne \(la chaîne Null n'est pas prise en charge et aucun échappement n'est fait\)|  
|<xref:System.DateTime>|MM\/DD\/YYYY<br /><br /> MM\/DD\/YYYY HH:MM:SS \[AM&#124;PM\]<br /><br /> Mois Jour Année<br /><br /> Mois Jour Année HH:MM:SS \[AM&#124;PM\]|  
|<xref:System.TimeSpan>|DD.HH:MM:SS<br /><br /> Où DD \= jours, HH \= heures, MM \= minutes, SS \= secondes|  
|<xref:System.Guid>|Un GUID, par exemple :<br /><br /> 936DA01F\-9ABD\-4d9d\-80C7\-02AF85C822A8|  
|<xref:System.DateTimeOffset>|MM\/DD\/YYYY HH:MM:SS MM:SS<br /><br /> Où DD \= jours, HH \= heures, MM \= minutes, SS \= secondes|  
|Énumérations|La valeur d'énumération, par exemple, qui définit l'énumération comme indiqué dans le code suivant.<br /><br /> `public enum Days{ Sunday, Monday, Tuesday, Wednesday, Thursday, Friday, Saturday };`<br /><br /> Chacune des valeurs d'énumération individuelles \(ou leurs valeurs entières correspondantes\) peut être spécifiée dans la chaîne de requête.|  
|Types qui ont un `TypeConverterAttribute` pouvant convertir le type vers et depuis une représentation sous forme de chaîne.|Dépend du convertisseur de type.|  
  
## Formats et le modèle de programmation Web HTTP WCF  
 Le modèle de programmation Web HTTP [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] a de nouvelles fonctionnalités permettant d'utiliser un grand nombre de formats de données différents.Au niveau de la couche de liaison, <xref:System.ServiceModel.WebHttpBinding> peut lire et écrire les différents types suivants de données :  
  
-   XML  
  
-   JSON  
  
-   Flux binaires opaques  
  
 Cela signifie que le modèle de programmation Web HTTP [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] peut gérer tout type de données, mais vous risquez de programmer à l'encontre de <xref:System.IO.Stream>.  
  
 [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] assure la prise en charge des données JSON \(AJAX\) ainsi que des flux de syndication \(notamment ATOM et RSS\).[!INCLUDE[crabout](../../../../includes/crabout-md.md)] ces fonctionnalités, consultez [Mise en forme HTTP Web WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md)[Vue d'ensemble de la syndication WCF](../../../../docs/framework/wcf/feature-details/wcf-syndication-overview.md) et [Intégration d'AJAX et prise en charge de JSON](../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md).  
  
## Modèle de programmation Web HTTP WCF et sécurité  
 Comme le modèle de programmation Web HTTP [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ne prend pas en charge les protocoles WS\-\*, la seule manière de sécuriser un service Web HTTP [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] consiste à exposer le service via HTTPS à l'aide de SSL.[!INCLUDE[crabout](../../../../includes/crabout-md.md)] l'installation de SSL avec [!INCLUDE[iisver](../../../../includes/iisver-md.md)], consultez [Procédure : implémenter SSL dans IIS](http://go.microsoft.com/fwlink/?LinkId=131613).  
  
## Dépannage du modèle de programmation HTTP Web WCF  
 Lors de l'appel de services Web HTTP WCF à l'aide d'un <xref:System.ServiceModel.Channels.ChannelFactory%601> afin de créer un canal, le <xref:System.ServiceModel.Description.WebHttpBehavior> utilise le <xref:System.ServiceModel.EndpointAddress> défini dans le fichier de configuration même si un <xref:System.ServiceModel.EndpointAddress> différent est passé au <xref:System.ServiceModel.Channels.ChannelFactory%601>.  
  
## Voir aussi  
 [Syndication WCF](../../../../docs/framework/wcf/feature-details/wcf-syndication.md)   
 [Modèle objet de programmation Web HTTP WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-object-model.md)   
 [Modèle de programmation HTTP Web WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)