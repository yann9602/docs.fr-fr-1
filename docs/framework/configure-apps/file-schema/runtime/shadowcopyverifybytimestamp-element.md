---
title: "&lt;shadowCopyVerifyByTimestamp&gt;, &#233;l&#233;ment | Microsoft Docs"
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
  - "<shadowCopyTimeStampVerification> (élément)"
  - "shadowCopyTimeStampVerification (élément)"
ms.assetid: 2f1648e5-997b-435e-a4f9-d236c574c66c
caps.latest.revision: 7
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 7
---
# &lt;shadowCopyVerifyByTimestamp&gt;, &#233;l&#233;ment
Spécifie si les clichés instantanés utilisent le comportement au démarrage par défaut introduit par le [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] ou rétablissent le comportement au démarrage des versions antérieures du .NET Framework.  
  
## Syntaxe  
  
```  
<shadowCopyVerifyByTimestamp enabled="true|false" />  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|activé|Attribut requis.<br /><br /> Spécifie si les domaines d'application qui utilisent des clichés instantanés comparent les horodatages des assemblys au démarrage de façon à déterminer si un assembly a été mis à jour avant la création de son cliché instantané.|  
  
## Attribut enabled  
  
|Valeur|Description|  
|------------|-----------------|  
|true|Au démarrage, copie uniquement des assemblys mis à jour puisqu'ils ont été copiés en dernier vers le répertoire de cliché instantané.  Valeur par défaut pour [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)].|  
|false|Rétablit le comportement au démarrage des versions antérieures du .NET Framework, qui consiste à copier tous les fichiers au démarrage.|  
  
### Éléments enfants  
 Aucun.  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`runtime`|Contient des informations sur les liaisons d'assembly et l'opération garbage collection.|  
  
## Notes  
 Depuis le [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], les assemblys font l'objet de clichés instantanés uniquement si leurs horodatages indiquent qu'ils ont été modifiés depuis leur dernière copie dans le répertoire de clichés instantanés.  Cela améliore les temps de démarrage de nombreuses applications qui utilisent les clichés instantanés, comme décrit dans [Clichés instantanés d'assemblys](../../../../../docs/framework/app-domains/shadow-copy-assemblies.md).  Les applications qui ont un pourcentage et une fréquence élevé de mises à jour d'assembly ne peut pas bénéficier de cette modification du comportement.  Dans ce cas, vous pouvez utiliser cet élément pour restaurer le comportement depuis les précédentes versions de .NET Framework.  
  
## Exemple  
 L'exemple suivant indique comment désactiver le comportement au démarrage par défaut des clichés instantanés dans le [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] et rétablir le comportement au démarrage des versions antérieures du .NET Framework.  
  
```  
<configuration>  
   <runtime>  
      <shadowCopyVerifyByTimestamp enabled="false" />  
   </runtime>  
</configuration>  
```  
  
## Voir aussi  
 [Schéma des paramètres d'exécution](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)   
 [Schéma des fichiers de configuration](../../../../../docs/framework/configure-apps/file-schema/index.md)   
 [Clichés instantanés d'assemblys](../../../../../docs/framework/app-domains/shadow-copy-assemblies.md)