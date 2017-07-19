---
title: "&lt;Namespace&gt;, &#233;l&#233;ment (.NET Native) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 57c614e5-18a9-4e87-bfd5-d0fe3396a192
caps.latest.revision: 20
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 20
---
# &lt;Namespace&gt;, &#233;l&#233;ment (.NET Native)
Applique la stratégie de réflexion runtime à tous les types dans un espace de noms spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Namespace Name="namespace_name"   
           Activate="policy_type"   
           Browse="policy_type" />  
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
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Type d'attribut|Description|  
|---------------|--------------------|-----------------|  
|`Name`|Général|Attribut requis. Spécifie le nom de l'espace de noms.|  
|`Activate`|Réflexion|Attribut facultatif. Contrôle l'accès aux constructeurs pour permettre l'activation d'instances au moment de l'exécution.|  
|`Browse`|Réflexion|Attribut facultatif. Contrôle la demande d'informations sur les éléments de programme, mais ne permet pas l'accès au moment de l'exécution.|  
|`Dynamic`|Réflexion|Attribut facultatif. Contrôle l'accès à l'exécution à tous les membres de types, y compris les constructeurs, les méthodes, les champs, les propriétés et les événements, pour permettre la programmation dynamique.|  
|`Serialize`|Sérialisation|Attribut facultatif. Contrôle l'accès au moment de l'exécution aux constructeurs, champs et propriétés, pour permettre la sérialisation et la désérialisation des instances de types par des bibliothèques comme le sérialiseur JSON Newtonsoft.|  
|`DataContractSerializer`|Sérialisation|Attribut facultatif. Contrôle la stratégie de sérialisation qui utilise le <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=fullName> (classe).|  
|`DataContractJsonSerializer`|Sérialisation|Attribut facultatif. Contrôle la stratégie de sérialisation JSON qui utilise le <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=fullName> (classe).|  
|`XmlSerializer`|Sérialisation|Attribut facultatif. Contrôle la stratégie de sérialisation XML qui utilise le <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> classe.|  
|`MarshalObject`|Interop|Attribut facultatif. Contrôle la stratégie pour le marshaling des types de références vers Windows Runtime et COM.|  
|`MarshalDelegate`|Interop|Attribut facultatif. Contrôle la stratégie pour le marshaling des types de délégués comme pointeurs de fonction vers du code natif.|  
|`MarshalStructure`|Interop|Attribut facultatif. Stratégie de contrôles pour le marshaling de structures en code natif.|  
  
## <a name="name-attribute"></a>Name (attribut)  
  
|Valeur|Description|  
|-----------|-----------------|  
|*nom_espace_de_noms*|L'espace de noms. Si le <> \> élément est un enfant d’un [ <> \</> \> ](../../../docs/framework/net-native/application-element-net-native.md), [ <> \</> \> ](../../../docs/framework/net-native/library-element-net-native.md), ou [ <> \> ](../../../docs/framework/net-native/assembly-element-net-native.md) élément *nom_espace_de_noms* doit être un nom d’espace de noms qualifié complet. Si le <> \> élément est un enfant d’un autre <> \> élément *nom_espace_de_noms* doit être un nom d’espace de noms relatif.|  
  
## <a name="all-other-attributes"></a>Tous les autres attributs  
  
|Valeur|Description|  
|-----------|-----------------|  
|*policy_setting*|Le paramètre s'applique à ce type de stratégie pour tous les types dans l'espace de noms. Les valeurs possibles sont `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal` et `Required All`. Pour plus d’informations, consultez [paramètres de stratégie de Directive Runtime](../../../docs/framework/net-native/runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|`<Namespace>`|Applique la stratégie de réflexion runtime à tous les types dans un espace de noms parent.|  
|[<>\>](../../../docs/framework/net-native/type-element-net-native.md)|Applique la stratégie de réflexion à un type.|  
|[<>\>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|Applique la stratégie de réflexion à un type générique construit.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[<>\>](../../../docs/framework/net-native/application-element-net-native.md)|Sert de conteneur pour des types à l'échelle de l'application et pour des membres de types dont les métadonnées sont disponibles pour la réflexion au moment de l'exécution. Le [ <> \> ](../../../docs/framework/net-native/application-element-net-native.md) élément peut avoir zéro, un ou plusieurs [ <> \> ](../../../docs/framework/net-native/assembly-element-net-native.md) éléments.|  
|[<>\>](../../../docs/framework/net-native/assembly-element-net-native.md)|Applique la stratégie de réflexion runtime à tous les types dans un assembly spécifié.|  
|[<>\>](../../../docs/framework/net-native/library-element-net-native.md)|Définit l'assembly qui contient des types et des membres de types dont les métadonnées sont disponibles pour la réflexion au moment de l'exécution. Le [ <> \> ](../../../docs/framework/net-native/library-element-net-native.md) élément peut avoir zéro ou un [ <> \> ](../../../docs/framework/net-native/assembly-element-net-native.md) élément.|  
|`<Namespace>`|Applique la stratégie de réflexion à tous les types dans un espace de noms parent.|  
  
## <a name="remarks"></a>Notes  
 Les attributs `Activate`, `Browse`, `Dynamic` et `Serialize` sont tous facultatifs. Si aucun n'est présent, l'élément `<Namespace>` sert uniquement de conteneur pour les éléments enfants. S'ils sont présents, l'élément `<Namespace>` applique la stratégie de réflexion runtime à tous les types dans l'espace de noms spécifié.  
  
 Lorsqu’il est un enfant de la [ <> \> ](../../../docs/framework/net-native/assembly-element-net-native.md) élément, le `<Namespace>` élément remplace la stratégie de réflexion runtime définie par le [ <> \> ](../../../docs/framework/net-native/assembly-element-net-native.md) élément.  
  
## <a name="see-also"></a>Voir aussi  
 [Paramètres de stratégie de Directive Runtime](../../../docs/framework/net-native/runtime-directive-policy-settings.md)   
 [Référence du fichier de Configuration (rd.xml) de Directives Runtime](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)   
 [Éléments de Directive Runtime](../../../docs/framework/net-native/runtime-directive-elements.md)