---
title: "&lt;NetFx45_CultureAwareComparerGetHashCode_LongStrings&gt; (&#233;l&#233;ment) | Microsoft Docs"
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
  - "NetFx45_CultureAwareComparerGetHashCode_LongStrings (élément)"
  - "<NetFx45_CultureAwareComparerGetHashCode_LongStrings> (élément)"
  - "GetHashCode (méthode)"
  - "codes de hachage, calcul"
ms.assetid: 3a5f38d1-ebc8-44de-aaeb-2929f6e6b48f
caps.latest.revision: 8
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 8
---
# &lt;NetFx45_CultureAwareComparerGetHashCode_LongStrings&gt; (&#233;l&#233;ment)
Spécifie si le runtime utilise une quantité de mémoire fixe pour calculer les codes de hachage pour la méthode <xref:System.StringComparer.GetHashCode%2A?displayProperty=fullName>.  
  
 \<configuration\>  
\<runtime\>  
\<NetFx45\_CultureAwareComparerGetHashCode\_LongStrings\>  
  
## Syntaxe  
  
```vb  
<NetFx45_CultureAwareComparerGetHashCode_LongStrings enabled="0|1">  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|`enabled`|Attribut requis.<br /><br /> Spécifie si le CLR \(Common Langage Runtime\) alloue une quantité de mémoire fixe lors du calcul des codes de hachage.|  
  
## Attribut enabled  
  
|Valeur|Description|  
|------------|-----------------|  
|0|Le Common Langage Runtime alloue une quantité de mémoire variable à la méthode <xref:System.StringComparer.GetHashCode%2A?displayProperty=fullName> pour calculer les codes de hachage. Il s'agit de la valeur par défaut.|  
|1|Le Common Langage Runtime alloue une quantité de mémoire fixe à la méthode <xref:System.StringComparer.GetHashCode%2A?displayProperty=fullName> pour calculer les codes de hachage.|  
  
### Éléments enfants  
 Aucun  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`runtime`|Contient des informations sur les options d'initialisation du runtime.|  
  
## Notes  
 Par défaut, le CLR alloue une quantité de mémoire variable à la méthode <xref:System.StringComparer.GetHashCode%2A?displayProperty=fullName>, et une exception <xref:System.ArgumentException> peut être levée lorsque la méthode tente de calculer le code de hachage de chaînes très longues \(de plusieurs millions de caractères\). Ajouter cet élément dans un fichier de configuration de l'application et affecter la valeur « 1 » à son attribut `enabled` vous permet de spécifier que la méthode <xref:System.StringComparer.GetHashCode%2A?displayProperty=fullName> utilise un autre algorithme qui alloue une quantité de mémoire fixe au calcul du code de hachage.  
  
> [!IMPORTANT]
>  L'élément `<NetFx45_CultureAwareComparerGetHashCode_LongStrings>` n'est pas utilisé dans [!INCLUDE[win8](../../../../../includes/win8-md.md)] et ses versions ultérieures.  
  
## Voir aussi  
 <xref:System.StringComparer.GetHashCode%2A?displayProperty=fullName>   
 [Schéma des paramètres d'exécution](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)   
 [Schéma des fichiers de configuration](../../../../../docs/framework/configure-apps/file-schema/index.md)