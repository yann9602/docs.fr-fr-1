---
title: "&lt;serviceMetadata&gt; | Microsoft Docs"
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
ms.assetid: 2b4c3b4c-31d4-4908-a9b7-5bb411c221f2
caps.latest.revision: 28
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 28
---
# &lt;serviceMetadata&gt;
Spécifie la publication de métadonnées de service et des informations associées.  
  
## Syntaxe  
  
```  
  
<serviceMetadata   
    externalMetadataLocation="String"  
    httpGetBinding=”String”  
    httpGetBindingConfiguration=”String”  
    httpGetEnabled="Boolean"   
    httpGetUrl="String"  
    httpsGetBinding=”String”  
    httpsGetBindingConfiguration=”String”  
    httpsGetEnabled="Boolean"   
    httpsGetUrl="String"  
    policyVersion="Policy12/Policy15"/>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|externalMetadataLocation|Uri contenant l'emplacement d'un fichier WSDL renvoyé à l'utilisateur en réponse aux demandes WSDL et MEX au lieu du WSDL généré automatiquement.  Lorsque cet attribut n'est pas défini, le WSDL par défaut est renvoyé.  La valeur par défaut est une chaîne vide.|  
|httpGetBinding|Chaîne qui spécifie le type de la liaison qui sera utilisée pour la récupération de métadonnées via HTTP GET.  Ce paramètre est facultatif.  En l'absence de spécification, les liaisons par défaut seront utilisées.<br /><br /> La prise en charge n'est assurée que pour les liaisons comportant des éléments de liaison internes qui prennent en charge <xref:System.ServiceModel.Channels.IReplyChannel>.  En outre, la propriété <xref:System.ServiceModel.Channels.MessageVersion%2A> de la liaison doit être <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.|  
|httpGetBindingConfiguration|Chaîne qui définit le nom de la liaison spécifiée dans l'attribut `httpGetBinding`, qui fait référence aux informations de configuration supplémentaires de cette liaison.  Le même nom doit être défini dans la section `<bindings>`.|  
|httpGetEnabled|Valeur booléenne indiquant si les métadonnées de service correspondant à la récupération doivent être publiées à l'aide d'une demande HTTP\/Get.  La valeur par défaut est `false`.<br /><br /> Si l'attribut httpGetUrl n'est pas spécifié, l'adresse utilisée pour publier les métadonnées est celle du service à laquelle est ajouté le suffixe « ? wsdl ».  Par exemple, si l'adresse du service est "http:\/\/localhost:8080\/CalculatorService", l'adresse des métadonnées HTTP\/Get est "http:\/\/localhost:8080\/CalculatorService?wsdl".<br /><br /> Si cette propriété a la valeur `false` ou si l'adresse du service n'est pas basée sur le protocole HTTP ou HTTPS, le suffixe « ? wsdl » n'est pas pris en compte.|  
|httpGetUrl|URI indiquant l'adresse utilisée pour publier les métadonnées correspondant à la récupération à l'aide d'une demande HTTP\/Get.  Si l'URI relatif est spécifié, il sera traité comme étant relatif à l'adresse de base du service.|  
|httpsGetBinding|Chaîne qui spécifie le type de la liaison qui sera utilisée pour la récupération de métadonnées via HTTPS GET.  Ce paramètre est facultatif.  En l'absence de spécification, les liaisons par défaut seront utilisées.<br /><br /> La prise en charge n'est assurée que pour les liaisons comportant des éléments de liaison internes qui prennent en charge <xref:System.ServiceModel.Channels.IReplyChannel>.  En outre, la propriété <xref:System.ServiceModel.Channels.MessageVersion%2A> de la liaison doit être <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.|  
|httpsGetBindingConfiguration|Chaîne qui définit le nom de la liaison spécifiée dans l'attribut `httpsGetBinding`, qui fait référence aux informations de configuration supplémentaires de cette liaison.  Le même nom doit être défini dans la section `<bindings>`.|  
|httpsGetEnabled|Valeur booléenne indiquant si les métadonnées de service correspondant à la récupération doivent être publiées à l'aide d'une demande HTTPS\/Get.  La valeur par défaut est `false`.<br /><br /> Si l'attribut httpsGetUrl n'est pas spécifié, l'adresse utilisée pour publier les métadonnées est celle du service à laquelle est ajouté le suffixe « ? wsdl ».  Par exemple, si l'adresse du service est "https:\/\/localhost:8080\/CalculatorService", l'adresse des métadonnées HTTP\/Get est "https:\/\/localhost:8080\/CalculatorService?wsdl".<br /><br /> Si cette propriété a la valeur `false` ou si l'adresse du service n'est pas basée sur le protocole HTTP ou HTTPS, le suffixe « ? wsdl » n'est pas pris en compte.|  
|httpsGetUrl|URI indiquant l'adresse utilisée pour publier les métadonnées afin d'effectuer une récupération à l'aide d'une demande HTTPS\/Get.|  
|policyVersion|Chaîne indiquant la version de la spécification WS\-Policy utilisée.  Cet attribut est de type <xref:System.ServiceModel.Description.PolicyVersion>.|  
  
### Éléments enfants  
 None  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<comportement\>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Spécifie un élément de comportement.|  
  
## Notes  
 Cet élément de configuration permet de contrôler les métadonnées qui publient les fonctionnalités d'un service.  Pour empêcher la divulgation involontaire de métadonnées de service potentiellement sensibles, la publication de métadonnées est désactivée par défaut dans la configuration des services [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)].  Ce comportement est sécurisé par défaut, mais il signifie également que vous ne pouvez pas utiliser d'outil d'importation de métadonnées \(tel que Svcutil.exe\) pour générer le code client requis pour appeler le service, à moins que le comportement de publication des métadonnées du service soit activé explicitement dans la configuration.  À l'aide de cet élément de configuration, vous pouvez activer ce comportement de publication pour votre service.  
  
 Pour consulter un exemple de code détaillé configurant ce comportement, consultez [Metadata Publishing Behavior](../../../../../docs/framework/wcf/samples/metadata-publishing-behavior.md).  
  
 Les attributs facultatifs `httpGetBinding` et `httpsGetBinding` vous permettent de configurer les liaisons utilisées pour la récupération de métadonnées via HTTP GET \(ou HTTPS GET\).  S'ils ne sont pas spécifiés, les liaisons par défaut \(`HttpTransportBindingElement` dans le cas de HTTP et `HttpsTransportBindingElement` dans le cas de HTTPS\) sont utilisées pour la récupération des métadonnées.  Notez que vous ne pouvez pas utiliser ces attributs avec les liaisons WCF intégrées.  La prise en charge n'est assurée que pour les liaisons comportant des éléments de liaison internes qui prennent en charge <xref:System.ServiceModel.Channels.IReplyChannel>.  En outre, la propriété <xref:System.ServiceModel.Channels.MessageVersion%2A> de la liaison doit être <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.  
  
 Pour éviter l'exposition d'un service aux utilisateurs malveillants, il est possible de sécuriser le transfert à l'aide du mécanisme HTTPS \(SSL over HTTP\).  Pour ce faire, vous devez d'abord lier un certificat X.509 approprié à un port spécifique sur l'ordinateur qui héberge le service.  \([!INCLUDE[crdefault](../../../../../includes/crdefault-md.md)] [Utilisation des certificats](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).\) Ensuite, ajoutez cet élément à la configuration du service et définissez l'attribut `httpsGetEnabled` sur `true`.  Enfin, affectez l'URL du point de terminaison des métadonnées du service à l'attribut `httpsGetUrl`, comme indiqué dans l'exemple suivant.  
  
```  
<behaviors>  
 <serviceBehaviors>  
  <behavior name="NewBehavior">  
    <serviceMetadata httpsGetEnabled="true"   
     httpsGetUrl="https://myComputerName/myEndpoint" />  
  </behavior>  
 </serviceBehaviors>  
