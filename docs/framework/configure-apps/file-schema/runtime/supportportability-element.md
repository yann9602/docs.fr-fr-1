---
title: "&lt;supportPortability&gt; élément"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- supportPortability element
- <supportPortability> element
ms.assetid: 6453ef66-19b4-41f3-b712-52d0c2abc9ca
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b46d12ecebae17b7cfe2168b6313be45ad5b04d4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ltsupportportabilitygt-element"></a>&lt;supportPortability&gt; élément
Spécifie qu’une application peut référencer le même assembly dans deux implémentations différentes du .NET Framework, en désactivant le comportement par défaut qui traite les assemblys de façon équivalente à des fins de portabilité des applications.  
  
 \<configuration > élément  
\<runtime > élément  
\<assemblyBinding > élément  
\<supportPortability > élément  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<supportPortability PKT="public_key_token" enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|PKT|Attribut requis.<br /><br /> Spécifie le jeton de clé publique de l’assembly affecté, sous forme de chaîne.|  
|enabled|Attribut facultatif.<br /><br /> Spécifie si la prise en charge pour la portabilité entre les implémentations de l’assembly .NET Framework spécifié doit être activée.|  
  
## <a name="enabled-attribute"></a>Attribut enabled  
  
|Valeur|Description|  
|-----------|-----------------|  
|true|Activer la prise en charge pour la portabilité entre les implémentations de l’assembly .NET Framework spécifié. Il s'agit de la valeur par défaut.|  
|false|Désactiver la prise en charge pour la portabilité entre les implémentations de l’assembly .NET Framework spécifié. Cela permet à l’application d’avoir des références à plusieurs implémentations de l’assembly spécifié.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`runtime`|Contient des informations sur les liaisons d’assembly et l’opération garbage collection.|  
|`assemblyBinding`|Contient des informations à propos de la redirection des versions d'assemblys et de l'emplacement de ces derniers.|  
  
## <a name="remarks"></a>Remarques  
 Compter les [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], prise en charge est fournie automatiquement pour les applications qui peuvent utiliser une des deux implémentations du .NET Framework, par exemple l’implémentation du .NET Framework ou .NET Framework pour l’implémentation Silverlight. Les deux implémentations d’un assembly .NET Framework particulier sont considérées comme équivalents par le binder d’assembly. Dans certains scénarios, cette fonctionnalité de portabilité application pose des problèmes. Dans ces scénarios, le `<supportPortability>` élément peut être utilisé pour désactiver la fonctionnalité.  
  
 Un tel scénario est un assembly qui doit faire référence à l’implémentation du .NET Framework et le .NET Framework pour l’implémentation Silverlight d’un assembly de référence particulier. Par exemple, un concepteur XAML écrit dans Windows Presentation Foundation (WPF) devrez peut-être faire référence à la fois l’implémentation de bureau WPF pour l’interface d’utilisateur du concepteur et le sous-ensemble de WPF qui est inclus dans l’implémentation de Silverlight. Par défaut, les références séparées provoquent une erreur du compilateur parce que la liaison d’assembly considère les deux assemblys comme équivalents. Cet élément désactive le comportement par défaut et permet la compilation de réussir.  
  
> [!IMPORTANT]
>  Afin que le compilateur passe les informations à la logique de liaison d’assembly du common language runtime, vous devez utiliser le `/appconfig` option du compilateur pour spécifier l’emplacement du fichier app.config qui contient cet élément.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant permet à une application d’avoir des références à l’implémentation du .NET Framework et le .NET Framework pour l’implémentation Silverlight de tout assembly .NET Framework qui existe dans les deux implémentations. Le `/appconfig` option du compilateur doit être utilisée pour spécifier l’emplacement de ce fichier app.config.  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding>  
         <supportPortability PKT="7cec85d7bea7798e" enable="false"/>  
         <supportPortability PKT="31bf3856ad364e35" enable="false"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [/appconfig (Options du compilateur c#)](http://msdn.microsoft.com/library/ee523958.aspx)  
 [Vue d’ensemble de .NET framework Assembly Unification](http://msdn.microsoft.com/en-us/8d8cc65e-031d-463b-bde3-2c6dc2e3bc48)
