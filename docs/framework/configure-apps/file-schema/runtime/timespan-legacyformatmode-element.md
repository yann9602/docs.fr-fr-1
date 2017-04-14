---
title: "&lt;TimeSpan_LegacyFormatMode&gt;, &#233;l&#233;ment | Microsoft Docs"
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
  - "<TimeSpan_LegacyFormatMode> (élément)"
  - "TimeSpan_LegacyFormatMode (élément)"
ms.assetid: 865e7207-d050-4442-b574-57ea29d5e2d6
caps.latest.revision: 8
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 8
---
# &lt;TimeSpan_LegacyFormatMode&gt;, &#233;l&#233;ment
Détermine si le runtime conserve le comportement hérité dans les opérations de mise en forme avec les valeurs <xref:System.TimeSpan?displayProperty=fullName>.  
  
## Syntaxe  
  
```  
<TimeSpan_LegacyFormatMode    
   enabled="true|false"/>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|`enabled`|Attribut requis.<br /><br /> Spécifie si l'exécution utilise le comportement de formatage hérité avec les valeurs <xref:System.TimeSpan?displayProperty=fullName>.|  
  
## Attribut enabled  
  
|Valeur|Description|  
|------------|-----------------|  
|`false`|Le runtime ne restaure pas le comportement de mise en forme hérité.|  
|`true`|Le runtime restaure le comportement de mise en forme hérité.|  
  
### Éléments enfants  
 Aucun.  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`runtime`|Contient des informations sur les options d'initialisation du runtime.|  
  
## Notes  
 Dans le [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], la structure <xref:System.TimeSpan?displayProperty=fullName> implémente l'interface <xref:System.IFormattable> et prend en charge des opérations de formatage avec des chaînes de format standard et personnalisées.  Si une méthode d'analyse rencontre un spécificateur de format ou une chaîne de format non pris en charge, il lève une exception <xref:System.FormatException>.  
  
 Dans les versions antérieures du .NET Framework, la structure <xref:System.TimeSpan> n'implémentait pas <xref:System.IFormattable> et ne prenait pas en charge les chaînes de format.  Toutefois, de nombreux développeurs ont supposé par erreur que <xref:System.TimeSpan> ne prenait pas en charge un ensemble de chaînes de format et ils les ont utilisées dans des [opérations de mise en forme composite](../../../../../docs/standard/base-types/composite-formatting.md) avec des méthodes telles que <xref:System.String.Format%2A?displayProperty=fullName>.  Si un type implémente <xref:System.IFormattable> et prend en charge des chaînes de format, les appels aux méthodes de format avec des chaînes de format non prises en charge lèvent habituellement un <xref:System.FormatException>.  Toutefois, étant donné que <xref:System.TimeSpan> n'a pas implémenté <xref:System.IFormattable>, le runtime a ignoré la chaîne de format et à la place a appelé la méthode <xref:System.TimeSpan.ToString?displayProperty=fullName>.  Cela signifie que, bien que les chaînes de format n'avaient aucun effet sur l'opération de mise en forme, leur présence n'a pas provoqué de <xref:System.FormatException>.  
  
 Pour les cas dans lesquels le code hérité passe une méthode de mise en forme composite et une chaîne de mise en forme non valide, et que ce code ne peut pas être recompilé, vous pouvez utiliser l'élément `<TimeSpan_LegacyFormatMode>` pour restaurer le comportement <xref:System.TimeSpan> hérité.  Lorsque vous affectez à l'attribut `enabled` de cet élément la valeur `true`, la méthode de mise en forme composite provoque un appel à <xref:System.TimeSpan.ToString?displayProperty=fullName> plutôt qu'à <xref:System.TimeSpan.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=fullName>, et <xref:System.FormatException> n'est pas levé.  
  
## Exemple  
 L'exemple suivant instancie un objet <xref:System.TimeSpan> et essaie de le mettre en forme avec la méthode <xref:System.String.Format%28System.String%2CSystem.Object%29?displayProperty=fullName> en utilisant une chaîne de format standard non prise en charge.  
  
 [!code-csharp[TimeSpan.BreakingChanges#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/timespan.breakingchanges/cs/legacyformatmode1.cs#1)]
 [!code-vb[TimeSpan.BreakingChanges#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/timespan.breakingchanges/vb/legacyformatmode1.vb#1)]  
  
 Lorsque vous exécutez l'exemple sur le [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)] ou sur une version antérieure, il affiche la sortie suivante :  
  
```  
12:30:45  
```  
  
 Cela diffère d'une façon marquée de la sortie si vous exécutez l'exemple sur [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)]:  
  
```  
Invalid Format  
```  
  
 Toutefois, si vous ajoutez le fichier de configuration suivant au répertoire de l'exemple, puis exécutez l'exemple sur [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] ou une version ultérieure, la sortie est identique à celle produite par l'exemple lorsqu'il est exécuté sur [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)].  
  
```  
<?xml version ="1.0"?>  
<configuration>  
   <runtime>  
      <TimeSpan_LegacyFormatMode enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## Voir aussi  
 [Schéma des paramètres d'exécution](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)   
 [Schéma des fichiers de configuration](../../../../../docs/framework/configure-apps/file-schema/index.md)