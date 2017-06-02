---
title: "Comment&#160;: configurer une liaison WS-Metadata Exchange personnalis&#233;e | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Échange de métadonnées WS [WCF]"
  - "Échange de métadonnées WS [WCF], configuration d'une liaison personnalisée"
ms.assetid: cdba4d73-da64-4805-bc56-9822becfd1e4
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# Comment&#160;: configurer une liaison WS-Metadata Exchange personnalis&#233;e
Cette rubrique explique comment configurer une liaison d'échange WS\-Metadata personnalisée.  [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] inclut quatre liaisons de métadonnées définies par le système, mais vous pouvez publier des métadonnées à l'aide de la liaison de votre choix.  Cette rubrique indique comment publier des métadonnées à l'aide du `wsHttpBinding`.  Cette liaison vous donne la possibilité d'exposer des métadonnées de manière sécurisée.  Le code dans cet article est basé sur [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).  
  
### Utilisation d'un fichier de configuration  
  
1.  Dans le fichier de configuration du service, ajoutez un comportement de service qui contient la balise `serviceMetadata` :  
  
    ```  
    <behaviors>  
       <serviceBehaviors>  
         <behavior name="CalculatorServiceBehavior">  
           <serviceMetadata httpGetEnabled="True"/>  
         </behavior>  
       </serviceBehaviors>  
    </behaviors>  
    ```  
  
2.  Ajoutez un attribut `behaviorConfiguration` à la balise de service qui référence ce nouveau comportement :  
  
    ```  
    <service        name="Microsoft.ServiceModel.Samples.CalculatorService"  
    behaviorConfiguration="CalculatorServiceBehavior">   
    ```  
  
3.  Ajoutez un point de terminaison de métadonnées qui spécifie mex comme adresse, `wsHttpBinding` comme liaison et <xref:System.ServiceModel.Description.IMetadataExchange> comme contrat :  
  
    ```  
    <endpoint address="mex"  
              binding="wsHttpBinding"  
              contract="IMetadataExchange" />  
    ```  
  
4.  Pour vérifier que le point de terminaison d'échange de métadonnées fonctionne correctement, ajoutez une balise de point de terminaison dans le fichier de configuration de client :  
  
    ```  
    <endpoint name="MyMexEndpoint"               address="http://localhost:8000/servicemodelsamples/service/mex"  
              binding="wsHttpBinding"  
              contract="IMetadataExchange"/>  
    ```  
  
5.  Dans la méthode Main\(\) du client, créez une instance <xref:System.ServiceModel.Description.MetadataExchangeClient>, affectez à sa propriété <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> la valeur `true`, appelez <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A>, puis effectuez une itération au sein de la collection de métadonnées retournée :  
  
    ```  
    string mexAddress = "http://localhost:8000/servicemodelsamples/service/mex";  
  
    MetadataExchangeClient mexClient = new MetadataExchangeClient("MyMexEndpoint");  
    mexClient.ResolveMetadataReferences = true;  
    MetadataSet mdSet = mexClient.GetMetadata(new EndpointAddress(mexAddress));  
    foreach (MetadataSection section in mdSet.MetadataSections)  
    Console.WriteLine("Metadata section: " + section.Dialect.ToString());  
    ```  
  
### Configuration par code  
  
1.  Créez une instance de liaison <xref:System.ServiceModel.WsHttpBinding> :  
  
    ```  
    WSHttpBinding binding = new WSHttpBinding();  
    ```  
  
2.  Créez une instance <xref:System.ServiceModel.ServiceHost> :  
  
    ```  
    ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService), baseAddress);  
    ```  
  
3.  Ajoutez un point de terminaison de service et ajoutez une instance <xref:System.ServiceModel.Description.ServiceMetadataBehavior> :  
  
    ```  
    serviceHost.AddServiceEndpoint(typeof(ICalculator), binding, baseAddress);  
    ServiceMetadataBehavior smb = new ServiceMetadataBehavior();  
    smb.HttpGetEnabled = true;  
    serviceHost.Description.Behaviors.Add(smb);  
    ```  
  
4.  Ajoutez un point de terminaison d'échange de métadonnées, en spécifiant le <xref:System.ServiceModel.WSHttpBinding> créé précédemment :  
  
    ```  
    serviceHost.AddServiceEndpoint(typeof(IMetadataExchange), binding, mexAddress);  
    ```  
  
5.  Pour vérifier que le point de terminaison d'échange de métadonnées fonctionne correctement, ajoutez une balise de point de terminaison dans le fichier de configuration de client :  
  
    ```  
    <endpoint name="MyMexEndpoint"               address="http://localhost:8000/servicemodelsamples/service/mex"  
              binding="wsHttpBinding"  
              contract="IMetadataExchange"/>  
    ```  
  
6.  Dans la méthode Main\(\) du client, créez une instance <xref:System.ServiceModel.Description.MetadataExchangeClient>, affectez à la propriété <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> la valeur `true`, appelez <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A>, puis effectuez une itération au sein de la collection de métadonnées retournée :  
  
    ```  
    string mexAddress = "http://localhost:8000/servicemodelsamples/service/mex";  
  
    MetadataExchangeClient mexClient = new MetadataExchangeClient("MyMexEndpoint");  
    mexClient.ResolveMetadataReferences = true;  
    MetadataSet mdSet = mexClient.GetMetadata(new EndpointAddress(mexAddress));  
    foreach (MetadataSection section in mdSet.MetadataSections)  
    Console.WriteLine("Metadata section: " + section.Dialect.ToString());  
  
    ```  
  
## Voir aussi  
 [Metadata Publishing Behavior](../../../../docs/framework/wcf/samples/metadata-publishing-behavior.md)   
 [Retrieve Metadata](../../../../docs/framework/wcf/samples/retrieve-metadata.md)   
 [Métadonnées](../../../../docs/framework/wcf/feature-details/metadata.md)   
 [Publication de métadonnées](../../../../docs/framework/wcf/feature-details/publishing-metadata.md)   
 [Publication de points de terminaison de métadonnées](../../../../docs/framework/wcf/publishing-metadata-endpoints.md)