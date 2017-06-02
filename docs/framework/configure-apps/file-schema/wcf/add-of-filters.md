---
title: "&lt;add&gt; de &lt;filters&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e3bf437c-dd99-49f3-9792-9a8721e6eaad
caps.latest.revision: 4
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 4
---
# &lt;add&gt; de &lt;filters&gt;
Filtre XPath qui spécifie le type de message à enregistrer.  
  
## Syntaxe  
  
```  
  
<filters>  
   <add filter="String"/>  
</filters>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|filtre|Chaîne qui spécifie une requête sur un document XML défini par une expression XPath 1.0.  Pour plus d'informations, consultez <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>.|  
  
### Éléments enfants  
 Aucun  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<filtres\>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters.md)|Contient une collection de filtres XPath utilisés pour contrôler le type de message enregistré.|  
  
## Notes  
 Les filtres sont appliqués uniquement à la couche de transport, spécifiée par `logMessagesAtTransportLevel` \(valeur `true`\).  Le niveau de service et l'enregistrement du message incorrect ne sont pas affectés par les filtres.  
  
 Pour ajouter un filtre à la collection, utilisez le mot clé `add`.  Lorsqu'un ou plusieurs filtres sont définis, seuls les messages qui correspondent au moins à l'un des filtres sont enregistrés.  Si aucun filtre n'est défini, tous les messages passent.  
  
 Les filtres prennent en charge la syntaxe XPath complète et s'appliquent dans l'ordre dans lequel ils apparaissent dans le fichier de configuration.  Un filtre syntaxiquement incorrect provoque la levée d'une exception de configuration.  
  
 L'exemple de code suivant illustre comment configurer un filtre afin que seuls les messages contenant une section d'en\-tête SOAP soient enregistrés.  
  
## Exemple  
 L'exemple de code suivant illustre comment configurer un filtre afin que seuls les messages contenant une section d'en\-tête SOAP soient enregistrés.  
  
```  
<messageLogging logEntireMessage="true"  
     logMalformedMessages="true" logMessagesAtServiceLevel="true"  
     logMessagesAtTransportLevel="true" maxMessagesToLog="420”>  
     <filters>  
        <add xmlns:soap="http://www.w3.org/2003/05/soap-envelope">  
                        /soap:Envelope/soap:Headers  
        </add>  
     </filters>  
</messageLogging>  
```  
  
## Voir aussi  
 <xref:System.ServiceModel.Configuration.DiagnosticSection>   
 <xref:System.ServiceModel.Diagnostics>   
 <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>   
 <xref:System.ServiceModel.Configuration.MessageLoggingElement>   
 <xref:System.ServiceModel.Configuration.MessageLoggingElement.Filters%2A>   
 <xref:System.ServiceModel.Configuration.XpathMessageFilterElement>   
 <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>   
 [Configuration de la journalisation des messages](../../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md)   
 [Configuration de la journalisation des messages](../../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md)   
 [\<messageLogging\>](../../../../../docs/framework/configure-apps/file-schema/wcf/messagelogging.md)