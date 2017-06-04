---
title: "&lt;gcAllowVeryLargeObjects&gt;, &#233;l&#233;ment | Microsoft Docs"
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
  - "<gcAllowVeryLargeObjects> (élément)"
  - "gcAllowVeryLargeObjects (élément)"
ms.assetid: 5c7ea24a-39ac-4e5f-83b7-b9f9a1b556ab
caps.latest.revision: 10
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 10
---
# &lt;gcAllowVeryLargeObjects&gt;, &#233;l&#233;ment
Sur les plateformes 64 bits, active les tableaux supérieurs à 2 gigaoctets \(GB\) en taille totale.  
  
## Syntaxe  
  
```  
<gcAllowVeryLargeObjects    
   enabled="true|false" />  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|`enabled`|Attribut requis.<br /><br /> Spécifie si les tableaux supérieurs à 2 Go de la taille totale sont activés sur les plateformes 64 bits.|  
  
## Attribut enabled  
  
|Valeur|Description|  
|------------|-----------------|  
|`false`|Les tableaux plus grands que 2 GB en taille totale ne sont pas activées.  Il s'agit de la valeur par défaut.|  
|`true`|Les tableaux de taille totale supérieure à 2 GB sont activés sur les plateformes 64 bits.|  
  
### Éléments enfants  
 Aucun  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`runtime`|Contient des informations sur les options d'initialisation du runtime.|  
  
## Notes  
 L'utilisation de cet élément dans votre fichier de configuration d'application autorise les tableaux supérieurs à 2 Go en taille, mais ne modifie pas d'autres limites à la taille d'objets ou à la taille de tableaux :  
  
-   Le nombre maximal d'éléments dans un tableau est <xref:System.UInt32.MaxValue?displayProperty=fullName>.  
  
-   L'index maximal d'une unique dimension est 2 147 483 591 \(0x7FFFFFC7\) pour les tableaux d'octets et les tableaux de structures codées sur un octet, et 2 146 435 071 \(0X7FEFFFFF\) pour d'autres types.  
  
-   La taille maximale pour les chaînes et les objets autres que les tableaux reste inchangée.  
  
> [!CAUTION]
>  Avant d'activer cette fonctionnalité, vérifiez que votre application ne comprend pas code unsafe qui suppose que les tableaux soient inférieure à 2 Go en taille.  Par exemple, le code unsafe qui utilise des tableaux comme tampons peut être susceptible à dépassements de mémoire tampon si il est écrit sur l'hypothèse que les tableaux ne dépasseront pas 2 Go.  
  
## Exemple  
 L'exemple suivant montre comment activer cette fonctionnalité pour une application.  
  
```  
<configuration>  
  <runtime>  
    <gcAllowVeryLargeObjects enabled="true" />  
  </runtime>  
</configuration>  
```  
  
## Voir aussi  
 [Schéma des paramètres d'exécution](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)   
 [Schéma des fichiers de configuration](../../../../../docs/framework/configure-apps/file-schema/index.md)