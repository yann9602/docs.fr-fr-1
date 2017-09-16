---
title: "&lt;Type&gt;, élément (.NET Native)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1e88d368-a886-4f1e-8eb6-6127979a9fce
caps.latest.revision: 33
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 0f483fba5ade9d33588a946984ca914b95cd1f18
ms.contentlocale: fr-fr
ms.lasthandoff: 08/21/2017

---
# <a name="lttypegt-element-net-native"></a>&lt;Type&gt;, élément (.NET Native)
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
|`DataContractSerializer`|Sérialisation|Attribut facultatif. Contrôle la stratégie pour la sérialisation qui utilise la classe <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=fullName>.|  
|`DataContractJsonSerializer`|Sérialisation|Attribut facultatif. Contrôle la stratégie pour la sérialisation JSON qui utilise la classe <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=fullName>.|  
|`XmlSerializer`|Sérialisation|Attribut facultatif. Contrôle la stratégie pour la sérialisation XML qui utilise la classe <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName>.|  
|`MarshalObject`|Interop|Attribut facultatif. Contrôle la stratégie pour le marshaling des types de références vers Windows Runtime et COM.|  
|`MarshalDelegate`|Interop|Attribut facultatif. Contrôle la stratégie pour le marshaling des types de délégués comme pointeurs de fonction vers du code natif.|  
|`MarshalStructure`|Interop|Attribut facultatif. Contrôle la stratégie pour le marshaling des types de valeurs vers du code natif.|  
  
## <a name="name-attribute"></a>Name (attribut)  
  
|Valeur|Description|  
|-----------|-----------------|  
|*type_name*|Nom du type. Si cet élément `<Type>` est l’enfant d’un élément [\<Namespace>](../../../docs/framework/net-native/namespace-element-net-native.md) ou d’un autre élément `<Type>`, *type_name* peut inclure le nom du type sans son espace de noms. Dans le cas contraire, *type_name* doit inclure le nom de type complet.|  
  
## <a name="all-other-attributes"></a>Tous les autres attributs  
  
