---
title: "NetNamedPipeBinding | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
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
  - "canal nommé de profil Net"
ms.assetid: e78e845f-c325-46e2-927d-81616f97f7d5
caps.latest.revision: 34
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 34
---
# NetNamedPipeBinding
Cet exemple illustre l'utilisation de la liaison `netNamedPipeBinding`, laquelle permet la communication interprocessus sur le même ordinateur.  Les canaux nommés ne fonctionnent pas sur plusieurs ordinateurs.  Cet exemple est basé sur le service de calculatrice [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).  
  
 Dans cet exemple, le service est auto\-hébergé.  Le client et le service sont tous les deux des applications console.  
  
> [!NOTE]
>  La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.  
  
 La liaison est spécifiée dans les fichiers de configuration pour le client et le service.  Le type de liaison est indiqué dans l'attribut `binding` de l'élément [\<endpoint\>](http://msdn.microsoft.com/fr-fr/13aa23b7-2f08-4add-8dbf-a99f8127c017), tel qu'illustré dans l'exemple de configuration suivant :  
  
```  
<endpoint address="net.pipe://localhost/ServiceModelSamples/service"  
          binding="netNamedPipeBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 L'exemple précédent indique comment configurer un point de terminaison pour utiliser la liaison `netNamedPipeBinding` avec les paramètres par défaut.  Si vous souhaitez configurer la liaison `netNamedPipeBinding` et modifier certains de ses paramètres, vous devez définir une configuration de liaison.  Le point de terminaison doit référencer la configuration de liaison par nom avec un attribut `bindingConfiguration`.  
  
```  
<endpoint address="net.pipe://localhost/ServiceModelSamples/service"  
          binding="netNamedPipeBinding"  
          bindingConfiguration="Binding1"   
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 Dans cet exemple, la configuration de liaison est nommée `Binding1` et est définie comme suit.  
  
```  
<bindings>  
  <!--   
        Following is the expanded configuration section for a NetNamedPipeBinding.  
        Each property is configured with the default value.  
     -->  
  <netNamedPipeBinding>  
    <binding name="Binding1"   
             closeTimeout="00:01:00"  
             openTimeout="00:01:00"   
             receiveTimeout="00:10:00"   
             sendTimeout="00:01:00"  
             transactionFlow="false"   
             transferMode="Buffered"   
             transactionProtocol="OleTransactions"  
             hostNameComparisonMode="StrongWildcard"   
             maxBufferPoolSize="524288"  
             maxBufferSize="65536"   
             maxConnections="10"   
             maxReceivedMessageSize="65536">  
      <security mode="Transport">  
        <transport protectionLevel="EncryptAndSign" />  
      </security>  
    </binding>  
  </netNamedPipeBinding>  
</bindings>  
  
```  
  
 Lorsque vous exécutez l'exemple, les demandes et réponses d'opération s'affichent dans la fenêtre de console du client.  Appuyez sur Entrée dans la fenêtre du client pour l'arrêter.  
  
```  
  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### Pour configurer, générer et exécuter l'exemple  
  
1.  Assurez\-vous d'avoir effectué la procédure indiquée à la section [Procédure d'installation unique pour les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Pour générer l'édition C\# ou Visual Basic .NET de la solution, conformez\-vous aux instructions figurant dans [Génération des exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Pour exécuter l'exemple dans une configuration à un seul ordinateur, conformez\-vous instructions figurant dans la rubrique [Exécution des exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur.  Recherchez le répertoire \(par défaut\) suivant avant de continuer.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n'existe pas, rendez\-vous sur la page \(éventuellement en anglais\) des [exemples Windows Communication Foundation \(WCF\) et Windows Workflow Foundation \(WF\) pour .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].  Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples\WCF\Basic\Binding\Net\NamedPipe`  
  
## Voir aussi