---
title: WMI Provider
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 462f0db3-f4a4-4a4b-ac26-41fc25c670a4
caps.latest.revision: "35"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7a0a64516bea4204eb782013e718c2fa26c6024b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="wmi-provider"></a>WMI Provider
Cet exemple montre comment rassembler pendant l'exécution des données des services [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] en utilisant le fournisseur WMI (Windows Management Instrumentation) généré dans [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. Cet exemple montre également comment ajouter un objet WMI défini par l'utilisateur à un service. L’exemple active le fournisseur WMI pour les [mise en route](../../../../docs/framework/wcf/samples/getting-started-sample.md) et montre comment collecter des données à partir de la `ICalculator` service lors de l’exécution.  
  
 WMI est l'implémentation de Microsoft de la norme WBEM (Web-Based Enterprise Management). Pour plus d’informations sur le SDK WMI, consultez [Windows Management Instrumentation](https://msdn.microsoft.com/library/aa394582.aspx). WBEM est une norme d'industrie qui détermine comment les applications exposent l'instrumentation de gestion aux outils de gestion externes.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] implémente un fournisseur WMI, un composant qui expose l'instrumentation au moment de l'exécution par l'intermédiaire d'une interface WBEM compatible. Les outils de gestion peuvent se connecter aux services au moment de l'exécution par l'intermédiaire de l'interface. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] expose des attributs de services tels que les adresses, les liaisons, les comportements et les écouteurs.  
  
 Le fournisseur WMI intégré est activé dans le fichier de configuration de l'application. Cette opération est effectuée via le `wmiProviderEnabled` attribut de la [ \<diagnostics >](../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md) dans les [ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) section, comme indiqué dans l’exemple suivant configuration :  
  
```xml  
<system.serviceModel>  
    ...  
    <diagnostics wmiProviderEnabled="true" />  
    ...  
</system.serviceModel>  
```  
  
 Cette entrée de configuration expose une interface WMI. Les applications de gestion peuvent maintenant se connecter par le biais de cette interface et accéder à l'instrumentation de gestion de l'application.  
  
## <a name="custom-wmi-object"></a>Objet  WMI personnalisé.  
 L'ajout d'objets WMI à un service permet de révéler des informations définies par l'utilisateur en même temps que les informations du fournisseur WMI intégré. Cela s'effectue en publiant le schéma du service dans WMI en utilisant l'application Installutil.exe. Des instructions plus détaillées sont disponibles dans les instructions d'installation à la fin de cette rubrique.  
  
