---
title: "WebContentTypeMapper, exemple | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a4fe59e7-44d8-43c6-a1f8-40c45223adca
caps.latest.revision: 15
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 15
---
# WebContentTypeMapper, exemple
Cet exemple illustre comment mapper les nouveaux types de contenu aux formats du corps des messages [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].  
  
 L'élément <xref:System.ServiceModel.Description.WebHttpEndpoint> se connecte à l'encodeur de message Web, permettant ainsi à [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] de recevoir des messages JSON, des messages XML ou des messages binaires bruts au niveau du même point de terminaison.L'encodeur détermine le format du corps des messages en examinant le type de contenu HTTP des demandes.Cet exemple introduit la classe <xref:System.ServiceModel.Channels.WebContentTypeMapper>, laquelle permet à l'utilisateur de contrôler le mappage entre le type de contenu et le format du corps des messages.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] fournit un ensemble de mappages par défaut destinés aux types de contenu.Par exemple, les mappages `application/json` et `text/xml` permettent de mapper les messages aux formats JSON et XML respectivement.Les types de contenu qui ne sont pas mappés aux formats JSON ou XML sont mappés au format binaire brut.  
  
 Dans certaines situations \(par exemple, avec des API de type push\), les développeurs de service ne contrôlent pas le type de contenu retourné par le client.Par exemple, les clients peuvent retourner le format JSON comme `text/javascript` au lieu de retourner `application/json`.Dans ce cas de figure, le développeur de service doit fournir un type qui dérive de <xref:System.ServiceModel.Channels.WebContentTypeMapper> pour pouvoir gérer correctement ce type de contenu, tel qu'illustré dans l'exemple de code suivant.  
  
```  
public class JsonContentTypeMapper : WebContentTypeMapper  
{  
    public override WebContentFormat  
               GetMessageFormatForContentType(string contentType)  
    {  
        if (contentType == "text/javascript")  
        {  
            return WebContentFormat.Json;  
        }  
        else  
        {  
            return WebContentFormat.Default;  
        }  
    }  
}  
  
```  
  
 Ce type doit se substituer à la méthode <xref:System.ServiceModel.Channels.WebContentTypeMapper.GetMessageFormatForContentType%28System.String%29>.La méthode doit évaluer l'argument `contentType` et retourner l'une des valeurs suivantes : <xref:System.ServiceModel.Channels.WebContentFormat>, <xref:System.ServiceModel.Channels.WebContentFormat>, <xref:System.ServiceModel.Channels.WebContentFormat> ou <xref:System.ServiceModel.Channels.WebContentFormat>.Lorsque cette méthode retourne la valeur <xref:System.ServiceModel.Channels.WebContentFormat>, les mappages d'encodeur de message Web par défaut sont utilisés.Dans l'exemple de code précédent, le type de contenu `text/javascript` est mappé au format JSON. Tous les autres mappages restent, en revanche, inchangés.  
  
 Pour utiliser la classe `JsonContentTypeMapper`, utilisez ce qui suit dans votre Web.config :  
  
```  
<system.serviceModel>  
  <standardEndpoints>  
    <webHttpEndpoint>  
      <standardEndpoint name="" contentTypeMapper="Microsoft.Samples.WebContentTypeMapper.JsonContentTypeMapper, JsonContentTypeMapper, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
    </webHttpEndpoint>  
  </standardEndpoints>  
</system.serviceModel>  
```  
  
 Pour vérifier les conditions requises à l'utilisation du JsonContentTypeMapper, supprimez l'attribut contentTypeMapper du fichier de configuration ci\-dessus.La page du client ne parvient pas à se charger lorsqu'elle essaie d'utiliser `text/javascript` pour envoyer le contenu JSON.  
  
### Pour configurer, générer et exécuter l'exemple  
  
1.  Assurez\-vous d'avoir effectué la procédure figurant à la section [Procédure d'installation unique pour les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Générez la solution WebContentTypeMapperSample.sln tel qu'indiqué à la section [Génération des exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Naviguez jusqu'à http:\/\/localhost\/ServiceModelSamples\/JCTMClientPage.htm \(n'ouvrez pas JCTMClientPage.htm à l'aide d'un navigateur à partir du répertoire de projet\).  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur.Recherchez le répertoire \(par défaut\) suivant avant de continuer.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n'existe pas, rendez\-vous sur la page \(éventuellement en anglais\) des [exemples Windows Communication Foundation \(WCF\) et Windows Workflow Foundation \(WF\) pour .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples\WCF\Extensibility\Ajax\WebContentTypeMapper`  
  
## Voir aussi