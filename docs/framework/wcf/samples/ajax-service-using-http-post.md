---
title: "AJAX Service Using HTTP POST | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1ac80f20-ac1c-4ed1-9850-7e49569ff44e
caps.latest.revision: 28
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 28
---
# AJAX Service Using HTTP POST
Cet exemple montre comment utiliser [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] pour créer un [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] service AJAX \(JavaScript et XML asynchrones\) qui utilise HTTP POST. Un service AJAX est un service auquel vous pouvez accéder à l'aide du code Javascript de base d'un client de navigateur Web. Cet exemple repose sur l’exemple [Basic AJAX Service](../../../../docs/framework/wcf/samples/basic-ajax-service.md). La seule différence entre les deux réside dans l’utilisation de HTTP POST au lieu de HTTP GET.  
  
 La prise en charge d'AJAX dans [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] est optimisée pour permettre son utilisation avec ASP.NET AJAX via le contrôle `ScriptManager`. Pour obtenir un exemple d’utilisation de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] avec ASP.NET AJAX, consultez [Ajax Samples](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).  
  
> [!NOTE]
>  La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.  
  
 Le service dans l'exemple suivant est un service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sans code spécifique à AJAX.  
  
 Si l'attribut <xref:System.ServiceModel.Web.WebInvokeAttribute> est appliqué à une opération, ou si l'attribut <xref:System.ServiceModel.Web.WebGetAttribute> n'est pas appliqué, le verbe HTTP par défaut \(« POST »\) est utilisé. Les demandes POST sont plus difficiles à générer que les demandes GET, mais elles ne sont pas mises en cache ; utilisez des demandes POST pour toutes les opérations où la mise en cache n'est pas appropriée.  
  
```  
[ServiceContract(Namespace = "PostAjaxService")]  
    public interface ICalculator  
    {        [WebInvoke]  
        double Add(double n1, double n2);  
        //Other operations omitted…  
    }  
  
```  
  
 Créez un point de terminaison AJAX sur le service à l'aide de <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>, comme dans l'exemple de servie AJAX de base.  
  
 Contrairement aux demandes GET, vous ne pouvez pas appeler des services POST depuis le navigateur. Par exemple, le fait de naviguer jusqu’à http:\/\/localhost\/ServiceModelSamples\/service.svc\/Add?n1\=100&n2\=200 génère une erreur, car le service POST s’attend à ce que les paramètres `n1` et `n2` soient envoyés dans le corps du message \(au format JSON\) et non dans l’URL.  
  
 La page web PostAjaxClientPage.aspx du client contient le code ASP.NET pour appeler le service toutes les fois que l’utilisateur clique sur l’un des boutons d’opération de la page. Le service répond de la même façon, comme dans l’exemple [Basic AJAX Service](../../../../docs/framework/wcf/samples/basic-ajax-service.md), avec la demande GET.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire \(par défaut\) suivant avant de continuer.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation \(WCF\) and Windows Workflow Foundation \(WF\) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)]. Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples\WCF\Basic\Ajax\PostAjaxService`  
  
#### Pour configurer, générer et exécuter l'exemple  
  
1.  Assurez\-vous d’avoir suivi les instructions d’installation de la section [Procédure d'installation unique pour les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Générez la solution PostAjaxService.sln comme décrit dans la section [Génération des exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Naviguez jusqu'à http:\/\/localhost\/ServiceModelSamples\/PostAjaxClientPage.aspx \(n'ouvrez pas PostAjaxClientPage.aspx dans le navigateur depuis le répertoire du projet\).  
  
## Voir aussi