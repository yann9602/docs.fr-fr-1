---
title: "&lt;Type&gt;, &#233;l&#233;ment (.NET Native) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1e88d368-a886-4f1e-8eb6-6127979a9fce
caps.latest.revision: 33
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 33
---
# &lt;Type&gt;, &#233;l&#233;ment (.NET Native)
Applique la stratégie runtime à un type particulier, tel qu'une classe ou une structure.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Type Name="type_name"  
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
|*nom_type*|Nom du type. Si cette `<Type>` élément est l’enfant d’un [ <> \> ](../../../docs/framework/net-native/namespace-element-net-native.md) ou un autre `<Type>` élément *type_name* peut inclure le nom du type sans son espace de noms. Dans le cas contraire, *type_name* doit inclure le nom de type qualifié complet.|  
  
## <a name="all-other-attributes"></a>Tous les autres attributs  
  
|Valeur|Description|  
|-----------|-----------------|  
|*policy_setting*|Paramètre à appliquer à ce type de stratégie. Les valeurs possibles sont `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal` et `Required All`. Pour plus d’informations, consultez [paramètres de stratégie de Directive Runtime](../../../docs/framework/net-native/runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[<>\>](../../../docs/framework/net-native/attributeimplies-element-net-native.md)|Si le type conteneur est un attribut, définit la stratégie runtime pour les éléments de code auxquels l'attribut est appliqué.|  
|[<>\>](../../../docs/framework/net-native/event-element-net-native.md)|Applique la stratégie de réflexion à un événement appartenant à ce type.|  
|[<>\>](../../../docs/framework/net-native/field-element-net-native.md)|Applique la stratégie de réflexion à un champ appartenant à ce type.|  
|[<>\>](../../../docs/framework/net-native/genericparameter-element-net-native.md)|Applique la stratégie au type de paramètre d'un type générique.|  
|[<>\>](../../../docs/framework/net-native/impliestype-element-net-native.md)|Applique la stratégie à un type, si cette stratégie a été appliquée au type représenté par l'élément conteneur `<Type>`.|  
|[<>\>](../../../docs/framework/net-native/method-element-net-native.md)|Applique la stratégie de réflexion à une méthode appartenant à ce type.|  
|[<>\>](../../../docs/framework/net-native/methodinstantiation-element-net-native.md)|Applique la stratégie de réflexion à une méthode générique construite appartenant à ce type.|  
|[<>\>](../../../docs/framework/net-native/property-element-net-native.md)|Applique la stratégie de réflexion à une propriété appartenant à ce type.|  
|[<>\>](../../../docs/framework/net-native/subtypes-element-net-native.md)|Applique la stratégie runtime à toutes les classes héritées du type conteneur.|  
|`<Type>`|Applique la stratégie de réflexion à un type imbriqué.|  
|[<>\>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|Applique la stratégie de réflexion à un type générique construit.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[<>\>](../../../docs/framework/net-native/application-element-net-native.md)|Sert de conteneur pour des types à l'échelle de l'application et pour des membres de types dont les métadonnées sont disponibles pour la réflexion au moment de l'exécution.|  
|[<>\>](../../../docs/framework/net-native/assembly-element-net-native.md)|Applique la stratégie de réflexion à tous les types d'un assembly spécifié.|  
|[<>\>](../../../docs/framework/net-native/library-element-net-native.md)|Définit l'assembly qui contient des types et des membres de types dont les métadonnées sont disponibles pour la réflexion au moment de l'exécution.|  
|[<>\>](../../../docs/framework/net-native/namespace-element-net-native.md)|Applique la stratégie de réflexion à tous les types d'un espace de noms.|  
|`<Type>`|Applique la stratégie de réflexion à un type et à tous ses membres.|  
|[<>\>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|Applique la stratégie de réflexion à un type générique construit et à tous ses membres.|  
  
## <a name="remarks"></a>Notes  
 Les attributs de réflexion, de sérialisation et d'interopérabilité sont tous facultatifs. Si aucun n'est présent, l'élément `<Type>` sert de conteneur dont les types enfants définissent une stratégie pour des membres individuels.  
  
 Si un `<Type>` élément est l’enfant d’un [ <> \</> \> ](../../../docs/framework/net-native/assembly-element-net-native.md), [ <> \</> \> ](../../../docs/framework/net-native/namespace-element-net-native.md), `<Type>`, ou [ <> \> ](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) élément, il substitue aux paramètres de stratégie définis par l’élément parent.  
  
 Un élément `<Type>` d'un type générique applique sa stratégie à toutes les instanciations qui n'ont pas leur propre stratégie. La stratégie des types génériques construits est définie par le [ <> \> ](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) élément.  
  
 Si le type est un type générique, son nom est décoré par un accent grave ('' ') suivi de son nombre de paramètres génériques. Par exemple, le `Name` attribut d’un `<Type>` élément pour le <xref:System.Collections.Generic.List%601?displayProperty=fullName> classe apparaît comme `Name="System.Collections.Generic.List`1 » ».  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise la réflexion pour afficher des informations sur les champs, propriétés et méthodes de la <xref:System.Collections.Generic.List%601?displayProperty=fullName> (classe). La variable `b` dans l’exemple est un [TextBlock](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.textblock.aspx) contrôle. Comme l'exemple récupère simplement les informations de type, la disponibilité des métadonnées est contrôlée par le paramètre de stratégie `Browse`.  
  
 [!code-csharp[ProjectN_Reflection#3](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/browsegenerictype1.cs#3)]  
  
 Étant donné que les métadonnées pour le <xref:System.Collections.Generic.List%601> classe n’est pas incluse automatiquement par le [!INCLUDE[net_native](../../../includes/net-native-md.md)] chaîne d’outils, l’exemple ne parvient pas à afficher les informations de membre requises au moment de l’exécution. Pour fournir les métadonnées nécessaires, ajoutez l'élément `<Type>` suivant au fichier de directives runtime. Notez que, étant donné que nous vous avons fourni un parent [ <> \> ](../../../docs/framework/net-native/namespace-element-net-native.md) élément, nous n’avons pas à fournir un nom de type qualifié complet dans le `<Type>` élément.  
  
```xml  
  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Application>  
      <Assembly Name="*Application*" Dynamic="Required All" />  
      <Namespace Name ="System.Collections.Generic" >  
        <Type Name="List`1" Browse="Required All" />   
     </Namespace>  
   </Application>  
</Directives>  
  
```  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise la réflexion pour récupérer un <xref:System.Reflection.PropertyInfo> objet qui représente le <xref:System.String.Chars%2A?displayProperty=fullName> propriété. Il utilise ensuite la [PropertyInfo.GetValue (Object, Object\<xref:System.Reflection.PropertyInfo.GetValue%28System.Object%2CSystem.Object%5B%5D%29?displayProperty=fullName> méthode pour récupérer la valeur du septième caractère dans une chaîne et pour afficher tous les caractères de la chaîne. La variable `b` dans l’exemple est un [TextBlock](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.textblock.aspx) contrôle.  
  
 [!code-csharp[ProjectN_Reflection#1](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/propertyinfo1.cs#1)]  
  
 Car les métadonnées pour le <xref:System.String> objet n’est pas disponible, l’appel à la [PropertyInfo.GetValue (Object, Object\<xref:System.Reflection.PropertyInfo.GetValue%28System.Object%2CSystem.Object%5B%5D%29?displayProperty=fullName> méthode lève une exception un <xref:System.NullReferenceException> exception pendant l’exécution temps lors de la compilation avec le [!INCLUDE[net_native](../../../includes/net-native-md.md)] chaîne d’outils. Pour éliminer l'exception et fournir les métadonnées nécessaires, ajoutez l'élément `<Type>` suivant au fichier de directives runtime :  
  
```xml  
  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
  <Application>  
    <Assembly Name="*Application*" Dynamic="Required All" />  
    <Type Name="System.String" Dynamic="Required Public"/> -->  
  </Application>  
</Directives>  
  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Référence du fichier de Configuration (rd.xml) de Directives Runtime](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)   
 [Éléments de Directive Runtime](../../../docs/framework/net-native/runtime-directive-elements.md)   
 [Paramètres de stratégie de Directive Runtime](../../../docs/framework/net-native/runtime-directive-policy-settings.md)