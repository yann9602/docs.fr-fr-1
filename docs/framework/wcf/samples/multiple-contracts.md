---
title: "Multiple Contracts | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2bef319b-fe9c-4d49-ac6c-dfb23eb35099
caps.latest.revision: 14
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 14
---
# Multiple Contracts
L'exemple Multiples Contracts montre comment implémenter plusieurs contrats sur un service et comment configurer des points de terminaison pour communiquer avec chacun des contrats implémentés.Cet exemple est basé sur [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).Le service a été modifié afin de définir deux contrats, le contrat `ICalculator` et le contrat `ICalculatorSession`.  
  
> [!NOTE]
>  La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent en fin de rubrique.  
  
 La classe de service implémente à la fois les contrats `ICalculator` et `ICalculatorSession`.Vu que l'un des contrats requiert une session, le service utilise le mode d'instance <xref:System.ServiceModel.InstanceContextMode> pour maintenir l'état sur la durée de vie de la session.  
  
 La configuration du service a été modifiée afin de définir deux points de terminaison et exposer chaque contrat.Le point de terminaison `ICalculator` est exposé à l'adresse de base à l'aide d'une `basicHttpBinding`.Le point de terminaison `ICalculatorSession` est exposé à l'adresse\/la session de base à l'aide d'une `wsHttpBinding` avec l'attribut `bindingConfiguration` ayant la valeur `BindingWithSession`, comme le montre l'exemple de configuration suivant.  
  
```  
<service   
    name="Microsoft.ServiceModel.Samples.CalculatorService"  
    behaviorConfiguration="CalculatorServiceBehavior">  
  <!-- ICalculator endpoint is exposed using BasicBinding at the base  
       address provided by host:   
       http://localhost/servicemodelsamples/service.svc  -->  
  <endpoint address=""  
            binding="basicHttpBinding"  
            contract="Microsoft.ServiceModel.Samples.ICalculator" />  
  <!-- ICalculatorSession endpoint is exposed using BindingWithSession  
       at {baseaddress}/session:  
       http://localhost/servicemodelsamples/service.svc/session -->  
  <endpoint address="session"  
            binding="wsHttpBinding"  
            bindingConfiguration="BindingWithSession"   
           contract="Microsoft.ServiceModel.Samples.ICalculatorSession" />  
  ...  
</service>  
  
```  
  
 Le code client généré inclut maintenant une classe de client pour le contrat `ICalculator` d'origine et pour le nouveau contrat `ICalculatorSession`.La configuration et le code client ont été modifiés pour communiquer avec chaque contrat au point de terminaison de service approprié.  
  
 Le client est une application console Windows \(.exe\).Le service est hébergé par les services IIS \(Internet Information Services\).  
  
 La fenêtre de console cliente affiche les opérations envoyées à chacun des points de terminaison, d'abord le point de terminaison de base, puis le point de terminaison sécurisé.  
  
### Pour configurer, générer et exécuter l'exemple  
  
1.  Assurez\-vous d'avoir effectué la procédure indiquée à la section [Procédure d'installation unique pour les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Pour générer l'édition C\# ou Visual Basic .NET de la solution, suivez les instructions indiquées dans [Génération des exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Pour exécuter l'exemple dans une configuration à un ou plusieurs ordinateurs, conformez\-vous aux instructions figurant dans la rubrique [Exécution des exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur.Recherchez le répertoire \(par défaut\) suivant avant de continuer.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n'existe pas, rendez\-vous sur la page \(éventuellement en anglais\) des [exemples Windows Communication Foundation \(WCF\) et Windows Workflow Foundation \(WF\) pour .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples\WCF\Basic\Services\MultipleContracts`  
  
## Voir aussi