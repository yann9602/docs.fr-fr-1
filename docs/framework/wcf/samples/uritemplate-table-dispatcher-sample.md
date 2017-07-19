---
title: "UriTemplate Table Dispatcher, exemple | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3b32975d-ba90-4c5c-83bc-2fbb48f11c0c
caps.latest.revision: 11
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 11
---
# UriTemplate Table Dispatcher, exemple
La classe <xref:System.UriTemplateTable> fournit une structure de table associative de type dictionnaire pour utiliser un ensemble d'instances de <xref:System.UriTemplate>.Cet exemple illustre un moteur de distribution de base construit à l'aide d'`UriTemplateTable`, un scénario d'utilisation commun pour la classe `UriTemplateTable`.  
  
 Cet exemple illustre les concepts clés suivants pour la classe `UriTemplateTable` :  
  
-   Association de délégués à des `UriTemplates` dans une `UriTemplateTable`.  
  
-   Utilisation de <xref:System.UriTemplateTable.MatchSingle%2A> pour obtenir le délégué de gestionnaire correct pour un URI particulier.  
  
-   Appel du délégué de gestionnaire pour traiter la requête.  
  
### Pour configurer, générer et exécuter l'exemple  
  
1.  Pour générer l'édition C\# ou Visual Basic .NET de la solution, suivez les instructions indiquées dans [Génération des exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
2.  Pour exécuter l'exemple dans une configuration à un ou plusieurs ordinateurs, conformez\-vous aux instructions figurant dans la rubrique [Exécution des exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur.Recherchez le répertoire \(par défaut\) suivant avant de continuer.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n'existe pas, rendez\-vous sur la page \(éventuellement en anglais\) des [exemples Windows Communication Foundation \(WCF\) et Windows Workflow Foundation \(WF\) pour .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples\WCF\Basic\Web\UriTemplateDispatcher`  
  
## Voir aussi  
 [UriTemplate Table](../../../../docs/framework/wcf/samples/uritemplate-table-sample.md)   
 [UriTemplate](../../../../docs/framework/wcf/samples/uritemplate-sample.md)