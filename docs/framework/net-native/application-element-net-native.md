---
title: "&lt;Application&gt;, élément (.NET Native)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b4e9b37a-059b-4076-8f56-cb3f9cef0cd9
caps.latest.revision: "21"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c486faf43a1109b0391f40072ab267b72e1d07d8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltapplicationgt-element-net-native"></a>&lt;Application&gt;, élément (.NET Native)
Sert de conteneur pour les types à l'échelle de l'application et pour les membres de type dont les métadonnées sont disponibles pour la réflexion au moment de l'exécution, et applique la stratégie de réflexion runtime à tous les éléments de programme dans une application.  
  
 \<Directives>, élément  
\<Application>, élément (rd.xml)  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<Application Activate="policy_setting"  
             Browse="policy_setting"  
             Dynamic="policy_setting"  
             Serialize="policy_setting"  
             DataContractSerializer="policy_setting"  
             DataContractJsonSerializer="policy_setting"  
             XmlSerializer="policy_setting"  
             MarshalObject="policy_setting"  
             MarshalDelegate="policy_setting"  
             MarshalStructure="policy_setting" />  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents. Dans le tableau Éléments enfants, la stratégie fait référence au type de métadonnées rendues disponibles pour des éléments de programme spécifiques au moment de l'exécution.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Type d'attribut|Description|  
|---------------|--------------------|-----------------|  
|`Activate`|Réflexion|Attribut facultatif. Contrôle l'accès aux constructeurs pour permettre l'activation d'instances au moment de l'exécution.|  
|`Browse`|Réflexion|Attribut facultatif. Contrôle la demande d'informations sur les types ou l'énumération de ceux-ci, mais ne permet pas d'effectuer un accès dynamique au moment de l'exécution.|  
|`Dynamic`|Réflexion|Attribut facultatif. Contrôle l'accès à l'exécution à tous les membres de types, y compris les constructeurs, les méthodes, les champs, les propriétés et les événements, pour permettre la programmation dynamique.|  
|`Serialize`|Sérialisation|Attribut facultatif. Contrôle l'accès au moment de l'exécution aux constructeurs, champs et propriétés, pour permettre la sérialisation et la désérialisation des instances de types par des bibliothèques comme le sérialiseur JSON Newtonsoft.|  
|`DataContractSerializer`|Sérialisation|Attribut facultatif. Contrôle la stratégie pour la sérialisation qui utilise la classe <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>.|  
|`DataContractJsonSerializer`|Sérialisation|Attribut facultatif. Contrôle la stratégie pour la sérialisation JSON qui utilise la classe <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType>.|  
|`XmlSerializer`|Sérialisation|Attribut facultatif. Contrôle la stratégie pour la sérialisation XML qui utilise la classe <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>.|  
|`MarshalObject`|Interop|Attribut facultatif. Contrôle la stratégie pour le marshaling des types de références vers Windows Runtime et COM.|  
|`MarshalDelegate`|Interop|Attribut facultatif. Contrôle la stratégie pour le marshaling des types de délégués comme pointeurs de fonction vers du code natif.|  
|`MarshalStructure`|Interop|Attribut facultatif. Stratégie de contrôles pour le marshaling de structures en code natif.|  
  
## <a name="all-attributes"></a>Tous les attributs  
  
|Valeur|Description|  
|-----------|-----------------|  
|*paramètre_stratégie*|Paramètre de cette stratégie à appliquer aux types dans l'application. Les valeurs possibles sont `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal` et `Required All`. Pour plus d’informations, consultez [Paramètres de stratégie de directive runtime](../../../docs/framework/net-native/runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<Assembly>](../../../docs/framework/net-native/assembly-element-net-native.md)|Applique la stratégie à tous les types d'un assembly particulier.|  
|[\<Namespace>](../../../docs/framework/net-native/namespace-element-net-native.md)|Applique la stratégie à tous les types d'un espace de noms particulier.|  
|[\<Type>](../../../docs/framework/net-native/type-element-net-native.md)|Applique la stratégie à un type particulier, tel qu'une classe ou une structure.|  
|[\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|Applique la stratégie à un type générique construit. Par exemple, vous pouvez utiliser un élément [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) afin de définir une stratégie pour un type `List<String>`.|  
|[\<Method>](../../../docs/framework/net-native/method-element-net-native.md)|Applique la stratégie à une méthode sur un type particulier.|  
|[\<MethodInstantiation>](../../../docs/framework/net-native/methodinstantiation-element-net-native.md)|Applique la stratégie à une méthode générique construite.|  
|[\<Property>](../../../docs/framework/net-native/property-element-net-native.md)|Applique la stratégie à une propriété sur un type particulier.|  
|[\<Field>](../../../docs/framework/net-native/field-element-net-native.md)|Applique la stratégie à un champ sur un type particulier.|  
|[\<Event>](../../../docs/framework/net-native/event-element-net-native.md)|Applique la stratégie à un événement sur un type particulier.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<Directives>](../../../docs/framework/net-native/directives-element-net-native.md)|Élément racine d'un fichier de directives de runtime.|  
  
## <a name="remarks"></a>Notes  
 L’élément [\<Directives>](../../../docs/framework/net-native/directives-element-net-native.md) peut contenir zéro ou un élément `<Application>`. Un même fichier de directives de réflexion ne peut pas contenir plusieurs éléments `<Application>`.  
  
 Un élément `<Application>` peut être utilisé de deux manières différentes :  
  
-   En tant que conteneur pour définir des éléments de programme dont les métadonnées sont nécessaires au moment de l'exécution. Dans ce cas, l'élément `<Application>` n'a pas besoin d'attributs. Au moment de la compilation, les outils du compilateur recherchent dans toutes les bibliothèques, y compris les bibliothèques principales du .NET Framework, les éléments de programme identifiés par les éléments enfants de l'élément `<Application>`. En revanche, les outils du compilateur ne recherchent les éléments de programme identifiés par les éléments enfants de [\<Library>](../../../docs/framework/net-native/library-element-net-native.md) que dans la bibliothèque désignée par l’élément [\<Library>](../../../docs/framework/net-native/library-element-net-native.md).  
  
-   En tant qu'élément qui définit la stratégie à l'échelle de l'application pour la réflexion, la sérialisation et l'interopérabilité. Les attributs de l’élément `<Application>` définissent la stratégie à l’échelle de l’application, qui peut être substituée par les éléments enfants définis par l’élément `<Application>` ou [\<Library>](../../../docs/framework/net-native/library-element-net-native.md).  
  
## <a name="see-also"></a>Voir aussi  
 [\<Bibliothèque > élément](../../../docs/framework/net-native/library-element-net-native.md)  
 [\<Directives > élément](../../../docs/framework/net-native/directives-element-net-native.md)  
 [Éléments de directive runtime](../../../docs/framework/net-native/runtime-directive-elements.md)  
 [Guide de référence du fichier de configuration des directives runtime (rd.xml)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
