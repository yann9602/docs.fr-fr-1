---
title: "&lt;idn&gt;, &#233;l&#233;ment (param&#232;tres d&#39;URI) | Microsoft Docs"
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
ms.assetid: 16c8e869-1791-4cf5-9244-3d3c738f60ec
caps.latest.revision: 11
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 11
---
# &lt;idn&gt;, &#233;l&#233;ment (param&#232;tres d&#39;URI)
Spécifie si l'analyse de l'IDN \(Internationalized Domain Name\) est appliquée à un nom de domaine.  
  
## Hiérarchie de schéma  
 [\<configuration\>, élément](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [\<Uri\>, élément \(paramètres d'URI\)](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)  
  
 [\<idn\>](../../../../../docs/framework/configure-apps/file-schema/network/idn-element-uri-settings.md)  
  
## Syntaxe  
  
```  
<idn  
  enabled="All|AllExceptIntranet|None"  
/idn>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|**Élément**|**Description**|  
|-----------------|---------------------|  
|`enabled`|Spécifie si l'analyse de l'IDN est appliquée à un nom de domaine. La valeur par défaut est Aucune|  
  
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
  
2.  Précisez si vous voulez appliquer l'analyse de l'IDN \(Internationalized Domain Name\) au nom de domaine et des règles d'analyse d'IRI.  Cela se fait dans le fichier machine.config ou app.config.  
  
 Il existe trois valeurs possibles pour l'IDN selon les serveurs DNS utilisés :  
  
-   idn enabled \= All  
  
     Cette valeur convertit tous les noms de domaine Unicode en leurs équivalents Punycode \(noms IDN\).  
  
-   idn enabled \= AllExceptIntranet  
  
     Cette valeur convertit tous les noms de domaine Unicode ne se trouvant pas sur l'Intranet local pour utiliser les équivalents Punycode \(noms IDN\).  Dans ce cas, pour gérer des noms internationaux sur l'Intranet local, les serveurs DNS utilisés pour l'Intranet doivent prendre en charge la résolution de noms Unicode.  
  
-   idn enabled \= None  
  
     Cette valeur ne convertit aucun nom de domaine Unicode pour utiliser Punycode.  Il s'agit de la valeur par défaut cohérente avec le comportement de la version 2.0 du .NET Framework.  
  
 L'activation de l'IDN permet de convertir toutes les étiquettes Unicode d'un nom de domaine en leurs équivalents Punycode.  Les noms Punycode contiennent uniquement des caractères ASCII et commencent toujours par le préfixe xn\-\-.  L'objectif est de prendre en charge des serveurs DNS existants sur Internet, étant donné que la plupart des serveurs DNS ne prennent en charge que des caractères ASCII \(consultez RFC 3940\).  
  
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
 <xref:System.Configuration.IdnElement?displayProperty=fullName>   
 <xref:System.Configuration.UriSection?displayProperty=fullName>   
 [Schéma des paramètres réseau](../../../../../docs/framework/configure-apps/file-schema/network/index.md)