</behaviors>  
```  
  
## Exemple  
 L'exemple suivant illustre la configuration d'un service pour exposer des métadonnées à l'aide de l'élément \<serviceMetadata\>.  Il configure également un point de terminaison afin d'exposer le contrat `IMetadataExchange` comme implémentation d'un protocole WS\-MetadataExchange \(MEX\).  L'exemple utilise `mexHttpBinding`, qui est une liaison standard équivalente à `wsHttpBinding` dans laquelle le mode de sécurité a la valeur `None`.  Une adresse relative de « mex » est utilisée dans le point de terminaison. Lorsqu'elle est résolue par rapport à l'adresse de base des services, l'adresse de point de terminaison est http:\/\/localhost\/servicemodelsamples\/service.svc\/mex.  
  
```  
<configuration>  
<system.serviceModel>  
  <services>  
    <service   
        name="Microsoft.ServiceModel.Samples.CalculatorService"  
        behaviorConfiguration="CalculatorServiceBehavior">  
      <!-- This endpoint is exposed at the base address provided by the host: http://localhost/servicemodelsamples/service.svc  -->  
      <endpoint address=""  
                binding="wsHttpBinding"  
                contract="Microsoft.ServiceModel.Samples.ICalculator" />  
      <!-- the mex endpoint is exposed at http://localhost/servicemodelsamples/service.svc/mex   
           To expose the IMetadataExchange contract, you   
           must enable the serviceMetadata behavior as demonstrated below -->  
      <endpoint address="mex"  
                binding="mexHttpBinding"  
                contract="IMetadataExchange" />  
    </service>  
  </services>  
  
  <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->  
  <behaviors>  
    <serviceBehaviors>  
      <behavior name="CalculatorServiceBehavior">  
        <!-- The serviceMetadata behavior publishes metadata through   
             the IMetadataExchange contract. When this behavior is   
             present, you can expose this contract through an endpoint   
             as shown above. Setting httpGetEnabled to true publishes   
             the service's WSDL at the <baseaddress>?wsdl  
             eg. http://localhost/servicemodelsamples/service.svc?wsdl -->  
        <serviceMetadata httpGetEnabled="True"/>  
        <serviceDebug includeExceptionDetailInFaults="False" />  
      </behavior>  
    </serviceBehaviors>  
  </behaviors>  
  
</system.serviceModel>  
  
</configuration>  
```  
  
## Voir aussi  
 <xref:System.ServiceModel.Configuration.ServiceMetadataPublishingElement>   
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior>   
 [Comportements de sécurité](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)   
 [Metadata Publishing Behavior](../../../../../docs/framework/wcf/samples/metadata-publishing-behavior.md)