---
title: "&lt;PreferComInsteadOfManagedRemoting&gt;, &#233;l&#233;ment | Microsoft Docs"
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
helpviewer_keywords: 
  - "<PreferComInsteadOfManagedRemoting> (élément)"
  - "PreferComInsteadOfManagedRemoting (élément)"
ms.assetid: a279a42a-c415-4e79-88cf-64244ebda613
caps.latest.revision: 17
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 17
---
# &lt;PreferComInsteadOfManagedRemoting&gt;, &#233;l&#233;ment
Spécifie si le runtime utilisera COM Interop au lieu de la communication à distance pour tous les appels au\-delà des limites du domaine d'application.  
  
## Syntaxe  
  
```  
<PreferComInsteadOfManagedRemoting enabled="true|false"/>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|`enabled`|Attribut requis.<br /><br /> Indique si le runtime utilisera COM Interop au lieu de la communication à distance au\-delà des limites du domaine d'application.|  
  
## Attribut enabled  
  
|Valeur|Description|  
|------------|-----------------|  
|`false`|Le runtime utilisera la communication à distance au\-delà des limites du domaine d'application.  Il s'agit de la valeur par défaut.|  
|`true`|Le runtime utilisera COM Interop au\-delà des limites du domaine d'application.|  
  
### Éléments enfants  
 Aucun.  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`runtime`|Contient des informations sur les liaisons d'assembly et l'opération garbage collection.|  
  
## Notes  
 Lorsque vous affectez à l'attribut `enabled` la valeur `true`, le runtime se comporte comme suit :  
  
-   L'exécution ne [IUnknown::QueryInterface](http://go.microsoft.com/fwlink/?LinkID=144867) requiert pas d'interface [IManagedObject](../../../../../ocs/framework/unmanaged-api/hosting/imanagedobject-interface.md) lorsqu'une interface [IUnknown](http://go.microsoft.com/fwlink/?LinkId=148003) entre dans le champ via une interface COM.  À la place, il construit un [Runtime Callable Wrapper](../../../../../docs/framework/interop/runtime-callable-wrapper.md) \(RCW\) autour de l'objet.  
  
-   Le runtime retourne E\_NOINTERFACE lorsqu'il reçoit un appel `QueryInterface` pour une interface [IManagedObject](../../../../../ocs/framework/unmanaged-api/hosting/imanagedobject-interface.md) pour tout [COM Callable Wrapper](../../../../../docs/framework/interop/com-callable-wrapper.md) \(CCW\) créé dans ce domaine.  
  
 Ces deux comportements garantissent que tous les appels via les interfaces COM entre objets managés au\-delà des limites du domaine d'application utilisent COM et COM Interop au lieu de la communication à distance.  
  
## Exemple  
 L'exemple suivant indique comment spécifier que le runtime doit utiliser COM Interop au\-delà des limites d'isolement :  
  
```  
<configuration>  
  <runtime>  
    <PreferComInsteadOfManagedRemoting enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## Voir aussi  
 [Schéma des paramètres d'exécution](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)   
 [Schéma des fichiers de configuration](../../../../../docs/framework/configure-apps/file-schema/index.md)