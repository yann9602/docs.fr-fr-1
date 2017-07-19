---
title: "AJAX Service Using Complex Types, exemple | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 88242b99-4811-4cbe-8201-52ddf48fb174
caps.latest.revision: 16
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 16
---
# AJAX Service Using Complex Types, exemple
Cet exemple montre comment utiliser [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] pour créer un service AJAX \(ASP.NET Asynchronous JavaScript and XML\) qui créent des instances de types complexes et les envoient entre le service et le client au format JSON \(JavaScript Object Notation\).Vous pouvez accéder à un service AJAX en utilisant le code JavaScript à partir d'un client de navigateur Web.Cet exemple repose sur l'exemple [Basic AJAX Service](../../../../docs/framework/wcf/samples/basic-ajax-service.md).  
  
 La prise en charge d'AJAX dans [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] est optimisée pour permettre son utilisation avec AJAX ASP.NET via le contrôle <xref:System.Web.UI.ScriptManager>.Pour obtenir un exemple d'utilisation de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] avec ASP.NET AJAX, consultez [AJAX Samples](http://msdn.microsoft.com/fr-fr/f3fa45b3-44d5-4926-8cc4-a13c30a3bf3e).  
  
> [!NOTE]
>  La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.  
  
 Le service dans l'exemple suivant est un service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sans code spécifique à AJAX.L'attribut <xref:System.ServiceModel.Web.WebGetAttribute> n'étant pas appliqué, le verbe HTTP par défaut \("POST"\) est utilisé.Le service a une opération appelée `DoMath` qui retourne un type complexe appelé `MathResult`.Le type complexe est un type de contrat de données standard qui ne contient pas non plus de code spécifique à AJAX.  
  
```  
[DataContract]  
    public class MathResult  
    {  
        [DataMember]  
        public double sum;  
        [DataMember]  
        public double difference;  
        [DataMember]  
        public double product;  
        [DataMember]  
        public double quotient;  
    }  
```  
  
 Créez un point de terminaison AJAX sur le service à l'aide de <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>, comme dans l'exemple de servie AJAX de base.  
  
 La page Web client ComplexTypeClientPage.aspx contient du code ASP.NET et JavaScript pour appeler le service lorsque l'utilisateur clique sur le bouton **Perform calculation** dans la page.Le code permettant d'appeler le service construit un corps JSON et l'envoie à l'aide de HTTP POST, comme dans l'exemple [AJAX Service Using HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).  
  
 Une fois l'appel de service réussi, vous pouvez accéder aux membres de données individuels \(`sum`, `difference`, `product` et `quotient`\) sur l'objet JavaScript résultant.  
  
```  
function onSuccess(mathResult){  
     document.getElementById("sum").value = mathResult.sum;  
     document.getElementById("difference").value = mathResult.difference;  
     document.getElementById("product").value = mathResult.product;  
     document.getElementById("quotient").value = mathResult.quotient;  
}  
  
```  
  
### Pour configurer, générer et exécuter l'exemple  
  
1.  Assurez\-vous d'avoir effectué la procédure indiquée dans la section [Procédure d'installation unique pour les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Générez la solution ComplexTypeAjaxService.sln tel qu'indiqué dans [Génération des exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Naviguez jusqu'à http:\/\/localhost\/ServiceModelSamples\/ComplexTypeClientPage.aspx \(n'ouvrez pas ComplexTypeClientPage.aspx dans le navigateur depuis le répertoire du projet\).  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur.Recherchez le répertoire \(par défaut\) suivant avant de continuer.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n'existe pas, rendez\-vous sur la page \(éventuellement en anglais\) des [exemples Windows Communication Foundation \(WCF\) et Windows Workflow Foundation \(WF\) pour .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples\WCF\Basic\Ajax\ComplexTypeAjaxService`  
  
## Voir aussi  
 [Basic AJAX Service](../../../../docs/framework/wcf/samples/basic-ajax-service.md)