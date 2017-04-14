---
title: "Comment&#160;: configurer un client Windows Communication Foundation de base | Microsoft Docs"
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
  - "WCF (clients WCF), configurer"
ms.assetid: d067b86d-afb0-47bf-94f6-45180a3d8d78
caps.latest.revision: 47
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 47
---
# Comment&#160;: configurer un client Windows Communication Foundation de base
Il s'agit de la cinquième des six tâches requises pour créer une application de base [!INCLUDE[indigo1](../../../includes/indigo1-md.md)].  Pour disposer d'une vue d'ensemble des six tâches, consultez la rubrique [Didacticiel de mise en route](../../../docs/framework/wcf/getting-started-tutorial.md).  
  
 Cette rubrique traite du fichier de configuration client qui a été généré à l'aide de la fonctionnalité Ajouter une référence de service de [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] ou de l'outil [Outil Service Model Metadata Tool \(Svcutil.exe\)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).  La configuration du client consiste à spécifier le point de terminaison que le client utilise pour accéder au service.  Un point de terminaison a une adresse, une liaison et un contrat et chacun de ces éléments doit être spécifié dans le processus de configuration du client.  
  
### Pour configurer un client Windows Communication Foundation  
  
1.  Ouvrez le fichier de configuration généré \(App.config\) du projet GettingStartedClient.  L'exemple suivant est une vue du fichier de configuration généré.  Sous la section [\<system.serviceModel\>](../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md), localisez l'élément [\<endpoint\>](http://msdn.microsoft.com/fr-fr/13aa23b7-2f08-4add-8dbf-a99f8127c017).  
  
    ```  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
        <startup>   
          <!-- specifies the version of WCF to use-->  
            <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.5,Profile=Client" />  
        </startup>  
        <system.serviceModel>  
            <bindings>  
                <!-- Uses wsHttpBinding-->  
                <wsHttpBinding>  
                    <binding name="WSHttpBinding_ICalculator" />  
                </wsHttpBinding>  
            </bindings>  
            <client>  
                <!-- specifies the endpoint to use when calling the service -->  
                <endpoint address="http://localhost:8000/ServiceModelSamples/Service/CalculatorService"  
                    binding="wsHttpBinding" bindingConfiguration="WSHttpBinding_ICalculator"  
                    contract="ServiceReference1.ICalculator" name="WSHttpBinding_ICalculator">  
                    <identity>  
                        <userPrincipalName value="migree@redmond.corp.microsoft.com" />  
                    </identity>  
                </endpoint>  
            </client>  
        </system.serviceModel>  
    </configuration><?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
        <startup>   
            <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.5,Profile=Client" />  
        </startup>  
        <system.serviceModel>  
            <bindings>  
                <wsHttpBinding>  
                    <binding name="WSHttpBinding_ICalculator" />  
                </wsHttpBinding>  
            </bindings>  
            <client>  
                <endpoint address="http://localhost:8000/ServiceModelSamples/Service/CalculatorService"  
                    binding="wsHttpBinding" bindingConfiguration="WSHttpBinding_ICalculator"  
                    contract="ServiceReference1.ICalculator" name="WSHttpBinding_ICalculator">  
                    <identity>  
                        <userPrincipalName value="migree@redmond.corp.microsoft.com" />  
                    </identity>  
                </endpoint>  
            </client>  
        </system.serviceModel>  
    </configuration>   
    ```  
  
     Cet exemple configure le point de terminaison que le client utilise pour accéder au service localisé à l'adresse suivante : http:\/\/localhost:8000\/ServiceModelSamples\/Service\/CalculatorService.  
  
     L'élément de point de terminaison spécifie que le contrat de service `ServiceReference1.ICalculator` est utilisé pour la communication entre le client et le service WCF.  Le canal WCF est configuré avec <xref:System.ServiceModel.WsHttpBinding> fourni par le système.  Ce contrat a été généré à l'aide de la fonctionnalité Ajouter une référence de service dans Visual Studio.  Il s'agit essentiellement d'une copie du contrat défini dans le projet GettingStartedLib.  La liaison <xref:System.ServiceModel.WsHttpBinding> spécifie le protocole HTTP pour le transport, la sécurité interopérable et d'autres détails de configuration.  
  
2.  [!INCLUDE[crabout](../../../includes/crabout-md.md)] l'utilisation du client généré avec cette configuration, consultez [Comment : Utiliser un client](../../../docs/framework/wcf/how-to-use-a-wcf-client.md).  
  
## Voir aussi  
 [Utilisation de liaisons pour configurer des services et des clients](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)   
 [Outil Service Model Metadata Tool \(Svcutil.exe\)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)   
 [Comment : créer un client](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)   
 [Getting Started](../../../docs/framework/wcf/samples/getting-started-sample.md)   
 [Self\-Host](../../../docs/framework/wcf/samples/self-host.md)