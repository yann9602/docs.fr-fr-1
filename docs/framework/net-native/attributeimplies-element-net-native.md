---
title: "&lt;AttributeImplies&gt;, &#233;l&#233;ment (.NET Native) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 82db7193-a860-418b-84fc-fff2fdf2e025
caps.latest.revision: 7
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 7
---
# &lt;AttributeImplies&gt;, &#233;l&#233;ment (.NET Native)
Définit la stratégie pour les éléments de code auxquels l'attribut conteneur est appliqué.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<AttributeImplies Activate="policy_type"  
                  Browse="policy_type"  
                  Dynamic="policy_type"  
                  Serialize="policy_type"   
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
|`Activate`|Réflexion|Attribut facultatif. Contrôle l'accès aux constructeurs pour permettre l'activation d'instances au moment de l'exécution.|  
|`Browse`|Réflexion|Attribut facultatif. Contrôle la demande d'informations sur les éléments de programme, mais ne permet pas l'accès au moment de l'exécution.|  
|`Dynamic`|Réflexion|Attribut facultatif. Contrôle l'accès à l'exécution à tous les membres de types, y compris les constructeurs, les méthodes, les champs, les propriétés et les événements, pour permettre la programmation dynamique.|  
|`Serialize`|Sérialisation|Attribut facultatif. Contrôle l'accès au moment de l'exécution aux constructeurs, champs et propriétés, pour permettre la sérialisation et la désérialisation des instances de types par des bibliothèques comme le sérialiseur JSON Newtonsoft.|  
|`DataContractSerializer`|Sérialisation|Attribut facultatif. Contrôle la stratégie de sérialisation qui utilise le <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=fullName> (classe).|  
|`DataContractJsonSerializer`|Sérialisation|Attribut facultatif. Contrôle la stratégie de sérialisation JSON qui utilise le <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=fullName> (classe).|  
|`XmlSerializer`|Sérialisation|Attribut facultatif. Contrôle la stratégie de sérialisation XML qui utilise le <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> classe.|  
|`MarshalObject`|Interop|Attribut facultatif. Contrôle la stratégie pour le marshaling des types de références vers Windows Runtime et COM.|  
|`MarshalDelegate`|Interop|Attribut facultatif. Contrôle la stratégie pour le marshaling des types de délégués comme pointeurs de fonction vers du code natif.|  
|`MarshalStructure`|Interop|Attribut facultatif. Contrôle la stratégie pour le marshaling des types de valeurs vers du code natif.|  
  
## <a name="all-attributes"></a>Tous les attributs  
  
|Valeur|Description|  
|-----------|-----------------|  
|*policy_setting*|Paramètre à appliquer à ce type de stratégie. Les valeurs possibles sont `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal` et `Required All`. Pour plus d’informations, consultez [paramètres de stratégie de Directive Runtime](../../../docs/framework/net-native/runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[<>\>](../../../docs/framework/net-native/type-element-net-native.md)|Applique la stratégie de réflexion à un type et à tous ses membres.|  
  
## <a name="remarks"></a>Notes  
 Le `<AttributeImplies>` élément est utilisé si son type conteneur est un attribut (autrement dit, une classe dérivée de <xref:System.Attribute?displayProperty=fullName>). Si l'attribut est appliqué à un élément de programme particulier, la stratégie définie par l'élément `<AttributeImplies>` s'applique à cet élément de programme.  
  
 Les attributs de réflexion, de sérialisation et d'interopérabilité sont tous facultatifs, même si un au moins doit être présent.  
  
## <a name="see-also"></a>Voir aussi  
 [<>\>Élément](../../../docs/framework/net-native/type-element-net-native.md)   
 [Référence du fichier de Configuration (rd.xml) de Directives Runtime](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)   
 [Éléments de Directive Runtime](../../../docs/framework/net-native/runtime-directive-elements.md)   
 [Paramètres de stratégie de Directive Runtime](../../../docs/framework/net-native/runtime-directive-policy-settings.md)