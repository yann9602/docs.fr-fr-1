---
title: "Service Debug Behavior | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9d8fd3fb-dc39-427a-8235-336a7e7162ba
caps.latest.revision: 10
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 10
---
# Service Debug Behavior
Cet exemple montre comment configurer les paramètres de comportement de débogage de service.Il est basé sur [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) qui implémente le contrat de service `ICalculator`.Cet exemple définit explicitement le comportement de débogage de service dans le fichier de configuration.Cela peut également être fait de façon impérative dans le code.  
  
 Dans cet exemple, le client est une application console \(.exe\) et le service est hébergé par les services IIS \(Internet Information Services\).  
  
> [!NOTE]
>  La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.  
  
 Le fichier Web.config du serveur définit le comportement de débogage de service permettant d'activer la page d'aide et la gestion des exceptions, tel qu'indiqué dans l'exemple suivant.  
  
```  
  
<behaviors>  
     <serviceBehaviors>  
         <behavior name="CalculatorServiceBehavior">  
         <!-- WARNING: Setting includeExceptionDetailInFaults = "True" could result in leaking secured server information to the client.-->  
         <!-- Please set this to false when deploying -->  
             <serviceDebug includeExceptionDetailInFaults="True" httpHelpPageEnabled="True"/>  
         </behavior>  
     </serviceBehaviors>  
</behaviors>  
  
```  
  
 [\<serviceDebug\>](../../../../docs/framework/configure-apps/file-schema/wcf/servicedebug.md) est l'élément de configuration qui permet de modifier les propriétés de comportement de débogage de service.L'utilisateur peut modifier ce comportement aux fins suivantes :  
  
-   Cela permet au service de retourner une exceptions levée par le code d'application même si celle\-ci n'est pas déclarée à l'aide de <xref:System.ServiceModel.FaultContractAttribute>.Pour ce faire, affectez `true` à `includeExceptionDetailInFaults`.Ce paramètre est utile lors du débogage de cas où le serveur lève une exception inattendue.  
  
    > [!IMPORTANT]
    >  Pour des raisons de sécurité, il est déconseillé d'activer ce paramètre dans un environnement de production.Une exception de serveur inattendue peut contenir des informations qui ne sont pas destinées au client et l'affectation de `true` à `includeExceptionDetailsInFaults` peut entraîner une fuite des informations.  
  
-   [\<serviceDebug\>](../../../../docs/framework/configure-apps/file-schema/wcf/servicedebug.md) permet également à un utilisateur d'activer ou de désactiver la page d'aide.Chaque service peut éventuellement exposer une page d'aide qui contient des informations sur le service, et notamment le point de terminaison permettant d'obtenir le WSDL pour le service.Pour ce faire, affectez `true` à `httpHelpPageEnabled`.Cela permet de retourner la page d'aide dans une demande GET à l'adresse de base du service.Pour modifier cette adresse, définissez un autre attribut `httpHelpPageUrl`.Pour sécuriser cette procédure, utilisez HTTPS au lieu de HTTP.Pour ce faire, définissez `httpsHelpPageEnabled` et `httpsHelpPageUrl`  
  
 Lorsque vous exécutez l'exemple, les demandes et réponses d'opération s'affichent dans la fenêtre de console cliente.Les trois premières opérations \(ajout, soustraction et multiplication\) doivent réussir.La dernière \(division\) échoue avec une exception de division par zéro.  
  
### Pour configurer, générer et exécuter l'exemple  
  
1.  Assurez\-vous d'avoir effectué la procédure indiquée dans la section [Procédure d'installation unique pour les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Pour générer l'édition C\# ou Visual Basic .NET de la solution, suivez les instructions indiquées dans [Génération des exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Pour exécuter l'exemple dans une configuration à un ou plusieurs ordinateurs, conformez\-vous aux instructions figurant dans la rubrique [Exécution des exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur.Recherchez le répertoire \(par défaut\) suivant avant de continuer.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n'existe pas, rendez\-vous sur la page \(éventuellement en anglais\) des [exemples Windows Communication Foundation \(WCF\) et Windows Workflow Foundation \(WF\) pour .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\ServiceDebug`  
  
## Voir aussi