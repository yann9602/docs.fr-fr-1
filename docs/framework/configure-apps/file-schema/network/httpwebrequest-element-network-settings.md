---
title: "&lt;httpWebRequest&gt;, &#233;l&#233;ment (param&#232;tres r&#233;seau) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/httpWebRequest"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#httpWebRequest"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<httpWebRequest> (élément)"
  - "httpWebRequest (élément)"
ms.assetid: 52acd9d2-5bdc-4dc4-9c2a-f0a476ccbb31
caps.latest.revision: 18
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 18
---
# &lt;httpWebRequest&gt;, &#233;l&#233;ment (param&#232;tres r&#233;seau)
Personnalise les paramètres de demande Web.  
  
## Syntaxe  
  
```  
  
      <httpWebRequest  
  maximumResponseHeadersLength="size"  
  maximumErrorResponseLength="size"  
  maximumUnauthorizedUploadLength="size"  
  useUnsafeHeaderParsing="true|false"  
/>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|**Attribut**|**Description**|  
|------------------|---------------------|  
|`maximumResponseHeadersLength`|Spécifie la longueur maximale d'un en\-tête de réponse, en kilo\-octets.  La valeur par défaut est 64.  Une valeur de \-1 indique qu'aucune limite de taille n'est imposée aux en\-têtes de réponse.|  
|`maximumErrorResponseLength`|Spécifie la longueur maximale d'une réponse d'erreur, en kilo\-octets.  La valeur par défaut est 64.  Une valeur de \-1 indique qu'aucune limite de taille n'est imposée à la réponse d'erreur.|  
|`maximumUnauthorizedUploadLength`|Spécifie la longueur maximale d'un téléchargement en réponse à un code d'erreur non autorisé, en octets.  La valeur par défaut est \-1.  Une valeur de \-1 indique qu'aucune limite de taille n'est imposée au transfert.|  
|`useUnsafeHeaderParsing`|Spécifie si l'analyse des en\-têtes non sécurisés est activée.  La valeur par défaut est `false`.|  
  
### Éléments enfants  
 Aucun  
  
### Éléments parents  
  
|**Élément**|**Description**|  
|-----------------|---------------------|  
|[paramètres](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|Configure les options réseau de base pour l'espace de noms <xref:System.Net>.|  
  
## Notes  
 Par défaut, le .NET Framework applique strictement la norme RFC 2616 pour l'analyse URI.  Certaines réponses du serveur peuvent inclure des caractères de contrôle dans les champs interdits ; dans ce cas, la méthode <xref:System.Net.HttpWebRequest.GetResponse?displayProperty=fullName> lève une <xref:System.Net.WebException>.  Si **useUnsafeHeaderParsing** a la valeur **true**, <xref:System.Net.HttpWebRequest.GetResponse?displayProperty=fullName> ne lève pas d'exception ; toutefois, votre application sera vulnérable à plusieurs formes d'attaques d'analyse URI.  La meilleure solution consiste à changer le serveur de sorte que la réponse n'inclue pas de caractères de contrôle.  
  
## Fichiers de configuration  
 Cet élément peut être utilisé dans le fichier de configuration de l'application ou dans le fichier de configuration machine \(Machine.config\).  
  
## Exemple  
 L'exemple de code suivant indique comment spécifier une longueur d'en\-tête supérieure à la longueur maximale standard.  
  
```  
<configuration>  
  <system.net>  
    <settings>  
      <httpWebRequest  
        maximumResponseHeadersLength="128"  
      />  
    </settings>  
  </system.net>  
</configuration>  
```  
  
## Voir aussi  
 <xref:System.Net.HttpWebRequest.MaximumResponseHeadersLength%2A>   
 [Schéma des paramètres réseau](../../../../../docs/framework/configure-apps/file-schema/network/index.md)