---
title: "&lt;bindingRedirect&gt;, &#233;l&#233;ment | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly/bindingRedirect"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#bindingRedirect"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<bindingRedirect> (élément)"
  - "bindingRedirect (élément)"
  - "balises conteneurs, <bindingRedirect> (élément)"
ms.assetid: 67784ecd-9663-434e-bd6a-26975e447ac0
caps.latest.revision: 12
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 11
---
# &lt;bindingRedirect&gt;, &#233;l&#233;ment
Redirige une version d'assembly vers une autre.  
  
## Syntaxe  
  
```  
  
   <bindingRedirect    
oldVersion="existing assembly version"  
newVersion="new assembly version"/>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|`oldVersion`|Attribut requis.<br /><br /> Spécifie la version de l'assembly demandée initialement.  Le format d'un numéro de version d'assembly est *major.minor.build.revision*.  Les valeurs valides pour chaque partie de ce numéro de version vont de 0 à 65535.<br /><br /> Vous pouvez également spécifier une plage de versions en respectant le format suivant :<br /><br /> *n.n.n.n \- n.n.n.n*|  
|`newVersion`|Attribut requis.<br /><br /> Spécifie la version de l'assembly à utiliser en lieu et place de la version initialement demandée, dans le format : *n.n.n.n*<br /><br /> Cette valeur peut spécifier une version antérieure à `oldVersion`.|  
  
### Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|Aucune||  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`assemblyBinding`|Contient des informations à propos de la redirection des versions d'assemblys et de l'emplacement de ces derniers.|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`dependentAssembly`|Encapsule la stratégie de liaisons et l'emplacement de chaque assembly.  Utilisez un élément dependentAssembly pour chaque assembly.|  
|`runtime`|Contient des informations sur les liaisons d'assembly et l'opération garbage collection.|  
  
## Notes  
 Lorsque vous générez une application .NET Framework basée sur un assembly avec nom fort, l'application utilise par défaut cette version de l'assembly au moment de l'exécution, même si une nouvelle version est disponible.  Vous pouvez toutefois configurer l'application pour faire en sorte qu'elle s'exécute en utilisant une version plus récente de l'assembly.  Pour plus d'informations sur la façon dont le code runtime utilise ces fichiers afin de déterminer la version de l'assembly à utiliser, consultez [Méthode de localisation des assemblys par le runtime](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).  
  
 Vous pouvez rediriger plusieurs versions d'assembly en incluant plusieurs éléments `bindingRedirect` dans un élément `dependentAssembly`.  Vous pouvez également rediriger une version plus récente vers une version antérieure de l'assembly.  
  
 La redirection de liaison d'assembly explicite dans un fichier de configuration de l'application nécessite une autorisation de sécurité.  Cela s'applique à la redirection des assemblys .NET Framework et des assemblys tiers.  L'autorisation est accordée en définissant l'indicateur [BindingRedirects](frlrfSystemSecurityPermissionsSecurityPermissionFlagClassTopic) sur la [classe SecurityPermission](frlrfSystemSecurityPermissionsSecurityPermissionClassTopic).  Pour plus d'informations, consultez [Autorisation de sécurité pour la redirection de liaison d'assembly](../../../../../docs/framework/configure-apps/assembly-binding-redirection-security-permission.md).  
  
## Exemple  
 L'exemple suivant montre comment rediriger une version d'assembly vers une autre.  
  
```  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="myAssembly"  
                              publicKeyToken="32ab4ba45e0a69a1"  
                              culture="neutral" />  
            <bindingRedirect oldVersion="1.0.0.0"  
                             newVersion="2.0.0.0"/>  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## Voir aussi  
 [Schéma des paramètres d'exécution](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)   
 [Schéma des fichiers de configuration](../../../../../docs/framework/configure-apps/file-schema/index.md)   
 [Redirection des versions d'assemblys](../../../../../docs/framework/configure-apps/redirect-assembly-versions.md)