---
title: "&lt;TypeParameter&gt;, &#233;l&#233;ment (.NET Native) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d37bb1b7-1ddc-4c6d-8ecf-583f804a2479
caps.latest.revision: 11
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 11
---
# &lt;TypeParameter&gt;, &#233;l&#233;ment (.NET Native)
Applique la stratégie au type représenté par un argument Type passé à une méthode.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Parameter Name="parameter_name"  
           Activate="policy_type"  
           Browse="policy_type"  
           Dynamic="policy_type"  
           Serialize="policy_type"  
           DataContractSerializer="policy_type"  
           DataContractJsonSerializer="policy_type"  
           XmlSerializer="policy_type"  
           MarshalObject="policy_type"  
           MarshalDelegate="policy_type"  
           MarshalStructure="policy_type" />  
  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Type d'attribut|Description|  
|---------------|--------------------|-----------------|  
|`Name`|Général|Attribut requis. Le nom du paramètre de type <xref:System.Type>. Par exemple, pour la signature de méthode `Type.GetInterfaceMap(Type interfaceType)`, la valeur de l'attribut `Name` est « interfaceType ».|  
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
  
## <a name="name-attribute"></a>Name (attribut)  
  
|Valeur|Description|  
|-----------|-----------------|  
|*parameter_name*|Le nom du paramètre de type <xref:System.Type>. Par exemple, pour la signature de méthode `Type.GetInterfaceMap(Type interfaceType)`, la valeur de l'attribut `Name` est « interfaceType ».|  
  
## <a name="all-other-attributes"></a>Tous les autres attributs  
  
|Valeur|Description|  
|-----------|-----------------|  
|*policy_setting*|Paramètre à appliquer à ce type de stratégie. Les valeurs possibles sont `All`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal` et `Required All`. Pour plus d’informations, consultez [paramètres de stratégie de Directive Runtime](../../../docs/framework/net-native/runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[<>\>](../../../docs/framework/net-native/method-element-net-native.md)|Applique une stratégie de réflexion runtime à un constructeur ou à une méthode.|  
  
## <a name="remarks"></a>Notes  
 Le `<TypeParameter>` élément est similaire à la [ <> \> ](../../../docs/framework/net-native/parameter-element-net-native.md) élément, à ceci près qu’il ne peut être appliqué uniquement aux paramètres de type <xref:System.Type>. Il applique la stratégie à tout type représenté au moment de l'exécution par l'argument de type spécifié par l'attribut `Name`.  
  
 Par exemple, le sérialiseur JSON NewtonSoft inclut une méthode `JsonConvert.DeserializeObject(String value, Type type)` statique. Les directives de réflexion suivantes :  
  
```xml  
  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Type Name="Newtonsoft.Json.JsonConvert" >  
      <Method Name="DeserializeObject">  
         <GenericParameter Name="type" Serialize="Required All" />  
      </Method>  
   </Type>  
</Directives>  
  
```  
  
 Spécifiez que les métadonnées pour le type de runtime représenté par le `type` argument doit être mis à disposition pour la sérialisation. Si ces directives runtime s'appliquent à un projet qui inclut le code source suivant :  
  
```csharp  
  
Type t = typeof(StockQuote);  
Object obj = JsonConvert.DeserializeObject(data, t);  
  
```  
  
 les directives de réflexion rendent les métadonnées pour le type `StockQuote` disponibles pour le sérialiseur JSON NewtonSoft au moment de l'exécution.  
  
## <a name="see-also"></a>Voir aussi  
 [<>\>Élément](../../../docs/framework/net-native/method-element-net-native.md)   
 [Référence du fichier de Configuration (rd.xml) de Directives Runtime](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)   
 [Paramètres de stratégie de Directive Runtime](../../../docs/framework/net-native/runtime-directive-policy-settings.md)   
 [Éléments de Directive Runtime](../../../docs/framework/net-native/runtime-directive-elements.md)