## <a name="accessing-wmi-information"></a>Accès aux informations WMI  
 Les données WMI sont accessibles de plusieurs façons différentes. Microsoft fournit des API WMI pour les scripts, les applications [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)], les applications C++ et le [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] (http://msdn.microsoft.com/library/default.asp?url=/library/wmisdk/wmi/using_wmi.asp).  
  
 Cet exemple utilise deux scripts Java : un pour énumérer des services qui s'exécutent sur l'ordinateur avec certaines de leurs propriétés et le second pour consulter les données WMI définies par l'utilisateur. Le script ouvre une connexion au fournisseur WMI, analyse les données et affiche les données rassemblées.  
  
 Démarrez l'exemple pour créer une instance en cours d'exécution d'un service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. Pendant que le service s'exécute, exécutez chaque script Java en utilisant la commande suivante dans l'invite de commandes :  
  
```  
cscript EnumerateServices.js  
```  
  
 Le script accède à l'instrumentation contenue dans le service et produit la sortie suivante :  
  
```  
Microsoft (R) Windows Script Host Version 5.6  
Copyright © Microsoft Corporation 1996-2001. All rights reserved.  
  
1 service(s) found.  
|-PID:           5776  
|-DistinguishedName:  CalculatorService@http://localhost/ServiceModelSamples/service.svc  
|-Endpoints:     1 endpoints  
  |-CalculatorService.ICalculator@http://localhost/ServiceModelSamples/service.svc  
    |-Address:                        http://localhost/ServiceModelSamples/service.svc  
    |-CounterInstanceName:  
    |-AddressHeaders:                 0  
    |-ContractType:                   Contract.Name='ICalculator'  
    |-BindingElements:                4 bindings  
      |-BindingElements[0]  
        |-Type:                       TransactionFlowBindingElement  
      |-BindingElements[1]  
        |-Type:                       SymmetricSecurityBindingElement  
      |-BindingElements[2]  
        |-Type:                       TextMessageEncodingBindingElement  
        |-MaxReadPoolSize:            64  
        |-MaxWritePoolSize:           16  
      |-BindingElements[3]  
        |-Type:                       HttpTransportBindingElement  
        |-ManualAddressing:           false  
        |-MaxBufferSize:              65536  
        |-AllowCookies:               false  
        |-AuthenticationScheme:       Anonymous  
        |-BypassProxyOnLocal:         false  
        |-HostNameComparisonMode:     StrongWildcard  
        |-ProxyAddress:               null  
        |-ProxyAuthenticationScheme:  Anonymous  
        |-Realm:  
        |-TransferMode:               Buffered  
        |-UseDefaultWebProxy:         true  
|-Behaviors:     5 behaviors  
      |-Behavior[0]  
      |-Type:                       ServiceBehaviorAttribute  
        |-AddressFilterMode:               Exact  
        |-AutomaticSessionShutdown:        true  
        |-ConcurrencyMode:                 Single  
        |-IncludeExceptionDetailInFaults:  false  
        |-InstanceContextMode:             PerSession  
        |-TransactionIsolationLevel:       Unspecified  
        |-TransactionTimeout:              null  
        |-ValidateMustUnderstand:          true  
      |-Behavior[1]  
      |-Type:                       AspNetCompatibilityRequirementsAttribute  
      |-Behavior[2]  
      |-Type:                       ServiceDebugBehavior  
      |-Behavior[3]  
      |-Type:                       ServiceAuthorizationBehavior  
      |-Behavior[4]  
      |-Type:                       Behavior  
```  
  
 Ensuite, exécutez le deuxième script Java pour afficher les données WMI définies par l'utilisateur :  
  
```  
cscript EnumerateCustomObjects.js  
```  
  
 Le script accède à l'instrumentation définie par l'utilisateur contenue dans les services et produit la sortie suivante :  
  
```  
1 WMIObject(s) found.  
|-PID:           30285bfd-9d66-4c4e-9be2-310499c5cef5  
|-InstanceId:    3839  
|-WMIInfo:       User Defined WMI Information.  
```  
  
 La sortie montre qu'un service unique s'exécute sur l'ordinateur. Le service expose un point de terminaison qui implémente le contrat `ICalculator`. Les paramètres du comportement et de la liaison qui sont implémentés par le point de terminaison sont répertoriés comme la somme des éléments individuels de la pile de messagerie.  
  
 WMI ne se limite pas à exposer l'instrumentation de gestion WMI de l'infrastructure [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. L'application peut exposer ses propres éléments de données spécifiques au domaine à travers le même mécanisme. WMI est un mécanisme unifié pour l'inspection et le contrôle d'un service Web.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple  
  
1.  Vérifiez que vous avez exécuté le [procédure d’installation d’à usage unique pour les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Publiez le schéma de services dans WMI en exécutant InstallUtil.exe (l'emplacement par défaut pour Installutil.exe est « %WINDIR%\Microsoft.NET\Framework\v4.0.30319 ») sur le fichier service.dll dans le répertoire d'hébergement. Cette étape doit seulement être exécutée lorsque des modifications ont été apportées au fichier service.dll. Pour plus d'informations, consultez Fourniture d'informations de gestion via l'instrumentation d'applications à l'adresse http://msdn.microsoft.com/fr-fr/library/ms186147.aspx dans la section « Comment : publier le schéma dans WMI pour une application instrumentée ».  
  
4.  Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [en cours d’exécution les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
    > [!NOTE]
    >  Si vous avez installé [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] après avoir installé ASP.NET, vous devrez peut-être exécuter "%WINDIR%\ Microsoft.Net\Framework\v3.0\Windows Communication Foundation\servicemodelreg.exe " -r -x pour donner l'autorisation au compte ASPNET de publier des objets WMI.  
  
5.  Consultez les données de l'exemple révélées par WMI en utilisant la commande `cscript EnumerateServices.js` ou `cscript EnumerateCustomObjects.js`.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\WMIProvider`  
  
## <a name="see-also"></a>Voir aussi  
 [Exemples d’analyse AppFabric](http://go.microsoft.com/fwlink/?LinkId=193959)
