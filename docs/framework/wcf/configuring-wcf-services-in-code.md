---
title: "Configuration de services WCF dans le code | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 193c725d-134f-4d31-a8f8-4e575233bff6
caps.latest.revision: 4
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 4
---
# Configuration de services WCF dans le code
[!INCLUDE[indigo1](../../../includes/indigo1-md.md)] permet aux développeurs de configurer des services dans les fichiers de configuration ou du code.Les fichiers de configuration sont utiles lorsqu'un service doit être configuré après avoir été déployé.Lorsqu'il utilise des fichiers de configuration, un professionnel de l'informatique doit uniquement mettre à jour le fichier de configuration, aucune recompilation n'est nécessaire.Les fichiers de configuration, toutefois, peuvent être complexes et difficiles à gérer.Il n'existe aucune prise en charge du débogage de fichiers de configuration et les éléments de configuration sont référencés par des noms. La création de fichiers de configuration est donc susceptible d'engendrer des erreurs et difficile.[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] vous permet également de configurer des services dans le code.Dans les versions antérieures de [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] \(4.0 ou version antérieure\) configurer des services dans le code était simple dans les scénarios auto\-hébergés ; la classe <xref:System.ServiceModel.ServiceHost> vous autorisait à configurer les points de terminaison et les comportements avant d'appeler ServiceHost.Open.Dans les scénarios hébergés sur le Web, toutefois, vous n'avez pas d'accès direct à la classe <xref:System.ServiceModel.ServiceHost>.Pour configurer un service hébergé sur le Web vous deviez créer un <xref:System.ServiceModel.ServiceHostFactory> qui créait le <xref:System.ServiceModel.ServiceHost> et effectuait la configuration nécessaire.Depuis le .NET 4.5, [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] offre un moyen plus simple de configurer des services auto\-hébergés et hébergés sur le Web dans le code.  
  
## Méthode Configure  
 Il suffit de définir une méthode statique publique appelée `Configure` avec la signature suivante dans votre classe d'implémentation de service :  
  
```csharp  
public static void Configure(ServiceConfiguration config)  
```  
  
 La méthode Configure prend une instance <xref:System.ServiceModel.ServiceConfiguration> qui permet au développeur d'ajouter des points de terminaison et des comportements.Cette méthode est appelée par [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] avant que l'hôte de service ne soit ouvert.S'ils sont définis, les paramètres de configuration du service spécifiés dans un fichier app.config ou web.config sont ignorés.  
  
 L'extrait de code suivant montre comment définir la méthode `Configure` et ajouter un point de terminaison de service, un comportement de point de terminaison et des comportements de service :  
  
```csharp  
public class Service1 : IService1  
    {  
        public static void Configure(ServiceConfiguration config)  
        {  
            ServiceEndpoint se = new ServiceEndpoint(new ContractDescription("IService1"), new BasicHttpBinding(), new EndpointAddress("basic"));  
            se.Behaviors.Add(new MyEndpointBehavior());  
            config.AddServiceEndpoint(se);  
  
            config.Description.Behaviors.Add(new ServiceMetadataBehavior { HttpGetEnabled = true });  
            config.Description.Behaviors.Add(new ServiceDebugBehavior { IncludeExceptionDetailInFaults = true });  
        }  
  
        public string GetData(int value)  
        {  
            return string.Format("You entered: {0}", value);  
        }  
  
        public CompositeType GetDataUsingDataContract(CompositeType composite)  
        {  
            if (composite == null)  
            {  
                throw new ArgumentNullException("composite");  
            }  
            if (composite.BoolValue)  
            {  
                composite.StringValue += "Suffix";  
            }  
            return composite;  
        }  
    }  
```  
  
 Pour activer un protocole tel que https pour un service, vous pouvez soit ajouter explicitement un point de terminaison qui utilise le protocole ou vous pouvez ajouter automatiquement des points de terminaison en appelant ServiceConfiguration.EnableProtocol \(Binding\) qui ajoute un point de terminaison pour chaque adresse de base compatible avec le protocole et chaque contrat de service défini.L'exemple de code suivant illustre l'utilisation de la méthode ServiceConfiguration.EnableProtocol :  
  
```csharp  
public class Service1 : IService1   
{   
    public string GetData(int value);   
    public static void Configure(ServiceConfiguration config)   
    {   
        // Enable “Add Service Reference” support   
       config.Description.Behaviors.Add( new ServiceMetadataBehavior { HttpGetEnabled = true });   
       // set up support for http, https, net.tcp, net.pipe   
       config.EnableProtocol(new BasicHttpBinding());   
       config.EnableProtocol(new BasicHttpBinding());   
       config.EnableProtocol(new NetTcpBinding());   
       config.EnableProtocol(new NetNamedPipeBinding());   
       // add an extra BasicHttpBinding endpoint at http:///basic   
       config.AddServiceEndpoint(typeof(IService1), new BasicHttpBinding(),"basic");   
    }   
}   
```  
  
 Les paramètres de la section \<`protocolMappings`\> sont utilisés uniquement si aucun point de terminaison de l'application n'est ajouté à <xref:System.ServiceModel.ServiceConfiguration> par programme. Vous pouvez également charger la configuration du service à partir du fichier de configuration de l'application par défaut en appelant <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration%2A>, puis modifier les paramètres.La classe <xref:System.ServiceModel.ServiceConfiguration> vous permet également de charger la configuration à partir d'une configuration centralisée.Le code suivant illustre comment implémenter :  
  
```  
public class Service1 : IService1   
{   
    public void DoWork();   
    public static void Configure(ServiceConfiguration config)   
    {   
          config.LoadFromConfiguration(ConfigurationManager.OpenMappedExeConfiguration(new ExeConfigurationFileMap { ExeConfigFilename = @"c:\sharedConfig\MyConfig.config" }, ConfigurationUserLevel.None));   
    }   
}  
  
```  
  
> [!IMPORTANT]
>  Notez que <xref:System.ServiceModel.LoadFromConfiguration%2A> ignore les paramètres \<`host`\> dans la balise \<`service`\> de \<`system.serviceModel`\>.Conceptuellement, \<`host`\> concerne la configuration de l'hôte, et non pas la configuration du service, et est chargé avant que la méthode Configure ne s'exécute.  
  
## Voir aussi  
 [Configuration des services à l'aide de fichiers de configuration](../../../docs/framework/wcf/configuring-services-using-configuration-files.md)   
 [Configuration des comportements clients](../../../docs/framework/wcf/configuring-client-behaviors.md)   
 [Configuration simplifiée](../../../docs/framework/wcf/simplified-configuration.md)   
 [Activation basée sur la configuration](../../../docs/framework/wcf/samples/configuration-based-activation.md)   
 [Configuration](../../../docs/framework/wcf/samples/configuration-sample.md)   
 [Activation basée sur la configuration dans les services IIS et WAS](../../../docs/framework/wcf/feature-details/configuration-based-activation-in-iis-and-was.md)   
 [Prise en charge de la configuration et des métadonnées](../../../docs/framework/wcf/extending/configuration-and-metadata-support.md)   
 [Configuration](../../../docs/framework/wcf/diagnostics/exceptions-reference/configuration.md)   
 [Comment : spécifier une liaison de service dans la configuration](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md)   
 [Comment : créer un point de terminaison de service dans la configuration.](../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)   
 [Comment : publier les métadonnées d'un service à l'aide d'un fichier de configuration](../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)   
 [Comment : spécifier une liaison de client dans la configuration](../../../docs/framework/wcf/how-to-specify-a-client-binding-in-configuration.md)