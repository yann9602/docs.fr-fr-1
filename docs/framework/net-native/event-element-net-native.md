---
title: "&lt;Event&gt;, élément (.NET Native)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e53b029c-9d6d-4c0a-9cdc-5cfca8a5ca47
caps.latest.revision: 11
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 3ea3a4233ca0b01cd4b6ebd328387fea1dd189de
ms.contentlocale: fr-fr
ms.lasthandoff: 08/21/2017

---
# <a name="lteventgt-element-net-native"></a>&lt;Event&gt;, élément (.NET Native)
Applique la stratégie de réflexion runtime à un événement.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<Event Name="event_name"   
       Browse="policy_type"   
       Dynamic="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Type d'attribut|Description|  
|---------------|--------------------|-----------------|  
|`Name`|Général|Attribut requis. Spécifie le nom de l'événement.|  
|`Browse`|Réflexion|Attribut facultatif. Contrôle la demande d'informations sur l'événement ou l'énumération de celui-ci, mais ne permet pas d'effectuer un accès dynamique au moment de l'exécution.|  
|`Dynamic`|Réflexion|Attribut facultatif. Contrôle l'accès à l'événement au moment de l'exécution pour autoriser la programmation dynamique. Cette stratégie garantit qu'un événement peut être géré dynamiquement au moment de l'exécution.|  
  
## <a name="name-attribute"></a>Name (attribut)  
  
|Valeur|Description|  
|-----------|-----------------|  
|*nom_méthode*|Nom de l'événement. Le type de l’événement est défini par l’élément [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) ou [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) parent.|  
  
## <a name="all-other-attributes"></a>Tous les autres attributs  
  
|Valeur|Description|  
|-----------|-----------------|  
|*paramètre_stratégie*|Paramètre à appliquer à ce type de stratégie pour l'événement. Les valeurs possibles sont `Auto`, `Excluded`, `Included` et `Required`. Pour plus d’informations, consultez [Paramètres de stratégie de directive runtime](../../../docs/framework/net-native/runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<Type>](../../../docs/framework/net-native/type-element-net-native.md)|Applique la stratégie de réflexion à un type et à tous ses membres.|  
|[\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|Applique la stratégie de réflexion à un type générique construit et à tous ses membres.|  
  
## <a name="remarks"></a>Remarques  
 Si la stratégie d'un événement n'est pas définie explicitement, elle hérite la stratégie runtime de son élément parent.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence du fichier de configuration des directives runtime (rd.xml)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)   
 [Éléments de directive runtime](../../../docs/framework/net-native/runtime-directive-elements.md)   
 [Paramètres de stratégie de directive runtime](../../../docs/framework/net-native/runtime-directive-policy-settings.md)

