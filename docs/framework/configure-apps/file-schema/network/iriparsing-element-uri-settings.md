---
title: "&lt;iriParsing&gt;, &#233;l&#233;ment (param&#232;tres d&#39;URI) | Microsoft Docs"
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
ms.assetid: 953d0b53-445e-41f9-b302-77c4030852ce
caps.latest.revision: 9
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 9
---
# &lt;iriParsing&gt;, &#233;l&#233;ment (param&#232;tres d&#39;URI)
Spécifie si l'analyse IRI \(International Resource Identifier\) est appliquée à un <xref:System.Uri> et si les règles d'analyse de l'identificateur IRI doivent être appliquées.  
  
## Hiérarchie de schéma  
 [\<configuration\>, élément](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [\<Uri\>, élément \(paramètres d'URI\)](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)  
  
 [\<iriParsing\>](../../../../../docs/framework/configure-apps/file-schema/network/iriparsing-element-uri-settings.md)  
  
## Syntaxe  
  
```  
<idn  
  enabled="true|false"  
/idn>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|**Élément**|**Description**|  
|-----------------|---------------------|  
|`enabled`|Spécifie si l'analyse IRI est activée.  La valeur par défaut est `false`.|  
  
### Éléments enfants  
 None  
  
### Éléments parents  
  
|**Élément**|**Description**|  
|-----------------|---------------------|  
|[uri](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)|Contient des paramètres qui spécifient la manière dont le .NET Framework gère des adresses Web exprimées à l'aide d'identificateurs URI \(Uniform Resource Identifiers\).|  
  
## Remarques  
 La classe <xref:System.Uri> existante a été étendue dans le .NET Framework 3.5. 3.0 SP1 et 2.0 SP1 avec prise en charge des IRI \(International Resource Identifiers\) et des IDN \(Internationalized Domain Names\).  Les utilisateurs actuels ne percevront pas les modifications du comportement de la version 2.0 du .NET Framework, sauf s'ils activent spécifiquement les prises en charge IRI et IDN.  Cela garantit la compatibilité des applications avec les versions antérieures du .NET Framework.  
  
 Pour activer la prise en charge des IRI, les deux modifications suivantes sont requises :  
  
1.  Ajout de la ligne suivante au fichier machine.config sous le répertoire .NET Framework 2.0  
  
    ```  
    <section name="uri" type="System.Configuration.UriSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    ```  
  
2.  Spécifications sur l'application des règles d'analyse de l'identificateur IRI.  Cela se fait dans le fichier machine.config ou app.config.  
  
 L'activation de l'analyse IRI \(iriParsing enabled \= `true`\) effectuera la vérification de la normalisation et des caractères d'après les règles IRI les plus récentes de la norme RFC 3987.  La valeur par défaut est `false` et effectuera la vérification de la normalisation et des caractères d'après les normes RFC 2396 et RFC 3986 \(pour les littéraux IPv6\).  
  
### Fichiers de configuration  
 Cet élément peut être utilisé dans le fichier de configuration de l'application ou dans le fichier de configuration machine \(Machine.config\).  
  
## Exemple  
  
### Description  
 L'exemple de code suivant illustre une configuration utilisée par la classe <xref:System.Uri> pour prendre en charge l'analyse de l'IRI et les noms IDN.  
  
### Code  
  
```  
<configuration>  
  <uri>  
    <idn enabled="All" />  
    <iriParsing enabled="true" />  
  </uri>  
</configuration>  
```  
  
## Voir aussi  
 <xref:System.Configuration.IriParsingElement?displayProperty=fullName>   
 <xref:System.Configuration.UriSection?displayProperty=fullName>   
 [Schéma des paramètres réseau](../../../../../docs/framework/configure-apps/file-schema/network/index.md)