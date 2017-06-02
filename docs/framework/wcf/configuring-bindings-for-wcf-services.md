---
title: "Configuration de liaisons pour les services Windows Communication Foundation | Microsoft Docs"
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
  - "liaisons (configuration des) (WCF)"
ms.assetid: 99a85fd8-f7eb-4a84-a93e-7721b37d415c
caps.latest.revision: 36
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 36
---
# Configuration de liaisons pour les services Windows Communication Foundation
Lorsque vous créez une application, vous souhaitez souvent confier des décisions à l'administrateur après le déploiement de l'application.Par exemple, il n'existe souvent aucune façon de savoir à l'avance ce que sera une adresse de service ou un URI \(Uniform Resource Identifier\).Au lieu d'encoder de manière irréversible une adresse, il est préférable de permettre à un administrateur de le faire après avoir créé un service.Cette souplesse est obtenue par le biais de la configuration.  
  
> [!NOTE]
>  Utilisez l'[Outil Service Model Metadata Tool \(Svcutil.exe\)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) avec le commutateur `/config` pour créer rapidement des fichiers de configuration.  
  
## Sections principales  
 Le schéma de configuration [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] inclut les trois sections principales suivantes \(`serviceModel`, `bindings` et `services`\) :  
  
```  
<configuration>  
    <system.serviceModel>  
        <bindings>  
        </bindings>  
        <services>  
        </services>  
        <behaviors>  
        </behaviors>  
    </system.serviceModel>  
</configuration>  
```  
  
### Éléments ServiceModel  
 Vous pouvez utiliser la section délimitée par l'élément `system.ServiceModel` pour configurer un type de service avec un ou plusieurs points de terminaison, ainsi que les paramètres pour un service.Ensuite, chaque point de terminaison peut être configuré avec une adresse, un contrat et une liaison.\([!INCLUDE[crabout](../../../includes/crabout-md.md)] les points de terminaison, consultez [Vue d'ensemble de la création de points de terminaison](../../../docs/framework/wcf/endpoint-creation-overview.md).Si aucun point de terminaison n'est spécifié, le runtime ajoute des points de terminaison par défaut.[!INCLUDE[crabout](../../../includes/crabout-md.md)] les points de terminaison, les liaisons et les comportements par défaut, consultez [Configuration simplifiée](../../../docs/framework/wcf/simplified-configuration.md) et [Configuration simplifiée pour WCF Services](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
 Une liaison spécifie des transports \(HTTP, TCP, canaux, Message Queuing \) et des protocoles \(sécurité, fiabilité, flux de transaction\) et se compose d'éléments de liaison, dont chacun spécifie un aspect de la manière dont un point de terminaison communique avec le monde.  
  
 Par exemple, la spécification de l'élément [\<basicHttpBinding\>](../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) indique qu'il convient d'utiliser HTTP comme transport pour un point de terminaison.Cela permet de rattacher le point de terminaison au moment de l'exécution lorsque le service qui utilise ce point de terminaison est ouvert.  
  
 Il existe deux types de liaisons : les liaisons prédéfinies et les liaisons personnalisées.Les liaisons prédéfinies contiennent des combinaisons utiles d'éléments utilisés dans des scénarios courants.Pour obtenir une liste des types de liaisons prédéfinies que [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] fournit, consultez [Liaisons fournies par le système](../../../docs/framework/wcf/system-provided-bindings.md).Si aucune collection de liaison prédéfinie n'a la combinaison correcte de fonctionnalités dont une application de service a besoin, vous pouvez construire des liaisons personnalisées pour satisfaire les spécifications de l'application.[!INCLUDE[crabout](../../../includes/crabout-md.md)] les liaisons personnalisées, consultez [\<customBinding\>](../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).  
  
 Les quatre exemples ci\-dessous illustrent les configurations de liaison les plus courantes utilisées pour configurer un service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)].  
  
#### Spécification d'un point de terminaison pour utiliser un type de liaison  
 Le premier exemple montre comment spécifier un point de terminaison configuré avec une adresse, un contrat et une liaison.  
  
```  
<service name="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null">  
  <!—- This section is optional with the default configuration introduced  
       in .NET Framework 4. -->  
  <endpoint   
      address="/HelloWorld2/"  
      contract="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null"  
      binding="basicHttpBinding" />  
  </endpoint>  
</service>  
```  
  
 Dans cet exemple, l'attribut `name` indique à quel type de service la configuration est destinée.Lorsque vous créez un service dans votre code avec le contrat `HelloWorld`, il est initialisé avec tous les points de terminaison définis dans l'exemple de configuration.Si l'assembly implémente un seul contrat de service, l'attribut `name` peut être omis parce que le service utilise le seul type disponible.L'attribut utilise une chaîne, qui doit être dans le format `Namespace.Class, AssemblyName, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null`  
  
 L'attribut `address` spécifie l'URI que d'autres points de terminaison utilisent pour communiquer avec le service.L'URI peut être un chemin d'accès absolu ou relatif.Si une adresse relative est fournie, l'hôte est censé fournir une adresse de base appropriée au schéma de transport utilisé dans la liaison.Si une adresse n'est pas configurée, l'adresse de base est l'adresse pour ce point de terminaison.  
  
 L'attribut `contract` spécifie le contrat que ce point de terminaison expose.Le type d'implémentation de service doit implémenter le type de contrat.Si une implémentation de service implémente un seul type de contrat, cette propriété peut alors être omise.  
  
 L'attribut de `binding` sélectionne une liaison prédéfinie ou personnalisée à utiliser pour ce point de terminaison spécifique.Un point de terminaison qui ne sélectionne pas explicitement de liaison utilise la sélection de liaison par défaut, qui correspond à `BasicHttpBinding`.  
  
