---
title: "Didacticiel de mise en route | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "mise en route (WCF)"
  - "WCF [WCF], mise en route"
  - "Windows Communication Foundation [WCF], mise en route"
ms.assetid: df939177-73cb-4440-bd95-092a421516a1
caps.latest.revision: 47
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 47
---
# Didacticiel de mise en route
Les rubriques contenues dans cette section visent à vous donner un aperçu de la programmation de [!INCLUDE[indigo1](../../../includes/indigo1-md.md)].  Elles doivent être parcourues dans l'ordre de la liste indiquée au bas de cette rubrique.  En suivant ce didacticiel, vous aurez une compréhension de base des étapes requises pour créer un service et des applications clientes [!INCLUDE[indigo2](../../../includes/indigo2-md.md)].  Un service expose un ou plusieurs points de terminaison, chaque point de terminaison exposant une ou plusieurs opérations de service.  Le *point de terminaison* d'un service spécifie une adresse d'emplacement du service, une liaison qui contient les informations qu'un client doit utiliser pour communiquer avec le service, ainsi qu'un contrat qui définit les fonctionnalités fournies par le service à ses clients.  
  
 Une fois que vous aurez terminé la séquence de rubriques de ce didacticiel, vous disposerez d'un service opérationnel et d'un client qui appelle le service.  Les trois premières rubriques décrivent comment définir un contrat de service, comment implémenter le contrat de service et comment héberger le service.  Le service créé est auto\-hébergé dans une application console.  Les services peuvent également être hébergés sous IIS \(Internet Information Services\).  [!INCLUDE[crabout](../../../includes/crabout-md.md)] la procédure à suivre, consultez [Comment : héberger un service WCF dans IIS](../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md).  Le service est configuré dans le code ; toutefois, les services peuvent également être configurés dans un fichier de configuration.  [!INCLUDE[crabout](../../../includes/crabout-md.md)] l'utilisation d'un fichier de configuration, consultez [Configuration des services à l'aide de fichiers de configuration](../../../docs/framework/wcf/configuring-services-using-configuration-files.md).  
  
 Les trois rubriques suivantes décrivent comment créer un proxy client, comment configurer l'application cliente et comment utiliser le proxy client pour appeler l'opération de service exposée par le service.  Les services publient les métadonnées qui définissent les informations dont une application cliente a besoin pour communiquer avec le service.  [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] automatise le processus d'accès à ces métadonnées et l'utilise pour créer et configurer l'application cliente pour le service.  Si vous n'utilisez pas [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)], vous pouvez utiliser [Outil Service Model Metadata Tool \(Svcutil.exe\)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) pour créer et configurer l'application cliente pour le service.  
  
 Toutes les rubriques de cette section partent du principe que vous utilisez Visual Studio 2011 comme environnement de développement.  Si vous utilisez un autre environnement de développement, ignorez les instructions spécifiques à [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)].  
  
> [!NOTE]
>  Si vous exécutez [!INCLUDE[wv](../../../includes/wv-md.md)] ou des versions ultérieures du système d'exploitation Windows, vous devez démarrer [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)] en sélectionnant le menu Démarrer, en cliquant avec le bouton droit sur Microsoft Visual Studio 2011 et en sélectionnant **Exécuter en tant qu'administrateur**.  Pour toujours lancer Visual Studio 2011 en tant qu'administrateur, vous pouvez créer un raccourci, cliquer dessus avec le bouton droit, sélectionnez successivement Propriétés et l'onglet **Compatibilité**, puis cochez l'option **Exécuter ce programme en tant qu'administrateur**.  Lorsque vous démarrez Visual Studio 2011 à partir de ce raccourci, l'application s'exécute systématiquement en tant qu'administrateur.  
  
 Pour les exemples d'applications téléchargeables et exécutables sur votre disque dur, consultez les rubriques dans [Windows Communication Foundation Samples](http://msdn.microsoft.com/fr-fr/8ec9d192-5d81-4f64-bfd3-90c5e5858c91).  Pour cette rubrique, voyez notamment [Getting Started](../../../docs/framework/wcf/samples/getting-started-sample.md).  
  
 Pour des informations plus détaillées sur la création des services et des clients, consultez [Programmation WCF de base](../../../docs/framework/wcf/basic-wcf-programming.md).  
  
## Dans cette section  
 [Comment : définir un contrat de service](../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md)  
 Décrit comment créer un contrat [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] à l'aide d'une interface définie par l'utilisateur.  Le contrat définit les fonctionnalités exposées par le service.  
  
 [Comment : implémenter un contrat de service](../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md)  
 Décrit comment implémenter un contrat de service.  Une fois qu'un contrat est défini, il doit être implémenté avec une classe de service.  
  
 [Comment : héberger et exécuter un service de base](../../../docs/framework/wcf/how-to-host-and-run-a-basic-wcf-service.md)  
 Décrit comment configurer un point de terminaison pour le service dans du code et comment héberger le service dans une application console.  Pour qu'il devienne actif, un service doit être configuré et hébergé dans un environnement d'exécution.  Cet environnement crée le service et contrôle son contexte et sa durée de vie.  
  
 [Comment : créer un client](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)  
 Décrit comment extraire les métadonnées utilisées pour créer un proxy client [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] à partir d'un service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)].  Ce processus utilise la fonctionnalité Ajouter une référence de service dans Visual Studio 2011.  
  
 [Comment : configurer un client](../../../docs/framework/wcf/how-to-configure-a-basic-wcf-client.md)  
 Décrit comment configurer un client WCF. La configuration du client nécessite la spécification du point de terminaison que le client utilise pour accéder au service.  
  
 [Comment : Utiliser un client](../../../docs/framework/wcf/how-to-use-a-wcf-client.md)  
 Décrit comment utiliser le proxy client [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] pour appeler des opérations de service.  
  
## Référence  
 <xref:System.ServiceModel.ServiceContractAttribute>  
  
 <xref:System.ServiceModel.OperationContractAttribute>  
  
## Rubriques connexes  
 [Windows Communication Foundation Samples](http://msdn.microsoft.com/fr-fr/8ec9d192-5d81-4f64-bfd3-90c5e5858c91)  
  
 [Cycle de vie de la programmation de base](../../../docs/framework/wcf/basic-programming-lifecycle.md)  
  
## Voir aussi  
 [Vue d'ensemble conceptuelle](../../../docs/framework/wcf/conceptual-overview.md)   
 [Guide de la documentation](../../../docs/framework/wcf/guide-to-the-documentation.md)   
 [Présentation de Windows Communication Foundation](../../../docs/framework/wcf/whats-wcf.md)   
 [Informations détaillées sur les fonctionnalités de WCF](../../../docs/framework/wcf/feature-details/index.md)