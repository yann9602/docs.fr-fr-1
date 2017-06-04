---
title: "&lt;Uri&gt;, &#233;l&#233;ment (param&#232;tres d&#39;URI) | Microsoft Docs"
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
  - "C++"
  - "jsharp"
ms.assetid: c22bab8b-477c-4ae4-8498-65ad409e0847
caps.latest.revision: 11
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 11
---
# &lt;Uri&gt;, &#233;l&#233;ment (param&#232;tres d&#39;URI)
Contient des paramètres qui spécifient la manière dont le .NET Framework gère des adresses Web exprimées à l'aide d'identificateurs URI \(Uniform Resource Identifiers\).  
  
## Hiérarchie de schéma  
 [\<configuration\>, élément](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [\<uri\>](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)  
  
## Syntaxe  
  
```  
<uri>  
</uri>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
 Aucun  
  
### Éléments enfants  
  
|**Élément**|**Description**|  
|-----------------|---------------------|  
|[idn](../../../../../docs/framework/configure-apps/file-schema/network/idn-element-uri-settings.md)|Spécifie si l'analyse de l'IDN \(Internationalized Domain Name\) est appliquée aux noms de domaines.|  
|[iriParsing](../../../../../docs/framework/configure-apps/file-schema/network/iriparsing-element-uri-settings.md)|Spécifie si l'analyse IRI \(International Resource Identifier\) est appliquée à un <xref:System.Uri> et si les règles d'analyse de l'identificateur IRI doivent être appliquées.|  
|[schemeSettings](../../../../../docs/framework/configure-apps/file-schema/network/schemesettings-element-uri-settings.md)|Spécifie comment un <xref:System.Uri> sera analysé pour des schémas spécifiques.|  
  
### Éléments parents  
  
|**Élément**|**Description**|  
|-----------------|---------------------|  
|[configuration](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|Contient les paramètres de tous les espaces de noms.|  
  
## Remarques  
 L'élément `uri` contient des paramètres pour les membres de la classe <xref:System.Uri> utilisés par des classes de l'espace de noms <xref:System.Net>.  Les paramètres configurent la prise en charge des IRI et des IDN.  
  
## Exemple  
  
### Description  
 L'exemple de code suivant illustre une configuration utilisée par la classe <xref:System.Uri> pour prendre en charge l'analyse de l'IRI et les noms IDN.  L'exemple efface également tous les paramètres de schémas, puis ajoute une prise en charge visant à ne pas échapper de délimiteurs de chemin d'accès encodés de pourcentage pour le schéma http.  
  
### Code  
  
```  
<configuration>  
  <uri>  
    <idn enabled="All" />  
    <iriParsing enabled="true" />  
    <schemeSettings>  
      <clear/>  
      <add name="http" genericUriParserOptions="DontUnescapePathDotsAndSlashes"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## Voir aussi  
 [Schéma des paramètres réseau](../../../../../docs/framework/configure-apps/file-schema/network/index.md)