#### Modification d'une liaison prédéfinie  
 Dans l'exemple suivant, une liaison prédéfinie est modifiée.Elle peut alors être utilisée pour configurer tout point de terminaison dans le service.La liaison est modifiée en affectant 1 seconde à la valeur <xref:System.ServiceModel.Configuration.IBindingConfigurationElement.ReceiveTimeout%2A>.Notez que la propriété retourne un objet <xref:System.TimeSpan>.  
  
 Cette liaison modifiée se trouve dans la section consacrée aux liaisons.Cette liaison modifiée peut maintenant être utilisée lors de la création de tout point de terminaison en définissant l'attribut `binding` dans l'élément `endpoint`.  
  
> [!NOTE]
>  Si vous donnez un nom particulier à la liaison, le `bindingConfiguration` spécifié dans le point de terminaison du service doit lui correspondre.  
  
```  
<service name="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null">  
  <endpoint   
      address="/HelloWorld2/"  
      contract="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null"  
      binding="basicHttpBinding" />  
  </endpoint>  
</service>  
<bindings>  
    <basicHttpBinding   
        receiveTimeout="00:00:01"  
    />  
</bindings>  
```  
  
## Configuration d'un comportement à appliquer à un service  
 Dans l'exemple ci\-dessous, un comportement spécifique est configuré pour le type de service.L'élément `ServiceMetadataBehavior` est utilisé pour permettre à l'[Outil Service Model Metadata Tool \(Svcutil.exe\)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) d'interroger le service et de générer des documents WSDL \(Web Services Description Language\) à partir des métadonnées.  
  
> [!NOTE]
>  Si vous donnez un nom particulier au comportement, le `behaviorConfiguration` spécifié dans la section du point de terminaison ou du service doit lui correspondre.  
  
```  
<behaviors>  
    <behavior>  
        <ServiceMetadata httpGetEnabled="true" />   
    </behavior>  
</behaviors>  
<services>  
    <service   
       name="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null"  
       <endpoint   
          address="http://computer:8080/Hello"  
          contract="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null"  
          binding="basicHttpBinding" />  
       </endpoint>  
    </service>  
</services>  
```  
  
 La configuration précédente permet à un client d'appeler et d'obtenir les métadonnées du service typé « HelloWorld ».  
  
 `svcutil /config:Client.exe.config http://computer:8080/Hello?wsdl`  
  
## Spécification d'un service avec deux points de terminaison qui utilisent des valeurs de liaison différentes  
 Dans ce dernier exemple, deux points de terminaison sont configurés pour le type de service `HelloWorld`.Chaque point de terminaison utilise un attribut `bindingConfiguration` personnalisé différent du même type de liaison \(chacun modifie `basicHttpBinding`\).  
  
```  
<service name="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null">  
    <endpoint  
        address="http://computer:8080/Hello1"  
        contract="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null"  
        binding="basicHttpBinding"  
        bindingConfiguration="shortTimeout"  
    </endpoint>  
    <endpoint  
        address="http://computer:8080/Hello2"  
        contract="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null"  
        binding="basicHttpBinding"  
        bindingConfiguration="Secure"  
     </endpoint>  
</service>  
<bindings>  
    <basicHttpBinding   
        name="shortTimeout"  
        timeout="00:00:00:01"   
     />  
     <basicHttpBinding   
        name="Secure" />  
        <Security mode="Transport" />  
</bindings>  
```  
  
 Vous pouvez obtenir le même comportement à l'aide de la configuration par défaut en ajoutant une section `protocolMapping` et en configurant les liaisons comme illustré dans l'exemple suivant.  
  
```xml  
<protocolMapping>  
    <add scheme=”http” binding=”basicHttpBinding” bindingConfiguration=”shortTimeout” />  
    <add scheme=”https” binding=”basicHttpBinding” bindingConfiguration=”Secure” />  
</protocolMapping>  
<bindings>  
    <basicHttpBinding   
        name="shortTimeout"  
        timeout="00:00:00:01"   
     />  
     <basicHttpBinding   
        name="Secure" />  
        <Security mode="Transport" />  
</bindings>  
```  
  
## Voir aussi  
 [Configuration simplifiée](../../../docs/framework/wcf/simplified-configuration.md)   
 [Liaisons fournies par le système](../../../docs/framework/wcf/system-provided-bindings.md)   
 [Vue d'ensemble de la création de points de terminaison](../../../docs/framework/wcf/endpoint-creation-overview.md)   
 [Utilisation de liaisons pour configurer des services et des clients](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)