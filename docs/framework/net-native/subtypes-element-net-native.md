---
title: "&lt;Subtypes&gt;, &#233;l&#233;ment (.NET Native) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fb854070-248b-46cf-9dab-c322e2b4d624
caps.latest.revision: 11
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 11
---
# &lt;Subtypes&gt;, &#233;l&#233;ment (.NET Native)
Applique la stratégie runtime à toutes les classes héritées du type conteneur.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Subtypes Activate="policy_type"  
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
 L'élément `<Subtypes>` applique la stratégie à tous les sous-types de son type conteneur. Utilisez-le pour appliquer des stratégies distinctes aux types dérivés et à leurs classes de base.  
  
 Les attributs de réflexion, de sérialisation et d'interopérabilité sont tous facultatifs, même si un au moins doit être présent.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant définit une classe nommée `BaseClass` et une sous-classe nommée `Derived1`.  
  
 [!code-csharp[ProjectN_Reflection#4](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/subtypes.cs#4)]  
  
 Comme le montre le code suivant, le fichier de directives runtime définit explicitement les stratégies `Dynamic` et `Activate` pour `BaseClass` sur `Excluded`. Ainsi, les objets de type `BaseClass` ne peuvent pas être instanciés dynamiquement ou par des appels du constructeur de classe `BaseClass`. Toutefois, l'élément `<Subtypes>` permet aux classes dérivées de `BaseClass` d'être instanciées dynamiquement et via des appels de leurs constructeurs de classe.  
  
```xml  
  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
  <Application>  
   <Assembly Name="*Application*" Dynamic="Required All" />  
     <Type Name="Examples.Libraries.BaseClass" Activate ="Excluded" Dynamic="Excluded" >  
        <Subtypes Activate="Public" Dynamic ="Public"/>  
     </Type>  
  </Application>  
</Directives>  
  
```  
  
 Raison de la `<Subtypes>` directive, le code suivant instancie un `Derived1` instance dynamiquement en appelant le <xref:System.Activator.CreateInstance%28System.Type%29?displayProperty=fullName> méthode s’exécute correctement.  La variable de bloc est un <xref:System.Windows.Controls.TextBlock> objet dans une application Windows Store vide.  
  
 [!code-csharp[ProjectN_Reflection#5](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/subtypes.cs#5)]  
  
## <a name="see-also"></a>Voir aussi  
 [<>\>Élément](../../../docs/framework/net-native/type-element-net-native.md)   
 [Référence du fichier de Configuration (rd.xml) de Directives Runtime](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)   
 [Éléments de Directive Runtime](../../../docs/framework/net-native/runtime-directive-elements.md)   
 [Paramètres de stratégie de Directive Runtime](../../../docs/framework/net-native/runtime-directive-policy-settings.md)