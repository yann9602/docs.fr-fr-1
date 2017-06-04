---
title: "Cr&#233;ation de services AJAX WCF sans ASP.NET | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ba4a7d1b-e277-4978-9f62-37684e6dc934
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# Cr&#233;ation de services AJAX WCF sans ASP.NET
Il est possible d'accéder aux services AJAX [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] à partir d'une page Web activée pour JavaScript, sans recourir à ASP.NET AJAX.  Cette rubrique décrit comment créer un service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] de ce type.  
  
 Pour obtenir des instructions sur l'utilisation de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] avec ASP.NET AJAX, consultez [Création de services WCF pour ASP.NET AJAX](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md).  
  
 La création d'un service AJAX [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] se décompose en trois parties :  
  
-   Création d'un point de terminaison AJAX accessible à partir du navigateur  
  
-   Création d'un contrat de service compatible AJAX  
  
-   Accès aux services AJAX WCF  
  
## Création d'un point de terminaison AJAX  
 La méthode la plus simple pour activer la prise en charge d'AJAX dans un service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] consiste à utiliser le <xref:System.ServiceModel.Activation.WebServiceHostFactory> dans le fichier .svc associé au service, comme l'illustre l'exemple suivant.  
  
```  
<%ServiceHost   
    language=c#  
    Debug="true"  
    Service="Microsoft.Ajax.Samples.CityService"  
    Factory=System.ServiceModel.Activation.WebServiceHostFactory  
%>  
```  
  
 Vous avez également la possibilité d'utiliser une configuration pour ajouter un point de terminaison AJAX.  Utilisez le <xref:System.ServiceModel.WebHttpBinding> sur le point de terminaison de service et configurez ce point de terminaison avec le <xref:System.ServiceModel.Description.WebHttpBehavior>, comme l'illustre l'extrait de code suivant.  
  
```  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="AjaxBehavior">  
          <webHttp/>  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
    <services>  
      <service name="Microsoft.Ajax.Samples.CityService">  
        <endpoint   
          address="ajaxEndpoint"  
          behaviorConfiguration="AjaxBehavior"  
          binding="webHttpBinding"  
          contract="Microsoft.Ajax.Samples.ICityService" />  
      </service>  
    </services>  
  </system.serviceModel>  
</configuration>  
```  
  
 Pour obtenir un exemple fonctionnel, consultez [AJAX Service with JSON and XML](../../../../docs/framework/wcf/samples/ajax-service-with-json-and-xml-sample.md).  
  
## Création d'un contrat de service compatible AJAX  
 Par défaut, les contrats de service exposés sur un point de terminaison AJAX retournent les données au format XML.  Qui plus est, les opérations de service sont, par défaut, accessibles par le biais des requêtes HTTP POST adressées aux URL qui incluent l'adresse du point de terminaison suivie du nom de l'opération, comme l'illustre l'exemple suivant.  
  
```  
[OperationContract]  
string[] GetCities(string firstLetters);  
```  
  
 Cette opération est accessible via une requête HTTP POST à `http://serviceaddress/endpointaddress/GetCities` et retourne un message XML.  
  
 Vous pouvez utiliser le modèle de programmation Web complet pour personnaliser ces aspects de base.  Par exemple, vous pouvez utiliser les attributs <xref:System.ServiceModel.Web.WebGetAttribute> ou <xref:System.ServiceModel.Web.WebInvokeAttribute> pour contrôler le verbe HTTP auquel l'opération répond, ou vous pouvez utiliser la propriété `UriTemplate` de ces attributs respectifs pour spécifier des URI personnalisés.  [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)], la rubrique [Modèle de programmation HTTP Web WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md).  
  
 Le format de données JSON est souvent utilisé dans les services AJAX.  Pour créer une opération qui retourne des données JSON au lieu de données XML, affectez <xref:System.ServiceModel.Web.WebMessageFormat> à la propriété <xref:System.ServiceModel.Web.WebGetAttribute.ResponseFormat%2A> \(ou la propriété <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A>\).  La rubrique [Sérialisation JSON autonome](../../../../docs/framework/wcf/feature-details/stand-alone-json-serialization.md) indique comment les types de contrats de données et les types .NET intégrés sont mappés au format JSON.  
  
 En principe, les demandes et les réponses JSON sont composées d'un seul élément.  Pour l'opération `GetCities` précédente, la demande ressemble à l'instruction suivante.  
  
```  
“na”  
```  
  
 La réponse à cette demande ressemble à l'instruction suivante.  
  
```  
[“Nairobi”, “Naples”, “Nashville”]  
```  
  
 Si l'opération utilise un paramètre supplémentaire, le style de demande doit être encapsulé pour encapsuler les deux paramètres dans un seul objet JSON.  L'exemple suivant illustre un message JSON de ce style.  
  
```  
{“firstLetters”: “na”, “maxNumber”: 2}  
```  
  
 Le contrat suivant accepte ce message.  
  
```  
[WebInvoke(BodyStyle=WebMessageBodyStyle.WrappedRequest, ResponseFormat=WebMessageFormat.Json)]  
[OperationContract]  
string[] GetCities(string firstLetters, int maxNumber);  
```  
  
## Accès aux services AJAX  
 Les points de terminaison AJAX [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] acceptent systématiquement les demandes XML et JSON.  
  
 Les requêtes HTTP POST avec un type de contenu « application\/json » sont traitées en tant que JSON, et celles avec un type de contenu qui indique XML \(par exemple, « texte\/xml »\) sont traitées en tant que XML.  
  
 Les requêtes HTTP GET contiennent tous les paramètres de requête dans l'URL proprement dite.  
  
 Il revient à l'utilisateur de choisir comment créer la requête HTTP au point de terminaison.  De plus, l'utilisateur dispose d'un contrôle total sur la construction du JSON qui forme le corps de la demande.  Pour obtenir un exemple de la création d'une demande à partir de JavaScript, consultez [AJAX Service with JSON and XML](../../../../docs/framework/wcf/samples/ajax-service-with-json-and-xml-sample.md).