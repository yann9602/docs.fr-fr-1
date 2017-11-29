---
title: '&lt;serviceHostingEnvironment&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4f8a7c4f-e735-4987-979a-b74fcdae2652
caps.latest.revision: "24"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 5770cb8fd68eb68145f3f7fbcf197302883efe9f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ltservicehostingenvironmentgt"></a>&lt;serviceHostingEnvironment&gt;
Cet élément définit le type instancié par l'environnement d'hébergement de service correspondant à un transport particulier. Si cet élément est vide, c'est le type par défaut qui est utilisé. Cet élément ne peut être utilisé qu'au niveau des fichiers de configuration de l'application ou de l'ordinateur.  
  
 \<système. ServiceModel >  
\<ServiceHostingEnvironment >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<serviceHostingEnvironment aspNetCompatibilityEnabled="Boolean" 
                           minFreeMemoryPercentageToActivateService="Integer" 
                           multipleSiteBindingsEnabled="Boolean">
  <baseAddressPrefixFilters>
    <add prefix="string" />
  </baseAddressPrefixFilters>
  <serviceActivations>
    <add factory="String" service="String" />
  </serviceActivations>
  <transportConfigurationTypes>
    <add name="String" transportConfigurationType="String" />
  </transportConfigurationTypes>
</serviceHostingEnvironment>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|aspNetCompatibilityEnabled|Valeur booléenne indiquant si le mode de compatibilité ASP.NET a été activé pour l'application actuelle. La valeur par défaut est `false`.<br /><br /> Lorsque cet attribut a la valeur `true`, les demandes transmises aux services [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] passent par le pipeline HTTP ASP.NET ; en outre, les communications via des protocoles non-HTTP sont interdites. Pour plus d’informations, consultez [Services WCF et ASP.NET](../../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md).|  
|minFreeMemoryPercentageToActivateService|Entier indiquant la quantité minimale de mémoire disponible nécessaire au système pour permettre l'activation d'un service [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]. **Attention :** spécification de cet attribut avec une confiance partielle dans le fichier web.config d’un [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] service entraîne un <xref:System.Security.SecurityException> lorsque le service est exécuté.|  
|multipleSiteBindingsEnabled|Valeur booléenne qui spécifie si plusieurs liaisons IIS par site sont autorisées.<br /><br /> Les services IIS se composent de sites Web, qui sont des conteneurs d'applications virtuelles contenant des répertoires virtuels. L'application dans un site est accessible par le biais d'une ou de plusieurs liaisons IIS. Une liaison IIS fournit deux informations : un protocole de liaison et des informations de liaison. Le protocole de liaison définit le schéma selon lequel la communication est établie et les informations de liaison sont les informations utilisées pour accéder au site. HTTP peut être un exemple de protocole de liaison, tandis que les informations de liaison peuvent contenir une adresse IP, un port, un en-tête d'hôte, etc.<br /><br /> IIS prend en charge la spécification de plusieurs liaisons IIS par site, ce qui entraîne plusieurs adresses de base par schéma. Toutefois, un service [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] hébergé sur un site n'autorise la liaison qu'avec un seul baseAddress par schéma.<br /><br /> Pour autoriser plusieurs liaisons IIS par site pour un service [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)], affectez à cet attribut la valeur `true`. Notez que la spécification de plusieurs liaisons de site est prise en charge uniquement pour le protocole HTTP. L'adresse des points de terminaison dans le fichier de configuration doit être un URI complet.|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<baseAddressPrefixFilters >](../../../../../docs/framework/configure-apps/file-schema/wcf/baseaddressprefixfilters.md)|Collection des éléments de configuration qui spécifient des filtres de préfixe pour les adresses de base utilisée par l’hôte de service.|  
|[\<serviceActivations >](../../../../../docs/framework/configure-apps/file-schema/wcf/serviceactivations.md)|Section de configuration qui décrit les paramètres d'activation.|  
|[\<transportConfigurationTypes >](../../../../../docs/framework/configure-apps/file-schema/wcf/transportconfigurationtypes.md)|Collection des éléments de configuration identifiant le type d’un transport particulier.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|serviceModel|Élément racine de tous les éléments de configuration Windows Communication Foundation (WCF).|  
  
## <a name="remarks"></a>Remarques  
 Par défaut, les services WCF sont exécutés conjointement à ASP.NET dans les domaines d'application hébergés (AppDomain). Bien que WCF et ASP.NET puissent coexister sur le même domaine AppDomain, les demandes WCF ne sont pas traitées par défaut par le pipeline HTTP d'ASP.NET. En conséquence, plusieurs éléments de la plate-forme d'application ASP.NET ne sont pas disponibles pour les services WCF. Il s'agit des méthodes suivantes :  
  
-   Autorisation de l'URL/du fichier ASP.NET  
  
-   Emprunt d'identité ASP.NET  
  
-   État de session basé sur les cookies  
  
-   HttpContext.Current  
  
-   Extensibilité de pipeline via HttpModule personnalisé  
  
 Si vos services WCF doivent fonctionner dans le contexte ASP.NET et communiquer uniquement via HTTP, vous pouvez utiliser le mode de compatibilité ASP.NET de WCF. Ce mode est activé lorsque l'attribut `aspNetCompatibilityEnabled` a la valeur `true` au niveau de l'application. Les implémentations de service doivent déclarer leur capacité de fonctionner en mode de compatibilité à l'aide de la classe <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute>. Lorsque le mode de compatibilité est activé :  
  
-   L'autorisation de l'URL/du fichier ASP.NET est appliquée avant l'autorisation WCF. Une décision d'autorisation est basée sur l'identité de la demande au niveau du transport. Les identités au niveau du message sont ignorées.  
  
-   Les opérations de service WCF commencent à s'exécuter dans le contexte d'emprunt d'identité ASP.NET. Si les emprunts d'identité ASP.NET et WCF sont tous deux activés pour un service spécifique, c'est le contexte d'emprunt d'identité WCF qui est appliqué.  
  
-   HttpContext.Current peut être utilisé à partir du code de service WCF ; cette opération permet d'empêcher l'exposition des points de terminaison non-HTTP.  
  
-   Les demandes WCF sont traitées par le pipeline ASP.NET. Les HttpModules ayant été configurés pour agir sur les requêtes entrantes peuvent également traiter des demandes WCF. Ils peuvent inclure des composants de plate-forme ASP.NET (par exemple, <xref:System.Web.SessionState.SessionStateModule>), ainsi que des modules tiers personnalisés.  
  
## <a name="example"></a>Exemple  
 L'exemple de code suivant indique comment activer le Mode de compatibilité ASP.  
  
## <a name="code"></a>Code  
  
```xml  
<serviceHostingEnvironment aspNetCompatibilityEnabled="true"/>  
```  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>  
 <xref:System.ServiceModel.ServiceHostingEnvironment>  
 [Hébergement d’applications WPF](../../../../../docs/framework/wcf/feature-details/hosting.md)  
 [Services WCF et ASP.NET](../../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md)
