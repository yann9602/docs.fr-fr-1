---
title: "&lt;enforceFIPSPolicy&gt; &#233;l&#233;ment | Microsoft Docs"
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
  - "<enforceFIPSPolicy>, élément"
  - "enforceFIPSPolicy, élément"
  - "FIPS (Federal Information Processing Standards)"
  - "FIPS"
ms.assetid: c35509c4-35cf-43c0-bb47-75e4208aa24e
caps.latest.revision: 7
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 7
---
# &lt;enforceFIPSPolicy&gt; &#233;l&#233;ment
Spécifie s'il faut appliquer une condition de configuration de l'ordinateur que les algorithmes de chiffrement doivent être conformes aux normes FIPS \(Federal Information Processing Standards\).  
  
## Syntaxe  
  
```  
<enforceFIPSPolicy enabled="true|false" />  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|activé|Attribut requis.<br /><br /> Spécifie s'il faut activer l'application d'une spécification de configuration de l'ordinateur que les algorithmes de chiffrement doivent être conformes avec FIPS.|  
  
## Attribut enabled  
  
|Valeur|Description|  
|------------|-----------------|  
|`true`|Si votre ordinateur est configuré pour exiger des algorithmes de chiffrement conformes à FIPS, cette spécification est appliquée.  Si une classe implémente un algorithme qui n'est pas conforme FIPS, les constructeurs ou les méthodes `Create` pour cette classe lèvent des exceptions lorsqu'ils sont exécutés sur cet ordinateur.  Il s'agit de la valeur par défaut.|  
|`false`|Les algorithmes de chiffrement qui sont utilisés par l'application ne sont pas requis pour être conformes à FIPS, indépendamment de la configuration de l'ordinateur.|  
  
### Éléments enfants  
 Aucun  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`runtime`|Contient des informations sur les liaisons d'assembly et l'opération garbage collection.|  
  
## Notes  
 À compter de .NET Framework 2.0, la création de classes qui implémentent les algorithmes de chiffrement est contrôlée par la configuration de l'ordinateur.  Si l'ordinateur est configuré pour exiger des algorithmes conformes à la norme FIPS, et qu'une classe implémente un algorithme qui n'est pas conforme à FIPS, toute tentative de créer une instance de cette classe lève une exception.  Les constructeurs lèvent une exception <xref:System.InvalidOperationException> et les méthodes `Create` lèvent une exception <xref:System.Reflection.TargetInvocationException> avec une exception interne <xref:System.InvalidOperationException>.  
  
 Si votre application est exécutée sur les ordinateurs dont les configurations requièrent une conformité avec FIPS, et que votre application utilise un algorithme qui n'est pas conforme FIPS, vous pouvez utiliser cet élément dans votre fichier de configuration pour empêcher le CLR d'appliquer la conformité FIPS.  Cet élément a été introduit dans [!INCLUDE[net_v20SP1_long](../../../../../includes/net-v20sp1-long-md.md)].  
  
## Exemple  
 L'exemple suivant montre comment empêcher le CLR d'appliquer la conformité FIPS.  
  
```  
<configuration>  
    <runtime>  
        <enforceFIPSPolicy enabled="false"/>  
    </runtime>  
</configuration>  
```  
  
## Voir aussi  
 [Schéma des paramètres d'exécution](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)   
 [Schéma des fichiers de configuration](../../../../../docs/framework/configure-apps/file-schema/index.md)   
 [Modèle de chiffrement](../../../../../docs/standard/security/cryptography-model.md)