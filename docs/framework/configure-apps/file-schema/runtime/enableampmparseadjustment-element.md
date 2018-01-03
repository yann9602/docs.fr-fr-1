---
title: "&lt;EnableAmPmParseAdjustment&gt; élément"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fda998a5-f538-4f8b-a18c-ee7f35e16938
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ed01035d7d5b154ebc6541eb6ac3dbae6a413fbc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltenableampmparseadjustmentgt-element"></a>&lt;EnableAmPmParseAdjustment&gt; élément
Détermine si date et heure de méthodes d’analyse utilisent un ensemble ajusté de règles pour analyser des chaînes de date qui contiennent un jour, un mois, une heure et un indicateur AM/PM.  
  
 \<configuration>  
 \<runtime >  
\<EnableAmPmParseAdjustment >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<EnableAmPmParseAdjustment enabled="0"|"1" />  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|`enabled`|Attribut requis.<br /><br /> Spécifie si date et heure de méthodes d’analyse utilisent un ensemble ajusté de règles pour analyser des chaînes de date qui contiennent uniquement un jour, le mois, le heure et l’indicateur AM/PM.|  
  
### <a name="enabled-attribute"></a>Attribut enabled  
  
|Valeur|Description|  
|-----------|-----------------|  
|0|Date et heure de méthodes d’analyse n’utilisent pas de règles ajustés pour analyser des chaînes de date qui contiennent uniquement un jour, le mois, le heure et l’indicateur AM/PM.|  
|1|Date et heure de l’analyse de méthodes utilisent des règles ajustés pour analyser des chaînes de date qui contiennent uniquement un jour, le mois, le heure et l’indicateur AM/PM.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`runtime`|Contient des informations sur les options d'initialisation du runtime.|  
  
## <a name="remarks"></a>Notes  
 Le `<EnableAmPmParseAdjustment>` élément contrôle la façon dont les méthodes suivantes analysent une chaîne de date qui contient un numéro du jour et le mois, suivi d’une heure et un indicateur AM/PM (par exemple, « 4/10 6 AM ») :  
  
-   <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>  
  
-   <xref:System.DateTimeOffset.Parse%2A?displayProperty=nameWithType>  
  
-   <xref:System.DateTime.TryParse%2A?displayProperty=nameWithType>  
  
-   <xref:System.DateTimeOffset.TryParse%2A?displayProperty=nameWithType>  
  
-   <xref:System.Convert.ToDateTime%2A?displayProperty=nameWithType>  
  
 Aucune des autres modèles ne sont affectés.  
  
 Le `<EnableAmPmParseAdjustment>` élément n’a aucun effet le <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType>, <xref:System.DateTime.TryParseExact%2A?displayProperty=nameWithType>, <xref:System.DateTimeOffset.ParseExact%2A?displayProperty=nameWithType>, et <xref:System.DateTimeOffset.TryParseExact%2A?displayProperty=nameWithType> méthodes.  
  
> [!IMPORTANT]
>  Dans le .NET Core et .NET Native, les règles d’analyse AM/PM ajustées sont activés par défaut.  
  
 Si la règle d’ajustement analyse n’est pas activée, le premier chiffre de la chaîne est interprété comme l’heure de l’horloge de 12 heures et le reste de la chaîne à l’exception de l’indicateur AM/PM est ignoré. La date et l’heure retournée par la méthode d’analyse se compose de la date et l’heure du jour extraite de la chaîne de date.  
  
 Si la règle d’ajustement analyse est activée, l’analyse de méthode interpréter le jour et le mois comme appartenant à l’année en cours et interpréter le temps que l’heure de l’horloge de 12 heures.  
  
 Le tableau suivant illustre la différence entre la <xref:System.DateTime> valeur lorsque le <xref:System.DateTime.Parse%28System.String%29?displayProperty=nameWithType> méthode est utilisée pour analyser la chaîne « « 6 4/10 AM » avec le `<EnableAmPmParseAdjustment>` l’élément `enabled` propriété la valeur « 0 » ou « 1 ». Il suppose que la date du jour est le 5 janvier 2017 et affiche la date comme si elle est mise en forme à l’aide de la chaîne de format « G » de la culture spécifiée.  
  
|Nom de culture|activé = « 0 »|activé = « 1 »|  
|------------------|------------------|------------------|  
|fr-FR|1/5/2017 4:00:00 AM|4/10/2017 6:00:00 AM|  
|en-GB|5/1/2017 6:00:00|10/4/2017 6:00:00|  
  
## <a name="see-also"></a>Voir aussi  
 [\<runtime > élément](../../../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md)  
 [\<configuration>, élément](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)
