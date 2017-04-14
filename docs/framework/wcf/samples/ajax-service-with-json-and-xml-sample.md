---
title: "AJAX Service with JSON and XML, exemple | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8ea5860d-0c42-4ae9-941a-e07efdd8e29c
caps.latest.revision: 15
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 15
---
# AJAX Service with JSON and XML, exemple
Cet exemple indique comment utiliser [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] pour créer un service AJAX \(Asynchronous JavaScript and XML\) qui retourne des données JSON \(JavaScript Object Notation\) ou XML.Vous pouvez accéder à un service AJAX en utilisant le code JavaScript à partir d'un client de navigateur Web.Cet exemple repose sur l'exemple [Basic AJAX Service](../../../../docs/framework/wcf/samples/basic-ajax-service.md).  
  
 Contrairement aux autres exemples AJAX, celui\-ci n'utilise pas ASP.NET AJAX et le contrôle <xref:System.Web.UI.ScriptManager>.Une fois configurés, les services AJAX [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sont accessibles à partir de n'importe quelle page HTML via JavaScript, et ce scénario est présenté ici.Pour obtenir un exemple d'utilisation de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] avec ASP.NET AJAX, consultez [AJAX Samples](http://msdn.microsoft.com/fr-fr/f3fa45b3-44d5-4926-8cc4-a13c30a3bf3e).  
  
 Cet exemple illustre comment commuter le type de réponse d'une opération entre JSON et XML.Cette fonctionnalité est disponible que le service soit configuré pour être accessible par ASP.NET AJAX ou par une page cliente HTML\/JavaScript.  
  
> [!NOTE]
>  La procédure d'installation ainsi que les instructions de génération correspondant à cet exemple figurent en fin de rubrique.  
  
 Pour permettre l'utilisation de clients AJAX non\-ASP.NET, utilisez <xref:System.ServiceModel.Activation.WebServiceHostFactory> \(pas <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>\) dans le fichier .svc.<xref:System.ServiceModel.Activation.WebServiceHostFactory> ajoute un point de terminaison standard <xref:System.ServiceModel.Description.WebHttpEndpoint> au service.Ce point de terminaison est configuré avec une adresse vide renvoyant au fichier .svc ; cela signifie que l'adresse du service est http:\/\/localhost\/ServiceModelSamples\/service.svc, sans autre suffixe que celui correspondant au nom de l'opération.  
  
```html  
<%@ServiceHost language="c#" Debug="true" Service="Microsoft.Samples.XmlAjaxService.CalculatorService" Factory="System.ServiceModel.Activation.WebServiceHostFactory" %>  
  
```  
  
 La section suivante dans Web.config peut être utilisée pour apporter des modifications de configuration supplémentaires au point de terminaison.Elle peut être supprimée si aucune modification supplémentaire n'est requise.  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>  
    <webHttpEndpoint>  
      <!-- Use this element to configure the endpoint -->  
      <standardEndpoint name="" />  
    </webHttpEndpoint>  
  </standardEndpoints>  
</system.serviceModel>  
  
```  
  
 Le format de données par défaut pour <xref:System.ServiceModel.Description.WebHttpEndpoint> est XML, alors que le format de données par défaut pour [for T:System.ServiceModel.Description.WebScriptEndpoint](assetId:///for T:System.ServiceModel.Description.WebScriptEndpoint?qualifyHint=False&autoUpgrade=True) est JSON.Pour plus d'informations, consultez [Création de services AJAX WCF sans ASP.NET](../../../../docs/framework/wcf/feature-details/creating-wcf-ajax-services-without-aspnet.md).  
  
 Le service présenté dans l'exemple suivant est un service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] standard avec deux opérations.Ces deux opérations requièrent le style de corps <xref:System.ServiceModel.Web.WebMessageBodyStyle> sur les attributs <xref:System.ServiceModel.Web.WebGetAttribute> ou <xref:System.ServiceModel.Web.WebInvokeAttribute>, ce qui est spécifique au comportement `webHttp` et n'a aucune incidence sur le commutateur de format de données JSON\/XML.  
  
```  
[OperationContract]  
[WebInvoke(ResponseFormat = WebMessageFormat.Xml, BodyStyle = WebMessageBodyStyle.Wrapped)]  
MathResult DoMathXml(double n1, double n2);  
```  
  
 Le format de réponse de l'opération est spécifié comme étant XML ; il s'agit du paramètre par défaut pour le comportement [\<webHttp\>](../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md).Il est toutefois conseillé de spécifier explicitement le format de réponse.  
  
 L'autre opération utilise l'attribut `WebInvokeAttribute` et spécifie explicitement JSON au lieu de XML pour la réponse.  
  
```  
[OperationContract]  
[WebInvoke(ResponseFormat = WebMessageFormat.Json, BodyStyle = WebMessageBodyStyle.Wrapped)]  
MathResult DoMathJson(double n1, double n2);  
```  
  
 Notez que dans les deux cas, les opérations retournent un type complexe, `MathResult`, lequel constitue un type de contrat de données [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] standard.  
  
 La page Web XmlAjaxClientPage.htm client contient du code JavaScript qui appelle l'une des deux opérations précédemment mentionnées lorsque l'utilisateur clique sur les boutons **Perform calculation \(return JSON\)** ou **Perform calculation \(return XML\)** dans la page.Le code permettant d'appeler le service construit un corps JSON et l'envoie à l'aide de HTTP POST.La requête est créée manuellement dans JavaScript, contrairement à l'exemple [Basic AJAX Service](../../../../docs/framework/wcf/samples/basic-ajax-service.md) et aux autres exemples utilisant ASP.NET AJAX.  
  
```  
// Create HTTP request  
var xmlHttp;  
// Request instantiation code omitted…  
// Result handler code omitted…  
  
// Build the operation URL  
var url = "service.svc/ajaxEndpoint/";  
url = url + operation;  
  
// Build the body of the JSON message  
var body = '{"n1":';  
body = body + document.getElementById("num1").value + ',"n2":';  
body = body + document.getElementById("num2").value + '}';  
  
// Send the HTTP request  
xmlHttp.open("POST", url, true);  
xmlHttp.setRequestHeader("Content-type", "application/json");  
xmlHttp.send(body);  
```  
  
 La réponse du service s'affiche sans traitement supplémentaire dans une zone de texte de la page.Cet exemple est implémenté à des fins de démonstration pour vous permettre d'observer directement les formats de données XML et JSON utilisés.  
  
```  
// Create result handler   
xmlHttp.onreadystatechange=function(){  
     if(xmlHttp.readyState == 4){  
          document.getElementById("result").value = xmlHttp.responseText;  
     }  
}  
```  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur.Recherchez le répertoire \(par défaut\) suivant avant de continuer.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n'existe pas, rendez\-vous sur la page \(éventuellement en anglais\) des [exemples Windows Communication Foundation \(WCF\) et Windows Workflow Foundation \(WF\) pour .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples\WCF\Basic\AJAX\XmlAjaxService`  
  
#### Pour configurer, générer et exécuter l'exemple  
  
1.  Assurez\-vous d'avoir effectué la [Procédure d'installation unique pour les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Générez la solution XmlAjaxService.sln comme indiqué dans la rubrique [Génération des exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Accédez à http:\/\/localhost\/ServiceModelSamples\/XmlAjaxClientPage.htm \(n'ouvrez pas XmlAjaxClientPage.htm dans le navigateur à partir du répertoire du projet\).  
  
## Voir aussi  
 [AJAX Service Using HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md)