---
title: "&lt;schemeSettings&gt;, &#233;l&#233;ment (param&#232;tres d&#39;URI) | Microsoft Docs"
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
ms.assetid: 0ae45c6e-8c4c-4c0d-8b9f-a93824648890
caps.latest.revision: 6
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 6
---
# &lt;schemeSettings&gt;, &#233;l&#233;ment (param&#232;tres d&#39;URI)
Spécifie comment un <xref:System.Uri> sera analysé pour des schémas spécifiques.  
  
## Syntaxe  
  
```  
  
      <schemeSettings>   
</schemeSettings>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
 None  
  
### Éléments enfants  
  
|**Élément**|**Description**|  
|-----------------|---------------------|  
|[ajouter](../../../../../docs/framework/configure-apps/file-schema/network/add-element-for-schemesettings-uri-settings.md)|Ajoute un paramètre de modèle pour un nom de modèle.|  
|[clear](../../../../../docs/framework/configure-apps/file-schema/network/clear-element-for-schemesettings-uri-settings.md)|Efface tous les paramètres de schémas existants.|  
|[remove](../../../../../docs/framework/configure-apps/file-schema/network/remove-element-for-schemesettings-uri-settings.md)|Supprime un paramètre de schéma correspondant à un nom de schéma.|  
  
### Éléments parents  
  
|**Élément**|**Description**|  
|-----------------|---------------------|  
|[uri](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)|Contient des paramètres qui spécifient la manière dont le .NET Framework gère des adresses Web exprimées à l'aide d'identificateurs URI \(Uniform Resource Identifiers\).|  
  
## Notes  
 Par défaut, la classe <xref:System.Uri?displayProperty=fullName> n'échappe pas les délimiteurs de chemin d'accès encodés de pourcentage avant d'exécuter la compression de chemin d'accès.  Cela a été implémenté comme mécanisme de sécurité contre des attaques telles que les suivantes :  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 Si cet URI est passé à des modules qui ne gèrent pas correctement les caractères encodés de pourcentage, il pourrait provoquer l'exécution de la commande suivante par le serveur :  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 Pour cette raison, la classe <xref:System.Uri?displayProperty=fullName> place en premier les délimiteurs de chemin d'accès hors d'une séquence d'échappement puis applique la compression des chemin d'accès.  Le résultat du passage de l'URL malveillante ci\-dessus au constructeur de classe <xref:System.Uri?displayProperty=fullName> provoque l'URI suivant :  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 Ce comportement par défaut peut être modifié pour échapper des délimiteurs de chemin d'accès encodés en pourcentage à l'aide de l'option de configuration schemeSettings pour un modèle spécifique.  
  
## Fichiers de configuration  
 Cet élément peut être utilisé dans le fichier de configuration de l'application ou dans le fichier de configuration machine \(Machine.config\).  
  
## Exemple  
 L'exemple de code suivant présente une configuration utilisée par la classe <xref:System.Uri> afin de ne pas placer dans une séquence d'échappement les délimiteurs de chemin d'accès encodés en pourcentage pour le schéma HTTP.  
  
```  
<configuration>  
  <uri>  
    <schemeSettings>  
      <add name="http" genericUriParserOptions="DontUnescapePathDotsAndSlashes"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## Informations sur les éléments  
  
|||  
|-|-|  
|Espace de noms|Système|  
|Nom du schéma||  
|Fichier de validation||  
|Peut être vide||  
  
## Voir aussi  
 <xref:System.Configuration.SchemeSettingElement?displayProperty=fullName>   
 <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=fullName>   
 <xref:System.Configuration.UriSection?displayProperty=fullName>   
 <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=fullName>   
 <xref:System.GenericUriParserOptions?displayProperty=fullName>   
 <xref:System.Uri?displayProperty=fullName>   
 [Schéma des paramètres réseau](../../../../../docs/framework/configure-apps/file-schema/network/index.md)