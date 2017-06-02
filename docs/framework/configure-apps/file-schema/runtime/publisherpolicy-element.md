---
title: "&lt;publisherPolicy&gt;, &#233;l&#233;ment | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/publisherPolicy"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly/publisherPolicy"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#publisherPolicy"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<publisherPolicy> (élément)"
  - "balises conteneurs, <publisherPolicy> (élément)"
  - "publisherPolicy (élément)"
ms.assetid: 4613407e-d0a8-4ef2-9f81-a6acb9fdc7d4
caps.latest.revision: 18
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 17
---
# &lt;publisherPolicy&gt;, &#233;l&#233;ment
Spécifie si le runtime applique la stratégie de l'éditeur.  
  
## Syntaxe  
  
```  
  
<publisherPolicy apply="yes|no"/>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|`apply`|Spécifie si la stratégie de l'éditeur doit être appliquée.|  
  
## appliquer l'attribut  
  
|Valeur|Description|  
|------------|-----------------|  
|`yes`|Applique la stratégie de l'éditeur.  Il s'agit de l'option par défaut.|  
|`no`|N'applique pas la stratégie de l'éditeur.|  
  
### Éléments enfants  
 Aucun.  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`runtime`|Contient des informations sur les liaisons d'assembly et l'opération garbage collection.|  
  
## Notes  
 Lorsqu'un fournisseur de composant publie une nouvelle version d'un assembly, il peut inclure une stratégie de l'éditeur pour que les applications qui utilisent l'ancienne version utilisent désormais la nouvelle.  Pour spécifier si la stratégie de l'éditeur doit être appliquée à un assembly particulier, placez l'élément **\<publisherPolicy\>** dans l'élément **\<dependentAssembly\>**.  
  
 La valeur par défaut de l'attribut **apply** est **yes**.  L'assignation de la valeur **no** à l'attribut **apply** a pour effet d'annuler tout paramétrage précédent de cet attribut à la valeur **yes**.  
  
 Une autorisation est nécessaire pour qu'une application ignore explicitement la stratégie d'éditeur à l'aide de l'élément [\<publisherPolicy apply\="no"\/\>](../../../../../docs/framework/configure-apps/file-schema/runtime/publisherpolicy-element.md) dans le fichier de configuration de l'application.  L'autorisation est accordée en définissant l'indicateur [BindingRedirects](frlrfSystemSecurityPermissionsSecurityPermissionFlagClassTopic) sur la [classe SecurityPermission](frlrfSystemSecurityPermissionsSecurityPermissionClassTopic).  Pour plus d'informations, consultez [Autorisation de sécurité pour la redirection de liaison d'assembly](../../../../../docs/framework/configure-apps/assembly-binding-redirection-security-permission.md).  
  
## Exemple  
 L'exemple suivant désactive la stratégie de l'éditeur pour l'assembly `myAssembly`.  
  
```  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="myAssembly"  
                                    publicKeyToken="32ab4ba45e0a69a1"  
                                    culture="neutral" />  
            <publisherPolicy apply="no"/>  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## Voir aussi  
 [Schéma des paramètres d'exécution](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)   
 [Schéma des fichiers de configuration](../../../../../docs/framework/configure-apps/file-schema/index.md)   
 [Méthode de localisation des assemblys par le runtime](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)   
 [Redirection des versions d'assemblys](../../../../../docs/framework/configure-apps/redirect-assembly-versions.md)