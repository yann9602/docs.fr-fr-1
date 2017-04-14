---
title: "&lt;supportPortability&gt;, &#233;l&#233;ment | Microsoft Docs"
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
  - "<supportPortability> (élément)"
  - "supportPortability (élément)"
ms.assetid: 6453ef66-19b4-41f3-b712-52d0c2abc9ca
caps.latest.revision: 9
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 9
---
# &lt;supportPortability&gt;, &#233;l&#233;ment
Spécifie qu'une application peut référencer le même assembly dans deux implémentations différentes du .NET Framework en désactivant le comportement par défaut qui considère les assemblys comme équivalents à des fins de portabilité de l'application.  
  
## Syntaxe  
  
```  
<supportPortability PKT="public_key_token" enabled="true|false"/>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|PKT|Attribut requis.<br /><br /> Spécifie le jeton de clé publique de l'assembly affecté, sous forme de chaîne.|  
|activé|Attribut facultatif.<br /><br /> Spécifie si la prise en charge de la portabilité entre les implémentations de l'assembly .NET Framework spécifié doit être activée.|  
  
## Attribut enabled  
  
|Valeur|Description|  
|------------|-----------------|  
|true|Active la prise en charge pour la portabilité entre les implémentations de l'assembly .NET Framework spécifié.  Il s'agit de la valeur par défaut.|  
|false|Désactivez le support pour la portabilité entre les implémentations de l'assembly .NET Framework spécifié.  Cela permet à l'application d'avoir des références à plusieurs implémentations de l'assembly spécifié.|  
  
### Éléments enfants  
 Aucun  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`runtime`|Contient des informations sur les liaisons d'assembly et l'opération garbage collection.|  
|`assemblyBinding`|Contient des informations sur la redirection des versions des assemblys et sur l'emplacement de ces derniers.|  
  
## Notes  
 Depuis le [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], le support est fourni automatiquement pour les applications qui peuvent utiliser l'une ou l'autre des deux implémentations du .NET Framework, par exemple l'implémentation du .NET Framework ou le .NET Framework pour l'implémentation Silverlight.  Les deux implémentations d'un assembly .NET Framework particulier sont vues comme équivalentes par le binder d'assembly.  Dans quelques scénarios, cette fonctionnalité de la portabilité de l'application provoque des problèmes.  Dans ces scénarios, l'élément `<supportPortability>` peut être utilisé pour désactiver la fonctionnalité.  
  
 Ce type de scénario correspond à un assembly qui doit référencer à la fois l'implémentation du .NET Framework et le .NET Framework pour l'implémentation Silverlight d'un assembly de référence particulier.  Par exemple, un concepteur XAML écrit dans Windows Presentation Foundation \(WPF\) devra peut\-être référencer à la fois l'implémentation du bureau WPF pour l'interface utilisateur du concepteur et le sous\-ensemble de WPF qui est fourni avec l'implémentation Silverlight.  Par défaut, les références séparées provoquent une erreur du compilateur, parce que la liaison d'assembly considère les deux assemblys comme équivalents.  Cet élément désactive le comportement par défaut et permet à la compilation de réussir.  
  
> [!IMPORTANT]
>  Pour que le compilateur passe les informations à la logique de liaison d'assembly du common language runtime, vous devez utiliser l'option du compilateur `/appconfig` pour spécifier l'emplacement du fichier app.config qui contient cet élément.  
  
## Exemple  
 L'exemple suivant permet à une application d'avoir des références à la fois à l'implémentation de .NET Framework et au .NET Framework pour l'implémentation Silverlight de tout assembly .NET Framework qui existe dans les deux implémentations.  L'option de compilateur `/appconfig` doit être utilisée pour spécifier l'emplacement de ce fichier app.config.  
  
```  
<configuration>  
   <runtime>  
      <assemblyBinding>  
         <supportPortability PKT="7cec85d7bea7798e" enable="false"/>  
         <supportPortability PKT="31bf3856ad364e35" enable="false"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## Voir aussi  
 [\/appconfig \(Options du compilateur C\#\)](http://msdn.microsoft.com/library/ee523958.aspx)   
 [.NET Framework Assembly Unification Overview](http://msdn.microsoft.com/fr-fr/8d8cc65e-031d-463b-bde3-2c6dc2e3bc48)