|Valeur|Description|  
|-----------|-----------------|  
|*policy_setting*|Paramètre à appliquer à ce type de stratégie. Les valeurs possibles sont `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal` et `Required All`. Pour plus d’informations, consultez [Paramètres de stratégie de directive runtime](../../../docs/framework/net-native/runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<AttributeImplies>](../../../docs/framework/net-native/attributeimplies-element-net-native.md)|Si le type conteneur est un attribut, définit la stratégie runtime pour les éléments de code auxquels l'attribut est appliqué.|  
|[\<Event>](../../../docs/framework/net-native/event-element-net-native.md)|Applique la stratégie de réflexion à un événement appartenant à ce type.|  
|[\<Field>](../../../docs/framework/net-native/field-element-net-native.md)|Applique la stratégie de réflexion à un champ appartenant à ce type.|  
|[\<GenericParameter>](../../../docs/framework/net-native/genericparameter-element-net-native.md)|Applique la stratégie au type de paramètre d'un type générique.|  
|[\<ImpliesType>](../../../docs/framework/net-native/impliestype-element-net-native.md)|Applique la stratégie à un type, si cette stratégie a été appliquée au type représenté par l'élément conteneur `<Type>`.|  
|[\<Method>](../../../docs/framework/net-native/method-element-net-native.md)|Applique la stratégie de réflexion à une méthode appartenant à ce type.|  
|[\<MethodInstantiation>](../../../docs/framework/net-native/methodinstantiation-element-net-native.md)|Applique la stratégie de réflexion à une méthode générique construite appartenant à ce type.|  
|[\<Property>](../../../docs/framework/net-native/property-element-net-native.md)|Applique la stratégie de réflexion à une propriété appartenant à ce type.|  
|[\<Subtypes>](../../../docs/framework/net-native/subtypes-element-net-native.md)|Applique la stratégie runtime à toutes les classes héritées du type conteneur.|  
|`<Type>`|Applique la stratégie de réflexion à un type imbriqué.|  
|[\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|Applique la stratégie de réflexion à un type générique construit.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<Application>](../../../docs/framework/net-native/application-element-net-native.md)|Sert de conteneur pour des types à l'échelle de l'application et pour des membres de types dont les métadonnées sont disponibles pour la réflexion au moment de l'exécution.|  
|[\<Assembly>](../../../docs/framework/net-native/assembly-element-net-native.md)|Applique la stratégie de réflexion à tous les types d'un assembly spécifié.|  
|[\<Library>](../../../docs/framework/net-native/library-element-net-native.md)|Définit l'assembly qui contient des types et des membres de types dont les métadonnées sont disponibles pour la réflexion au moment de l'exécution.|  
|[\<Namespace>](../../../docs/framework/net-native/namespace-element-net-native.md)|Applique la stratégie de réflexion à tous les types d'un espace de noms.|  
|`<Type>`|Applique la stratégie de réflexion à un type et à tous ses membres.|  
|[\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|Applique la stratégie de réflexion à un type générique construit et à tous ses membres.|  
  
## <a name="remarks"></a>Remarques  
 Les attributs de réflexion, de sérialisation et d'interopérabilité sont tous facultatifs. Si aucun n'est présent, l'élément `<Type>` sert de conteneur dont les types enfants définissent une stratégie pour des membres individuels.  
  
 Si un élément `<Type>` est l’enfant d’un élément [\<Assembly>](../../../docs/framework/net-native/assembly-element-net-native.md), [\<Namespace>](../../../docs/framework/net-native/namespace-element-net-native.md), `<Type>` ou [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md), il se substitue aux paramètres de stratégie définis par l’élément parent.  
  
 Un élément `<Type>` d'un type générique applique sa stratégie à toutes les instanciations qui n'ont pas leur propre stratégie. La stratégie des types génériques construits est définie par l’élément [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md).  
  
 Si le type est un type générique, son nom est décoré par un accent grave (\`) suivi de son nombre de paramètres génériques. Par exemple, l’attribut `Name` d’un élément `<Type>` pour la classe <xref:System.Collections.Generic.List%601?displayProperty=fullName> est `Name="System.Collections.Generic.List`1"`.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant utilise la réflexion pour afficher des informations sur les champs, les propriétés et les méthodes de la classe <xref:System.Collections.Generic.List%601?displayProperty=fullName>. La variable `b` utilisée dans l’exemple est un contrôle [TextBlock](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.textblock.aspx). Comme l'exemple récupère simplement les informations de type, la disponibilité des métadonnées est contrôlée par le paramètre de stratégie `Browse`.  
  
 [!code-csharp[ProjectN_Reflection#3](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/browsegenerictype1.cs#3)]  
  
 Comme les métadonnées de la classe <xref:System.Collections.Generic.List%601> ne sont pas automatiquement incluses par la chaîne d'outils [!INCLUDE[net_native](../../../includes/net-native-md.md)], l'exemple ne parvient pas à afficher les informations de membre requises au moment de l'exécution. Pour fournir les métadonnées nécessaires, ajoutez l'élément `<Type>` suivant au fichier de directives runtime. Comme nous avons déjà fourni un élément [<Namespace\>](../../../docs/framework/net-native/namespace-element-net-native.md) parent, nous n’avons pas à fournir un nom de type complet dans l’élément `<Type>`.  
  
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
 L'exemple suivant utilise la réflexion pour récupérer un objet <xref:System.Reflection.PropertyInfo> qui représente la propriété <xref:System.String.Chars%2A?displayProperty=fullName>. Il utilise ensuite la méthode <xref:System.Reflection.PropertyInfo.GetValue%28System.Object%2CSystem.Object%5B%5D%29?displayProperty=fullName> pour récupérer la valeur du septième caractère d'une chaîne et afficher tous les caractères de la chaîne. La variable `b` utilisée dans l’exemple est un contrôle [TextBlock](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.textblock.aspx).  
  
 [!code-csharp[ProjectN_Reflection#1](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/propertyinfo1.cs#1)]  
  
 Comme les métadonnées de l'objet <xref:System.String> ne sont pas disponibles, l'appel à la méthode <xref:System.Reflection.PropertyInfo.GetValue%28System.Object%2CSystem.Object%5B%5D%29?displayProperty=fullName> lève une exception <xref:System.NullReferenceException> au moment de l'exécution pendant la compilation avec la chaîne d'outils [!INCLUDE[net_native](../../../includes/net-native-md.md)]. Pour éliminer l'exception et fournir les métadonnées nécessaires, ajoutez l'élément `<Type>` suivant au fichier de directives runtime :  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
  <Application>  
    <Assembly Name="*Application*" Dynamic="Required All" />  
    <Type Name="System.String" Dynamic="Required Public"/> -->  
  </Application>  
</Directives>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence du fichier de configuration des directives runtime (rd.xml)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)   
 [Éléments de directive runtime](../../../docs/framework/net-native/runtime-directive-elements.md)   
 [Paramètres de stratégie de directive runtime](../../../docs/framework/net-native/runtime-directive-policy-settings.md)

