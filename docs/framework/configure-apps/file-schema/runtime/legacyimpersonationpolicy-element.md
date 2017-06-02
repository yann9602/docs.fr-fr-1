---
title: "&lt;legacyImpersonationPolicy&gt;, &#233;l&#233;ment | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#legacyImpersonationPolicy"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/legacyImpersonationPolicy"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<legacyImpersonationPolicy> (élément)"
  - "legacyImpersonationPolicy (élément)"
ms.assetid: 6e00af10-42f3-4235-8415-1bb2db78394e
caps.latest.revision: 15
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 12
---
# &lt;legacyImpersonationPolicy&gt;, &#233;l&#233;ment
Spécifie que l'identité Windows n'est pas transmise entre des points asynchrones, quels que soient les paramètres de flux du contexte d'exécution sur le thread actif.  
  
## Syntaxe  
  
```  
<legacyImpersonationPolicy    
   enabled="true|false"/>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|`enabled`|Attribut requis.<br /><br /> Spécifie que <xref:System.Security.Principal.WindowsIdentity> n'est pas transmis entre des points asynchrones, quels que soient les paramètres de flux de <xref:System.Threading.ExecutionContext> sur le thread actif.|  
  
## Attribut enabled  
  
|Valeur|Description|  
|------------|-----------------|  
|`false`|<xref:System.Security.Principal.WindowsIdentity> est transmis entre des points asynchrones en fonction des paramètres de flux de <xref:System.Threading.ExecutionContext> pour le thread actif.  Il s'agit de la valeur par défaut.|  
|`true`|<xref:System.Security.Principal.WindowsIdentity> n'est pas transmis entre des points asynchrones, quels que soient les paramètres de flux de <xref:System.Threading.ExecutionContext> sur le thread actif.|  
  
### Éléments enfants  
 Aucun  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`runtime`|Contient des informations sur les liaisons d'assembly et l'opération garbage collection.|  
  
## Notes  
 Dans les versions 1.0 et 1.1 du .NET Framework, <xref:System.Security.Principal.WindowsIdentity> n'est pas transmis entre des points asynchrones définis par l'utilisateur.  Le .NET Framework version 2.0 comprend un objet <xref:System.Threading.ExecutionContext> qui contient des informations à propos du thread en cours d'exécution et les transmet entre des points asynchrones d'un domaine d'application.  <xref:System.Security.Principal.WindowsIdentity> est également passé dans le cadre du flux d'informations entre les points asynchrones. En d'autres termes, s'il existe un contexte d'emprunt d'identité, il fera également partie du flux transmis.  Cet élément permet d'empêcher la transmission de <xref:System.Security.Principal.WindowsIdentity> entre des points asynchrones.  
  
> [!NOTE]
>  Le Common Language Runtime \(CLR\) est informé des opérations d'emprunt d'identité exécutées à l'aide de code managé uniquement, et non des emprunts d'identité exécutés en dehors du code managé, par exemple via un appel de code non managé ou via des appels directs aux fonctions Win32.  Seuls les objets <xref:System.Security.Principal.WindowsIdentity> managés peuvent être transmis entre des points asynchrones, sauf si l'élément `alwaysFlowImpersonationPolicy` a la valeur true \(`<alwaysFlowImpersonationPolicy enabled="true"/>`\).  La définition de l'élément `alwaysFlowImpersonationPolicy` sur la valeur true spécifie que l'identité Windows est toujours transmise entre des points asynchrones, indépendamment du mode d'exécution de l'emprunt d'identité.  Pour plus d'informations sur la transmission d'un emprunt d'identité non managé entre des points asynchrones, consultez [\<alwaysFlowImpersonationPolicy\>, élément](../../../../../docs/framework/configure-apps/file-schema/runtime/alwaysflowimpersonationpolicy-element.md).  
  
 Cet élément peut être utilisé uniquement dans le fichier de configuration de l'application.  
  
 Vous pouvez modifier ce comportement par défaut de deux autres façons :  
  
1.  Dans le code managé, thread par thread.  
  
     Vous pouvez supprimer le flux thread par thread en modifiant les paramètres <xref:System.Threading.ExecutionContext> et <xref:System.Security.SecurityContext> à l'aide de la méthode <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=fullName>, <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=fullName> ou <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=fullName>.  
  
2.  Dans l'appel à l'interface d'hébergement non managée pour charger le Common Language Runtime.  
  
     Si vous utilisez une interface d'hébergement non managée \(au lieu d'un simple fichier exécutable managé\) pour charger le Common Language Runtime, vous pouvez spécifier un indicateur spécial dans l'appel à la fonction [CorBindToRuntimeEx, fonction](../../../../../ocs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md).  Pour activer le mode de compatibilité pour l'ensemble du processus, affectez la valeur STARTUP\_LEGACY\_IMPERSONATION au paramètre `flags` de [CorBindToRuntimeEx, fonction](../../../../../ocs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md).  
  
## Exemple  
 L'exemple suivant montre comment spécifier le comportement hérité \(legacy\) qui ne transmet pas l'identité Windows entre des points asynchrones.  
  
```  
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## Voir aussi  
 [Schéma des paramètres d'exécution](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)   
 [Schéma des fichiers de configuration](../../../../../docs/framework/configure-apps/file-schema/index.md)