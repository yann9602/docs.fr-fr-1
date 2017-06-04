---
title: "&lt;bypassTrustedAppStrongNames&gt;, &#233;l&#233;ment | Microsoft Docs"
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
  - "<bypassTrustedAppStrongNames> (élément)"
  - "bypassTrustedAppStrongNames (élément)"
  - "fonctionnalité consistant à ignorer les noms forts"
  - "assemblys avec nom fort, charger dans des domaines d'application de confiance"
ms.assetid: 71b2ebf6-3843-41e2-ad52-ffa5cd083a40
caps.latest.revision: 18
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 18
---
# &lt;bypassTrustedAppStrongNames&gt;, &#233;l&#233;ment
Spécifie s'il faut ignorer la validation de noms forts sur les assemblys de confiance totale chargés dans un <xref:System.AppDomain> de confiance totale.  
  
## Syntaxe  
  
```  
<bypassTrustedAppStrongNames    
   enabled="true|false"/>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|`enabled`|Attribut requis.<br /><br /> Spécifie si la fonctionnalité consistant à ignorer la validation des noms forts pour les assemblys de confiance totale est activée.  Lorsque cette fonctionnalité est activée, l'exactitude des noms forts n'est pas validée lorsque l'assembly est chargé.  La valeur par défaut est `true`.|  
  
## Attribut enabled  
  
|Valeur|Description|  
|------------|-----------------|  
|`true`|Les signatures avec nom fort sur les assemblys de confiance totale ne sont pas validées lorsque les assemblys sont chargés dans un <xref:System.AppDomain> de confiance totale.  Il s'agit de la valeur par défaut.|  
|`false`|Les signatures avec nom fort sur les assemblys de confiance totale sont validées lorsque les assemblys sont chargés dans un <xref:System.AppDomain> de confiance totale.  Seule l'exactitude de la signature avec nom fort est vérifiée. La signature n'est pas comparée à un autre nom fort en vue d'établir une correspondance.|  
  
### Éléments enfants  
 Aucun  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`runtime`|Contient des informations sur les liaisons d'assembly et l'opération garbage collection.|  
  
## Notes  
 La fonctionnalité consistant à ignorer les noms forts évite la surcharge inhérente à la vérification des signatures avec nom fort des assemblys de confiance totale.  
  
 Cette fonctionnalité s'applique à tout assembly signé avec un nom fort qui présente les caractéristiques suivantes :  
  
-   Confiance totale sans la preuve <xref:System.Security.Policy.StrongName> \(par exemple, dispose de la preuve de zone `MyComputer` \).  
  
-   Chargé dans un <xref:System.AppDomain> de confiance totale.  
  
-   Chargé à partir d'un emplacement sous la propriété <xref:System.AppDomainSetup.ApplicationBase%2A> de ce <xref:System.AppDomain>.  
  
-   Sans signature différée.  
  
> [!NOTE]
>  Si la fonctionnalité consistant à ignorer la vérification a été désactivée pour toutes les applications de l'ordinateur en utilisant une clé de Registre, ce paramètre de fichier de configuration n'a aucun effet.  Pour plus d'informations, consultez [Comment : désactiver la fonctionnalité consistant à ignorer les noms forts](../../../../../docs/framework/app-domains/how-to-disable-the-strong-name-bypass-feature.md).  
  
## Exemple  
 L'exemple suivant indique comment spécifier le comportement qui valide la signature avec nom fort sur les assemblys de confiance totale.  
  
```  
<configuration>  
   <runtime>  
      <bypassTrustedAppStrongNames enabled="false"/>  
   </runtime>  
</configuration>  
```  
  
## Voir aussi  
 [Schéma des paramètres d'exécution](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)   
 [Schéma des fichiers de configuration](../../../../../docs/framework/configure-apps/file-schema/index.md)   
 [Comment : désactiver la fonctionnalité consistant à ignorer les noms forts](../../../../../docs/framework/app-domains/how-to-disable-the-strong-name-bypass-feature.md)