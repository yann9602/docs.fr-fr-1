---
title: "Utilisation de JSONP | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f386718c-b4ba-4931-a610-40c27a46672a
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# Utilisation de JSONP
JSON Padding \(JSONP\) est un mécanisme qui active la prise en charge de scripts entre sites dans les navigateurs Web.  JSONP repose sur la capacité des navigateurs Web à charger des scripts à partir d'un site différent de celui d'où a été extrait le document chargé en cours.  Le mécanisme fonctionne en remplissant la charge utile du format JSON par un nom de fonction de rappel défini par l'utilisateur, comme indiqué dans l'exemple suivant.  
  
```  
callback({"a" = \"b\" });  
```  
  
 Dans l'exemple précédent la charge utile JSON, `{"a" = \"b\"}`, est encapsulée dans un appel de fonction, `callback`.  La fonction de rappel doit déjà être définie dans la page Web actuelle.  Le type de contenu d'une réponse JSONP est « application\/javascript ».  
  
## Utilisation de JSONP  
 JSONP n'est pas activé automatiquement.  Pour l'activer, affectez à l'attribut `javascriptCallbackEnabled` la valeur `true` sur l'un des points de terminaison standard HTTP \(<xref:System.ServiceModel.Description.WebHttpEndpoint> ou <xref:System.ServiceModel.Description.WebScriptEndpoint>\), comme le montre l'exemple suivant.  
  
```xml  
<system.serviceModel>  
    <standardEndpoints>  
      <webHttpEndpoint>  
        <standardEndpoint name="" javascriptCallbackEnabled="true"/>  
      </webHttpEndpoint>  
    </standardEndpoints>     
  </system.serviceModel>  
```  
  
 Le nom de la fonction de rappel peut être spécifié dans une variable de requête nommée rappel, comme indiqué dans l'URL suivante.  
  
```  
http://baseaddress/Service/RestService?callback=functionName  
```  
  
 En cas d'appel, le service envoie une réponse similaire à celle\-ci.  
  
```jscript  
functionName({"root":"Something});  
```  
  
 Vous pouvez également spécifier le nom de la fonction de rappel en appliquant l'objet <xref:System.ServiceModel.Web.JavascriptCallbackBehaviorAttribute> à la classe de service, comme indiqué dans l'exemple suivant.  
  
```csharp  
[ServiceContract]  
[JavascriptCallbackBehavior(ParameterName = "$callback")]  
public class Service1  
{  
    [OperationContract]  
    [WebGet(ResponseFormat=WebMessageFormat.Json)]  
    public string GetData()  
    {              
    }  
}  
```  
  
 Pour le service illustré précédemment, une demande se présente comme suit.  
  
```  
http://baseaddress/Service/RestService?$callback=anotherFunction  
```  
  
 En cas d'appel, le service répond comme suit.  
  
```  
anotherFunction ({"root":"Something});  
```  
  
## Codes d'état HTTP  
 Les réponses JSONP avec des codes d'état HTTP différents de 200 incluent un deuxième paramètre avec la représentation numérique du code d'état HTTP, comme indiqué dans l'exemple suivant.  
  
```  
anotherFunction ({"root":"Something}, 201);  
```  
  
## Validations  
 Les validations suivantes sont effectuées lorsque JSONP est activé :  
  
-   L'infrastructure WCF lève une exception si `javascriptCallback` est activé, un paramètre de chaîne de requête de rappel est présent dans la demande et le format de réponse est défini sur JSON.  
  
-   Si la demande contient le paramètre de chaîne de requête de rappel mais que l'opération n'est pas HTTP GET, le paramètre de rappel est ignoré.  
  
-   Si le nom de rappel est `null` ou une chaîne vide, la réponse n'est pas mise au format JSONP.  
  
## Voir aussi  
 [Vue d'ensemble du modèle de programmation Web HTTP WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md)