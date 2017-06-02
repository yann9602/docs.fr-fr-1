---
title: "&lt;Application&gt;, &#233;l&#233;ment (.NET Native) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b4e9b37a-059b-4076-8f56-cb3f9cef0cd9
caps.latest.revision: 21
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 21
---
# &lt;Application&gt;, &#233;l&#233;ment (.NET Native)
Sert de conteneur pour les types à l'échelle de l'application et pour les membres de type dont les métadonnées sont disponibles pour la réflexion au moment de l'exécution, et applique la stratégie de réflexion runtime à tous les éléments de programme dans une application.  
  
 <>\>Élément  
<>\>Élément (rd.xml)  
  
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
|`DataContractSerializer`|Sérialisation|Attribut facultatif. Contrôle la stratégie de sérialisation qui utilise le <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=fullName> (classe).|  
|`DataContractJsonSerializer`|Sérialisation|Attribut facultatif. Contrôle la stratégie de sérialisation JSON qui utilise le <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=fullName> (classe).|  
|`XmlSerializer`|Sérialisation|Attribut facultatif. Contrôle la stratégie de sérialisation XML qui utilise le <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> classe.|  
|`MarshalObject`|Interop|Attribut facultatif. Contrôle la stratégie pour le marshaling des types de références vers Windows Runtime et COM.|  
|`MarshalDelegate`|Interop|Attribut facultatif. Contrôle la stratégie pour le marshaling des types de délégués comme pointeurs de fonction vers du code natif.|  
|`MarshalStructure`|Interop|Attribut facultatif. Stratégie de contrôles pour le marshaling de structures en code natif.|  
  
## <a name="all-attributes"></a>Tous les attributs  
  
|Valeur|Description|  
|-----------|-----------------|  
|*policy_setting*|Paramètre de cette stratégie à appliquer aux types dans l'application. Les valeurs possibles sont `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal` et `Required All`. Pour plus d’informations, consultez [paramètres de stratégie de Directive Runtime](../../../docs/framework/net-native/runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[<>\>](../../../docs/framework/net-native/assembly-element-net-native.md)|Applique la stratégie à tous les types d'un assembly particulier.|  
|[<>\>](../../../docs/framework/net-native/namespace-element-net-native.md)|Applique la stratégie à tous les types d'un espace de noms particulier.|  
|[<>\>](../../../docs/framework/net-native/type-element-net-native.md)|Applique la stratégie à un type particulier, tel qu'une classe ou une structure.|  
|[<>\>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|Applique la stratégie à un type générique construit. Par exemple, un [ <> \> ](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) élément peut être utilisé pour définir une stratégie pour un `List<String>` type.|  
|[<>\>](../../../docs/framework/net-native/method-element-net-native.md)|Applique la stratégie à une méthode sur un type particulier.|  
|[<>\>](../../../docs/framework/net-native/methodinstantiation-element-net-native.md)|Applique la stratégie à une méthode générique construite.|  
|[<>\>](../../../docs/framework/net-native/property-element-net-native.md)|Applique la stratégie à une propriété sur un type particulier.|  
|[<>\>](../../../docs/framework/net-native/field-element-net-native.md)|Applique la stratégie à un champ sur un type particulier.|  
|[<>\>](../../../docs/framework/net-native/event-element-net-native.md)|Applique la stratégie à un événement sur un type particulier.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[<>\>](../../../docs/framework/net-native/directives-element-net-native.md)|Élément racine d'un fichier de directives de runtime.|  
  
## <a name="remarks"></a>Notes  
 Le [ <> \> ](../../../docs/framework/net-native/directives-element-net-native.md) l’élément peut contenir zéro ou un `<Application>` élément. Un même fichier de directives de réflexion ne peut pas contenir plusieurs éléments `<Application>`.  
  
 Un élément `<Application>` peut être utilisé de deux manières différentes :  
  
-   En tant que conteneur pour définir des éléments de programme dont les métadonnées sont nécessaires au moment de l'exécution. Dans ce cas, l'élément `<Application>` n'a pas besoin d'attributs. Au moment de la compilation, les outils du compilateur recherchent dans toutes les bibliothèques, y compris les bibliothèques principales du .NET Framework, les éléments de programme identifiés par les éléments enfants de l'élément `<Application>`. En revanche, les outils du compilateur recherchent uniquement dans la bibliothèque désignée par le [ <> \> ](../../../docs/framework/net-native/library-element-net-native.md) élément pour les éléments de programme identifiés par les éléments enfants de [ <> \</> \> ](../../../docs/framework/net-native/library-element-net-native.md).  
  
-   En tant qu'élément qui définit la stratégie à l'échelle de l'application pour la réflexion, la sérialisation et l'interopérabilité. Les attributs de la `<Application>` élément définissent la stratégie de l’application, qui peut être substituée par les éléments enfants définis par le `<Application>` ou [ <> \> ](../../../docs/framework/net-native/library-element-net-native.md) élément.  
  
## <a name="see-also"></a>Voir aussi  
 [<>\>Élément](../../../docs/framework/net-native/library-element-net-native.md)   
 [<>\>Élément](../../../docs/framework/net-native/directives-element-net-native.md)   
 [Éléments de Directive Runtime](../../../docs/framework/net-native/runtime-directive-elements.md)   
 [Référence du fichier de Configuration (rd.xml) de Directives Runtime](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)