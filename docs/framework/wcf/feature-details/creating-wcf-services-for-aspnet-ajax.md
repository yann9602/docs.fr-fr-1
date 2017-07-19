---
title: "Cr&#233;ation de services WCF pour ASP.NET AJAX | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 04c0402c-e617-4ba5-aedf-d17692234776
caps.latest.revision: 18
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 18
---
# Cr&#233;ation de services WCF pour ASP.NET AJAX
Microsoft ASP.NET AJAX permet de créer rapidement des pages Web d'une grande interaction pour l'utilisateur avec des éléments d'interface utilisateur réactifs et familiers.Les fonctionnalités ASP.NET AJAX fournissent des bibliothèques de client de script qui incorporent des scripts ECMAScript \(JavaScript\) et des technologies Dynamic HTML \(DHTML\) compatibles entre navigateurs ainsi qu'une intégration avec la plate\-forme de développement serveur ASP.NET 2.0.Grâce à ASP.NET AJAX, vous pouvez améliorer l'expérience utilisateur et l'efficacité de vos applications Web.  
  
 ASP.NET AJAX se compose de bibliothèques de client de script et des composants serveur intégrés destinés à fournir une infrastructure de développement fiable.Pour accéder à un service à partir d'une page ASP.NET : une fois que l'URL de service est ajoutée au contrôle de gestionnaire de script ASP.NET dans la page, les opérations de service peuvent être appelées à l'aide du code Javascript qui est identique à un appel de fonction JavaScript régulier.Consultez [Présentation d'ASP.NET AJAX](http://go.microsoft.com/fwlink/?LinkId=186475) \(page éventuellement en anglais\) sur l'utilisation des services Web dans l'infrastructure AJAX.  
  
 La plupart des services [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] peuvent être exposés en tant que service compatible avec ASP.NET AJAX en ajoutant un point de terminaison ASP.NET AJAX approprié.  
  
 Si vous utilisez Visual Studio, vous pouvez utiliser un modèle prégénéré pour les services WCF compatibles AJAX, disponible dans la boîte de dialogue **Ajouter un nouvel élément** lorsque vous utilisez des sites Web ASP.NET ou des applications Web.  
  
 Si vous n'utilisez pas les modèles Visual Studio, vous pouvez créer un point de terminaison ASP.NET AJAX de deux manières :  
  
-   Créez le point de terminaison à l'aide de l'activation d'hôte dynamique sans utiliser de configuration.Il s'agit de l'approche la plus simple si vous n'êtes pas familier avec le système de configuration WCF.[!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Comment : ajouter un point de terminaison AJAX ASP.NET sans utiliser de configuration](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md).  
  
-   Ajoutez un point de terminaison compatible AJAX à un service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] à l'aide de la configuration.[!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Comment : utiliser la configuration pour ajouter un point de terminaison AJAX ASP.NET](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md).  
  
 Le modèle de programmation Web décrit dans la section [Vue d'ensemble du modèle de programmation Web HTTP WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md) peut être utilisé avec les services ASP.NET AJAX.Plus précisément :  
  
-   Vous pouvez utiliser les attributs <xref:System.ServiceModel.Web.WebGetAttribute> et <xref:System.ServiceModel.Web.WebInvokeAttribute> pour choisir entre les verbes HTTP GET et HTTP POST.Correctement utilisés, ils permettent d'améliorer considérablement la performance de votre application.[!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Comment : choisir entre des demandes HTTP POST et HTTP GET pour des points de terminaison AJAX ASP.NET](../../../../docs/framework/wcf/feature-details/http-post-and-http-get-requests-for-aspnet-ajax-endpoints.md).  
  
-   Vous pouvez utiliser les propriétés <xref:System.ServiceModel.Web.WebGetAttribute.ResponseFormat%2A> et <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A> pour que votre service retourne des données XML au lieu du format JSON \(JavaScript Object Notation\) par défaut.Effectuée dans le cadre de l'infrastructure ASP.NET AJAX, cette opération permet au client JavaScript de recevoir un objet XML DOM.  
  
    > [!WARNING]
    >  Votre opération doit affecter au type de contenu la valeur texte\/xml pour y parvenir.Sinon, le client JavaScript recevra une chaîne contenant le XML au lieu d'un objet XML DOM.  
  
     Voici un exemple d'opération qui retourne les données XML avec le type de contenu défini convenablement :  
  
    ```  
    [OperationContract, WebGet(ResponseFormat=WebMessageFormat.Xml)]  
    public XElement GetData()  
    {  
    XElement x;  
    //Get some data here...  
  
    WebOperationContext.Current.OutgoingResponse.ContentType = "text/xml";      
    return x;  
    }  
  
    ```  
  
-   Aucune autre propriété sur les attributs <xref:System.ServiceModel.Web.WebGetAttribute> et <xref:System.ServiceModel.Web.WebInvokeAttribute> ne peut être modifiée si la compatibilité avec ASP.NET AJAX est requise.Il est possible de faire appel à d'autres aspects du modèle de programmation Web tant que les conventions d'appel ASP.NET AJAX sont respectées.  
  
 D'autres scénarios avancés requièrent la prise en compte de certains détails supplémentaires pour la prise en charge d'AJAX dans [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] :  
  
-   Pour comprendre la manière dont les données sont transférées entre un client de page AJAX et un service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] à l'aide du JavaScript, et pour plus d'informations sur la façon dont les types .NET Framework sont mappés aux types JavaScript, consultez [Prise en charge du format JSON et d'autres formats de transfert de données](../../../../docs/framework/wcf/feature-details/support-for-json-and-other-data-transfer-formats.md).  
  
-   Pour tirer parti des fonctionnalités ASP.NET, par exemple, l'authentification basée sur URL et l'accès aux informations de session ASP.NET, vous pouvez activer le mode de compatibilité ASP.NET par la configuration.  
  
 Les points de terminaison AJAX dans [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] peuvent être consommés même sans l'infrastructure ASP.NET AJAX.Cette procédure exige une connaissance du fonctionnement de l'architecture de prise en charge d'AJAX dans [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].Pour une discussion sur cette architecture, consultez [Modèle objet de programmation Web HTTP WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-object-model.md).Pour un exemple de code qui illustre cette approche, consultez [AJAX Service with JSON and XML](../../../../docs/framework/wcf/samples/ajax-service-with-json-and-xml-sample.md).  
  
## Voir aussi  
 [Modèle de programmation HTTP Web WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)   
 [Comment : ajouter un point de terminaison AJAX ASP.NET sans utiliser de configuration](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md)   
 [Comment : utiliser la configuration pour ajouter un point de terminaison AJAX ASP.NET](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md)   
 [Comment : choisir entre des demandes HTTP POST et HTTP GET pour des points de terminaison AJAX ASP.NET](../../../../docs/framework/wcf/feature-details/http-post-and-http-get-requests-for-aspnet-ajax-endpoints.md)