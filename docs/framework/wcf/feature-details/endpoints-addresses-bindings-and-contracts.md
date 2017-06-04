---
title: "Points de terminaison&#160;: adresses, liaisons et contrats | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "points de terminaison (WCF)"
  - "WCF (WCF), points de terminaison"
  - "Windows Communication Foundation (WCF), points de terminaison"
ms.assetid: 9ddc46ee-1883-4291-9926-28848c57e858
caps.latest.revision: 14
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 14
---
# Points de terminaison&#160;: adresses, liaisons et contrats
Toute communication avec un service [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] se produit par l'intermédiaire des *points de terminaison* du service.Les points de terminaison fournissent aux clients l'accès aux fonctionnalités offertes par un service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
 Chaque point de terminaison se compose de quatre propriétés :  
  
-   Une adresse qui indique où rechercher le point de terminaison.  
  
-   Une liaison qui spécifie comment un client peut communiquer avec le point de terminaison.  
  
-   Un contrat qui identifie les opérations disponibles.  
  
-   L'ensemble des comportements qui spécifient les détails d'implémentation locaux du point de terminaison.  
  
 Cette rubrique traite de cette structure de point de terminaison et explique comment elle est représenté dans le modèle objet [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
## Structure d'un point de terminaison  
 Chaque point de terminaison comprend les éléments suivants :  
  
-   Adresse : l'adresse identifie le point de terminaison de manière unique et indique aux consommateurs potentiels l'emplacement du service.Elle est représentée dans le modèle objet [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] par la classe <xref:System.ServiceModel.EndpointAddress>.Une classe <xref:System.ServiceModel.EndpointAddress> contient :  
  
    -   Une propriété <xref:System.ServiceModel.EndpointAddress.Uri%2A>, qui représente l'adresse du service.  
  
    -   Une propriété <xref:System.ServiceModel.EndpointAddress.Identity%2A> qui représente l'identité de sécurité du service et une collection d'en\-tête de message facultatifs.Les en\-têtes de message facultatifs sont utilisés pour fournir des informations d'adressage supplémentaires et plus détaillées afin d'identifier le point de terminaison ou d'interagir avec lui.  
  
     [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [Spécification d'une adresse de point de terminaison](../../../../docs/framework/wcf/specifying-an-endpoint-address.md).  
  
-   Liaison : la liaison spécifie le mode de communication avec le point de terminaison.Cela inclut :  
  
    -   Le protocole de transport à utiliser \(par exemple, TCP ou HTTP\).  
  
    -   L'encodage à utiliser pour les messages \(par exemple, texte ou binaire\).  
  
    -   Les conditions de sécurité nécessaires \(par exemple, SSL ou la sécurité des messages SOAP\).  
  
     [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [Vue d'ensemble des liaisons WCF](../../../../docs/framework/wcf/bindings-overview.md).Une liaison est représentée dans le modèle objet [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] par la classe de base abstraite <xref:System.ServiceModel.Channels.Binding>.Pour la plupart des scénarios, les utilisateurs peuvent utiliser l'une des liaisons fournies par le système.Pour plus d'informations, consultez [Liaisons fournies par le système](../../../../docs/framework/wcf/system-provided-bindings.md).  
  
-   Contrats : le contrat de service définit les fonctionnalités que le point de terminaison expose au client.Un contrat spécifie :  
  
    -   Quelles opérations peuvent être appelées par un client.  
  
    -   Le format du message.  
  
    -   Le type de paramètres d'entrée ou les données requis pour appeler l'opération.  
  
    -   Le type de traitement ou le message de réponse que le client peut attendre.  
  
     Pour plus d'informations sur la définition d'un contrat, consultez [Conception de contrats de service](../../../../docs/framework/wcf/designing-service-contracts.md).  
  
-   Comportements : vous pouvez utiliser des comportements de point de terminaison pour personnaliser le comportement local du point de terminaison du service.Les comportements de point de terminaison accomplissent ceci en participant au processus de génération d'une exécution [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].Un exemple de comportement de point de terminaison est la propriété <xref:System.ServiceModel.Description.ServiceEndpoint.ListenUri%2A> qui vous permet de spécifier une adresse d'écoute différente de l'adresse SOAP ou WSDL \(Web Services Description Language\).[!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][ClientViaBehavior](../../../../docs/framework/wcf/diagnostics/wmi/clientviabehavior.md).  
  
## Définition des points de terminaison  
 L'adresse du point de terminaison pour un service peut être spécifiée de manière impérative en utilisant le code ou de façon déclarative par la configuration.[!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Comment : créer un point de terminaison de service dans la configuration.](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md) et [Comment : créer un point de terminaison de service dans le code](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md).  
  
## Dans cette section  
 Cette section explique à quoi servent les liaisons, les points de terminaison et les adresses, indique comment configurer une liaison et un point de terminaison et montre comment utiliser le comportement `ClientVia` et la propriété `ListenUri`.  
  
 [adresses](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md)  
 Décrit comment les points de terminaison sont adressés dans [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
 [Liaisons](../../../../docs/framework/wcf/feature-details/bindings.md)  
 Décrit comment les liaisons sont utilisées pour spécifier le transport, l'encodage et les détails de protocole requis pour que les clients et les services puissent communiquer l'un l'autre.  
  
 [Contrats](../../../../docs/framework/wcf/feature-details/contracts.md)  
 Décrit comment les contrats définissent les méthodes d'un service.  
  
 [Comment : créer un point de terminaison de service dans la configuration.](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)  
 Décrit comment créer un point de terminaison de service dans la configuration.  
  
 [Comment : créer un point de terminaison de service dans le code](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md)  
 Décrit comment créer un point de terminaison de service dans le code.  
  
 [Comment : utiliser Svcutil.exe pour valider le code de service compilé](../../../../docs/framework/wcf/feature-details/how-to-use-svcutil-exe-to-validate-compiled-service-code.md)  
 Décrit comment détecter les erreurs dans les implémentations et les configurations d'un service sans héberger le service, à l'aide de [Outil Service Model Metadata Tool \(Svcutil.exe\)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).  
  
## Voir aussi  
 [Configuration des services](../../../../docs/framework/wcf/configuring-services.md)   
 [Extension de liaisons](../../../../docs/framework/wcf/extending/extending-bindings.md)