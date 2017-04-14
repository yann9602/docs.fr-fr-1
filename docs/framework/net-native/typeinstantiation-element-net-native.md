---
title: "&lt;TypeInstantiation&gt;, &#233;l&#233;ment (.NET Native) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a5eada64-075b-4162-9655-ded84e4681f2
caps.latest.revision: 21
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 21
---
# &lt;TypeInstantiation&gt;, &#233;l&#233;ment (.NET Native)
Applique la stratégie de réflexion runtime à un type générique construit.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<TypeInstantiation Name="type_name"  
                   Arguments="type_arguments"  
                   Activate="policy_type"  
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
|`Name`|Général|Attribut requis. Spécifie le nom du type.|  
|`Arguments`|Général|Attribut requis. Spécifie les arguments de type générique. Si plusieurs arguments sont présents, ils sont séparés par des virgules.|  
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
|*nom_type*|Nom du type. Si cette `<TypeInstantiation>` élément est l’enfant d’un [ <> \> ](../../../docs/framework/net-native/namespace-element-net-native.md) élément, un [ <> \> ](../../../docs/framework/net-native/type-element-net-native.md) élément ou un autre `<TypeInstantiation>` élément *type_name* pouvez spécifier le nom du type sans son espace de noms. Dans le cas contraire, *type_name* doit inclure le nom de type qualifié complet. Le nom du type n'est pas décoré. Par exemple, pour un <xref:System.Collections.Generic.List%601?displayProperty=fullName> objet, le `<TypeInstantiation>` élément peut apparaître comme suit :<br /><br /> `\<TypeInstantiation Name=System.Collections.Generic.List Dynamic="Required Public" />`|  
  
## <a name="arguments-attribute"></a>Attribut Arguments  
  
|Valeur|Description|  
|-----------|-----------------|  
|*type_argument*|Spécifie les arguments de type générique. Si plusieurs arguments sont présents, ils sont séparés par des virgules. Chaque argument doit être composé du nom de type qualifié complet.|  
  
## <a name="all-other-attributes"></a>Tous les autres attributs  
  
|Valeur|Description|  
|-----------|-----------------|  
|*policy_setting*|Paramètre à appliquer à ce type de stratégie pour le type générique construit. Les valeurs possibles sont `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal` et `Required All`. Pour plus d’informations, consultez [paramètres de stratégie de Directive Runtime](../../../docs/framework/net-native/runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[<>\>](../../../docs/framework/net-native/event-element-net-native.md)|Applique la stratégie de réflexion à un événement appartenant à ce type.|  
|[<>\>](../../../docs/framework/net-native/field-element-net-native.md)|Applique la stratégie de réflexion à un champ appartenant à ce type.|  
|[<>\>](../../../docs/framework/net-native/impliestype-element-net-native.md)|Applique la stratégie à un type, si cette stratégie a été appliquée au type représenté par l'élément conteneur `<TypeInstantiation>`.|  
|[<>\>](../../../docs/framework/net-native/method-element-net-native.md)|Applique la stratégie de réflexion à une méthode appartenant à ce type.|  
|[<>\>](../../../docs/framework/net-native/methodinstantiation-element-net-native.md)|Applique la stratégie de réflexion à une méthode générique construite appartenant à ce type.|  
|[<>\>](../../../docs/framework/net-native/property-element-net-native.md)|Applique la stratégie de réflexion à une propriété appartenant à ce type.|  
|[<>\>](../../../docs/framework/net-native/type-element-net-native.md)|Applique la stratégie de réflexion à un type imbriqué.|  
|`<TypeInstantiation>`|Applique la stratégie de réflexion à un type générique construit imbriqué.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[<>\>](../../../docs/framework/net-native/application-element-net-native.md)|Sert de conteneur pour des types à l'échelle de l'application et pour des membres de types dont les métadonnées sont disponibles pour la réflexion au moment de l'exécution.|  
|[<>\>](../../../docs/framework/net-native/assembly-element-net-native.md)|Applique la stratégie de réflexion à tous les types d'un assembly spécifié.|  
|[<>\>](../../../docs/framework/net-native/library-element-net-native.md)|Définit l'assembly qui contient des types et des membres de types dont les métadonnées sont disponibles pour la réflexion au moment de l'exécution.|  
|[<>\>](../../../docs/framework/net-native/namespace-element-net-native.md)|Applique la stratégie de réflexion à tous les types d'un espace de noms.|  
|[<>\>](../../../docs/framework/net-native/type-element-net-native.md)|Applique la stratégie de réflexion à un type et à tous ses membres.|  
|`<TypeInstantiation>`|Applique la stratégie de réflexion à un type générique construit et à tous ses membres.|  
  
## <a name="remarks"></a>Notes  
 Les attributs de réflexion, de sérialisation et d'interopérabilité sont tous facultatifs. Toutefois, au moins un doit être présent.  
  
 Si un `<TypeInstantiation>` élément est l’enfant d’un [ <> \</> \> ](../../../docs/framework/net-native/assembly-element-net-native.md), [ <> \</> \> ](../../../docs/framework/net-native/namespace-element-net-native.md), ou [ <> \</> \> ](../../../docs/framework/net-native/type-element-net-native.md), élément, il substitue aux paramètres de stratégie définis par l’élément parent. Si un [ <> \> ](../../../docs/framework/net-native/type-element-net-native.md) élément spécifie une définition de type générique correspondante, le `<TypeInstantiation>` élément remplace la stratégie de réflexion runtime que pour les instanciations du type générique construit spécifié.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise la réflexion pour récupérer la définition de type générique construit d’un <xref:System.Collections.Generic.Dictionary%602> objet.</TKey, TValue> Il utilise également la réflexion pour afficher des informations sur les <xref:System.Type> objets qui représentent des types génériques construits et définitions de type générique. La variable `b` dans l’exemple est un [TextBlock](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.textblock.aspx) contrôle.  
  
 [!code-csharp[ProjectN_Reflection#2](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/makegenerictype1.cs#2)]  
  
 Après la compilation avec les [!INCLUDE[net_native](../../../includes/net-native-md.md)] chaîne d’outils, l’exemple lève un [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) exception sur la ligne qui appelle la <xref:System.Type.GetGenericTypeDefinition%2A?displayProperty=fullName> (méthode). Vous pouvez éliminer l'exception et fournir les métadonnées nécessaires en ajoutant l'élément `<TypeInstantiation>` suivant au fichier de directives runtime :  
  
```xml  
  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
  <Application>  
    <Assembly Name="*Application*" Dynamic="Required All" />  
     <TypeInstantiation Name="System.Collections.Generic.Dictionary"  
                        Arguments="System.String,GenericType.Example"  
                        Dynamic="Required Public" />  
  </Application>  
</Directives>  
  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Référence du fichier de Configuration (rd.xml) de Directives Runtime](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)   
 [Éléments de Directive Runtime](../../../docs/framework/net-native/runtime-directive-elements.md)   
 [Paramètres de stratégie de Directive Runtime](../../../docs/framework/net-native/runtime-directive-policy-settings.md)