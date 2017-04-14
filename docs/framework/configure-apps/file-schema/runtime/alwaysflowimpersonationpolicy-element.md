---
title: "&lt;alwaysFlowImpersonationPolicy&gt;, &#233;l&#233;ment | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/alwaysFlowImpersonationPolicy"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#alwaysFlowImpersonationPolicy"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<alwaysFlowImpersonationPolicy> (élément)"
  - "alwaysFlowImpersonationPolicy (élément)"
ms.assetid: ee622801-9e46-470b-85ab-88c4b1dd2ee1
caps.latest.revision: 9
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 7
---
# &lt;alwaysFlowImpersonationPolicy&gt;, &#233;l&#233;ment
Spécifie que l'identité Windows est toujours transmise entre des points asynchrones, indépendamment du mode d'exécution de l'emprunt d'identité.  
  
## Syntaxe  
  
```  
<alwaysFlowImpersonationPolicy    
  enabled="true|false"/>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|`enabled`|Attribut requis.<br /><br /> Indique si l'identité Windows est transmise entre des points asynchrones.|  
  
## Attribut enabled  
  
|Valeur|Description|  
|------------|-----------------|  
|`false`|L'identité Windows n'est pas transmise entre des points asynchrones, à moins que l'emprunt d'identité soit exécuté par l'intermédiaire de méthodes managées telles que <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A>.  Il s'agit de la valeur par défaut.|  
|`true`|Spécifie que l'identité Windows est toujours transmise entre des points asynchrones, indépendamment du mode d'exécution de l'emprunt d'identité.|  
  
### Éléments enfants  
 Aucun  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`runtime`|Contient des informations sur les liaisons d'assembly et l'opération garbage collection.|  
  
## Notes  
 Dans les versions 1.0 et 1.1 du .NET Framework, l'identité Windows n'est pas transmise entre des points asynchrones.  Le .NET Framework version 2.0 comprend un objet <xref:System.Threading.ExecutionContext> qui contient des informations à propos du thread en cours d'exécution et les transmet entre des points asynchrones d'un domaine d'application.  <xref:System.Security.Principal.WindowsIdentity> est également transmis dans le cadre des informations passées entre des points asynchrones, à condition que l'emprunt d'identité ait été exécuté à l'aide de méthodes managées telles que <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A> et pas par d'autres moyens, tels qu'un appel de code non managé à des méthodes natives.  Cet élément est utilisé pour spécifier la transmission de l'identité Windows entre des points asynchrones, indépendamment du mode d'exécution de l'emprunt d'identité.  
  
 Vous pouvez modifier ce comportement par défaut de deux autres façons :  
  
1.  Dans le code managé, thread par thread.  
  
     Vous pouvez supprimer le flux thread par thread en modifiant les paramètres <xref:System.Threading.ExecutionContext> et <xref:System.Security.SecurityContext> à l'aide de la méthode <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=fullName>, <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=fullName> ou <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=fullName>.  
  
2.  Dans l'appel à l'interface d'hébergement non managée pour charger le Common Language Runtime.  
  
     Si vous utilisez une interface d'hébergement non managée \(au lieu d'un simple fichier exécutable managé\) pour charger le Common Language Runtime, vous pouvez spécifier un indicateur spécial dans l'appel à la fonction [CorBindToRuntimeEx, fonction](../../../../../ocs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md).  Pour activer le mode de compatibilité pour l'ensemble du processus, affectez la valeur STARTUP\_ALWAYSFLOW\_IMPERSONATION au paramètre `flags` de [CorBindToRuntimeEx, fonction](../../../../../ocs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md).  
  
## Fichier de configuration  
 Cet élément peut être utilisé uniquement dans le fichier de configuration de l'application.  
  
## Exemple  
 L'exemple suivant montre comment spécifier la transmission de l'identité Windows entre des points asynchrones, même si l'emprunt d'identité est effectué par d'autres moyens que les méthodes managées.  
  
```  
<configuration>  
  <runtime>  
    <alwaysFlowImpersonationPolicy enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## Voir aussi  
 [Schéma des paramètres d'exécution](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)   
 [Schéma des fichiers de configuration](../../../../../docs/framework/configure-apps/file-schema/index.md)   
 [\<legacyImpersonationPolicy\>, élément](../../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md)