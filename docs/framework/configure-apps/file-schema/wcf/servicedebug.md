---
title: "&lt;serviceDebug&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6d7ea986-f232-49fe-842c-f934d9966889
caps.latest.revision: 19
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 19
---
# &lt;serviceDebug&gt;
Spécifie les fonctionnalités de débogage et d'informations d'aide pour un service [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)].  
  
## Syntaxe  
  
```  
  
<serviceDebug   
    httpHelpPageBinding=”String”  
    httpHelpPageBindingConfiguration=”String”  
    httpHelpPageEnabled="Boolean"  
    httpHelpPageUrl="Uri"  
    httpsHelpPageBinding=”String”  
    httpsHelpPageBindingConfiguration=”String”  
    httpsHelpPageEnabled="Boolean"  
    httpsHelpPageUrl="Uri"  
    includeExceptionDetailInFaults="Boolean" />  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|httpHelpPageBinding|Valeur de chaîne qui spécifie le type de liaison à utiliser lorsque le protocole HTTP permet d'accéder à la page d'aide du service.<br /><br /> La prise en charge n'est assurée que pour les liaisons comportant des éléments de liaison internes qui prennent en charge [System.ServiceModel.Channels.IReplyChannel](assetId:///System.ServiceModel.Channels.IReplyChannel?qualifyHint=False&amp;autoUpgrade=True).  En outre, la propriété [System.ServiceModel.Channels.MessageVersion](assetId:///System.ServiceModel.Channels.MessageVersion?qualifyHint=False&amp;autoUpgrade=True) de la liaison doit être [System.ServiceModel.Channels.MessageVersion.None](assetId:///System.ServiceModel.Channels.MessageVersion.None?qualifyHint=False&amp;autoUpgrade=True).|  
|httpHelpPageBindingConfiguration|Chaîne qui définit le nom de la liaison spécifiée dans l'attribut `httpHelpPageBinding`, qui fait référence aux informations de configuration supplémentaires de cette liaison.  Le même nom doit être défini dans la section `<bindings>`.|  
|httpHelpPageEnabled|Valeur booléenne qui contrôle si [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] publie une page d'aide HTML à l'adresse spécifiée par l'attribut `httpHelpPageUrl`.  La valeur par défaut est `true`.<br /><br /> Vous pouvez affecter la valeur `false` à cette propriété pour désactiver la publication d'une page d'aide HTML visible par les navigateurs HTML.<br /><br /> Pour vous assurer que la page d'aide HTML est publiée à l'emplacement contrôlé par l'attribut `httpHelpPageUrl`, vous devez affecter la valeur `true` à cet attribut.  L'une des conditions suivantes doit également être remplie :<br /><br /> -   L'attribut `httpHelpPageUrl` est une adresse absolue qui prend en charge le schéma de protocole HTTP.<br />-   Il existe une adresse de base pour le service qui prend en charge le schéma de protocole HTTP.<br /><br /> Bien qu'une exception soit levée si une adresse absolue qui ne prend pas en charge le schéma de protocole HTTP est assignée à l'attribut `httpHelpPageUrl`, tout autre scénario dans lequel aucun des critères précédents n'est rempli ne lève pas d'exception et ne génère aucune page d'aide HTML.|  
|httpHelpPageUrl|URI qui spécifie l'URL basée sur HTTP relative ou absolue du fichier d'aide HTML personnalisé que l'utilisateur consulte lorsque le point de terminaison est affiché à l'aide d'un navigateur HTML.<br /><br /> Vous pouvez utiliser cet attribut pour activer l'utilisation d'un fichier d'aide HTML personnalisé retourné par une requête HTTP\/Get, à partir d'un navigateur HTML par exemple.  L'emplacement du fichier d'aide HTML est résolu comme suit.<br /><br /> 1.  Si la valeur de cet attribut est une adresse relative, l'emplacement du fichier d'aide HTML correspond à la valeur de l'adresse de base du service qui prend en charge les requêtes HTTP, plus la valeur de cette propriété.<br />2.  Si la valeur de cet attribut est une adresse absolue et prend en charge les requêtes HTTP, l'emplacement du fichier d'aide HTML correspond à la valeur de cette propriété.<br />3.  Si la valeur de cet attribut est absolue mais ne prend pas en charge les requêtes HTTP, une exception est levée.<br /><br /> Cet attribut est valide uniquement lorsque l'attribut `httpHelpPageEnabled`  a la valeur `true`.|  
|httpsHelpPageBinding|Valeur de chaîne qui spécifie le type de liaison à utiliser lorsque le protocole HTTPS permet d'accéder à la page d'aide du service.<br /><br /> La prise en charge n'est assurée que pour les liaisons comportant des éléments de liaison internes qui prennent en charge assetId:///System.ServiceModel.Channels.IReplyChannel?qualifyHint=False&amp;autoUpgrade=True.  En outre, la propriété assetId:///System.ServiceModel.Channels.MessageVersion?qualifyHint=False&amp;autoUpgrade=True de la liaison doit être assetId:///System.ServiceModel.Channels.MessageVersion.None?qualifyHint=False&amp;autoUpgrade=True.|  
|httpsHelpPageBindingConfiguration|Chaîne qui définit le nom de la liaison spécifiée dans l'attribut `httpsHelpPageBinding`, qui fait référence aux informations de configuration supplémentaires de cette liaison.  Le même nom doit être défini dans la section `<bindings>`.|  
|httpsHelpPageEnabled|Valeur booléenne qui contrôle si [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] publie une page d'aide HTML à l'adresse spécifiée par l'attribut `httpsHelpPageUrl`.  La valeur par défaut est `true`.<br /><br /> Vous pouvez affecter la valeur `false` à cette propriété pour désactiver la publication d'une page d'aide HTML visible par les navigateurs HTML.<br /><br /> Pour vous assurer que la page d'aide HTML est publiée à l'emplacement contrôlé par l'attribut `httpsHelpPageUrl`, vous devez affecter la valeur `true` à cet attribut.  L'une des conditions suivantes doit également être remplie :<br /><br /> -   L'attribut `httpsHelpPageUrl` est une adresse absolue qui prend en charge le schéma de protocole HTTPS.<br />-   Il existe une adresse de base pour le service qui prend en charge le schéma de protocole HTTPS.<br /><br /> Bien qu'une exception soit levée si une adresse absolue qui ne prend pas en charge le schéma de protocole HTTPS est assignée à l'attribut `httpsHelpPageUrl`, tout autre scénario dans lequel aucun des critères précédents n'est rempli ne lève pas d'exception et ne génère aucune page d'aide HTML.|  
|httpsHelpPageUrl|URI qui spécifie l'URL basée sur HTTPS relative ou absolue du fichier d'aide HTML personnalisé que l'utilisateur consulte lorsque le point de terminaison est affiché à l'aide d'un navigateur HTML.<br /><br /> Vous pouvez utiliser cet attribut pour activer l'utilisation d'un fichier d'aide HTML personnalisé retourné par une requête HTTPS\/Get, à partir d'un navigateur HTML par exemple.  L'emplacement du fichier d'aide HTML est résolu comme suit :<br /><br /> -   Si la valeur de cette propriété est une adresse relative, l'emplacement du fichier d'aide HTML est la valeur de l'adresse de base du service qui prend en charge les requêtes HTTPS, plus cette valeur de propriété.<br />-   Si la valeur de cette propriété est une adresse absolue et prend en charge les requêtes HTTPS, l'emplacement du fichier d'aide HTML est la valeur de cette propriété.<br />-   Si la valeur de cette propriété est absolue mais ne prend pas en charge les requêtes HTTPS, une exception est levée.<br /><br /> Cet attribut est valide uniquement lorsque l'attribut `httpHelpPageEnabled`  a la valeur `true`.|  
|includeExceptionDetailInFaults|Valeur qui spécifie si des informations sur les exceptions managées doivent être incluses dans les informations sur les erreurs SOAP retournées au client à des fins de débogage.  La valeur par défaut est `false`.<br /><br /> Si vous affectez par programme la valeur `true` à l'attribut, vous pouvez activer le flux d'informations sur les exceptions managées pour le client à des fins de débogage, ainsi que la publication de fichiers d'informations HTML pour les utilisateurs qui parcourent le service avec un navigateur Web. **Caution:**  Le retour des informations sur les exceptions managées aux clients peut entraîner un problème de sécurité.  En effet, les détails de l'exception exposent des informations relatives à l'implémentation d'un service interne qui peuvent être utilisées par des clients non autorisés.|  
  
### Éléments enfants  
 Aucun  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<comportement\>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Spécifie un élément de comportement.|  
  
## Notes  
 Affecter à `includeExceptionDetailInFaults` la valeur `true` permet au service de retourner toute exception levée même par le code d'application si l'exception n'est pas déclarée à l'aide du <xref:System.ServiceModel.FaultContractAttribute>.  Ce paramètre est utile lors du débogage de cas où le serveur lève une exception inattendue.  Avec cet attribut, un formulaire sérialisé de l'exception inconnue est retourné et vous pouvez consulter plus de détails de l'exception.  
  
> [!CAUTION]
>  Le retour d'informations sur les exceptions managées aux clients peut constituer un problème de sécurité, car les détails d'exception exposent des informations relatives à l'implémentation de service interne que des clients non autorisés pourraient utiliser.  En raison des risques de sécurité encourus, il est fortement recommandé de n'utiliser cette méthode que dans le cadre de scénarios de débogage contrôlés.  Vous devez affecter la valeur `false` à `includeExceptionDetailInFaults` lors du déploiement de l'application.  
  
 Pour plus d'informations sur les problèmes de sécurité liés aux exceptions managées, consultez [Spécification et gestion des erreurs dans les contrats et les services](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md).  Pour obtenir un exemple de code, consultez [Service Debug Behavior](../../../../../docs/framework/wcf/samples/service-debug-behavior.md).  
  
 Vous pouvez également définir `httpsHelpPageEnabled` et `httpsHelpPageUrl` pour activer ou désactiver la page d'aide.  Chaque service peut éventuellement exposer une page d'aide qui contient des informations sur le service, et notamment le point de terminaison permettant d'obtenir le WSDL pour le service.  Pour ce faire, affectez `true` à `httpHelpPageEnabled`.  Cela permet de retourner la page d'aide dans une demande GET à l'adresse de base du service.  Pour modifier cette adresse, définissez l'attribut `httpHelpPageUrl`.  En outre, vous pouvez faire sécuriser cette procédure en utilisant HTTPS au lieu de HTTP.  
  
 Les attributs facultatifs `httpHelpPageBinding` et `httpHelpPageBinding` vous permettent de configurer les liaisons utilisées pour accéder à la page Web du service.  S'ils ne sont pas spécifiés, les liaisons par défaut \(`HttpTransportBindingElement` dans le cas de HTTP et `HttpsTransportBindingElement` dans le cas de HTTPS\) sont utilisées pour accéder à la page d'aide du service.  Notez que vous ne pouvez pas utiliser ces attributs avec les liaisons WCF intégrées.  La prise en charge n'est assurée que pour les liaisons comportant des éléments de liaison internes qui prennent en charge assetId:///System.ServiceModel.Channels.IReplyChannel?qualifyHint=False&amp;autoUpgrade=True.  En outre, la propriété assetId:///System.ServiceModel.Channels.MessageVersion?qualifyHint=False&amp;autoUpgrade=True de la liaison doit être assetId:///System.ServiceModel.Channels.MessageVersion.None?qualifyHint=False&amp;autoUpgrade=True.  
  
## Voir aussi  
 <xref:System.ServiceModel.Configuration.ServiceDebugElement>   
 <xref:System.ServiceModel.Description.ServiceDebugBehavior>   
 [Spécification et gestion des erreurs dans les contrats et les services](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)   
 [Gestion des exceptions et des erreurs](../../../../../docs/framework/wcf/extending/handling-exceptions-and-faults.md)   
 [Service Debug Behavior](../../../../../docs/framework/wcf/samples/service-debug-behavior.md)