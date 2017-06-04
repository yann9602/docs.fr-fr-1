---
title: "&#201;criture des attributs personnalis&#233;s | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "AllowMultiple (propriété)"
  - "classes d'attributs, déclarer"
  - "attributs (.NET Framework), personnalisé"
  - "AttributeTargets (énumération)"
  - "AttributeUsageAttribute (classe), attributs personnalisés"
  - "attributs personnalisés"
  - "Inherited (propriété)"
  - "instances multiples d'un attribut"
ms.assetid: 97216f69-bde8-49fd-ac40-f18c500ef5dc
caps.latest.revision: 14
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 14
---
# &#201;criture des attributs personnalis&#233;s
Pour concevoir vos propres attributs personnalisés, vous n’avez pas besoin de maîtriser les nombreux nouveaux concepts. Si vous êtes familiarisé avec la programmation orientée objet et savez concevoir des classes, vous possédez déjà la plupart des connaissances nécessaires. Les attributs personnalisés sont essentiellement des classes traditionnelles qui dérivent directement ou indirectement de <xref:System.Attribute?displayProperty=fullName>. Tout comme les classes traditionnelles, les attributs personnalisés contiennent des méthodes qui stockent et récupèrent les données.  
  
 Les principales étapes permettant de concevoir correctement des classes d’attributs personnalisés sont les suivantes :  
  
-   [Application d’AttributeUsageAttribute](#cpconapplyingattributeusageattribute)  
  
-   [Déclaration de la classe d’attributs](#cpcondeclaringattributeclass)  
  
-   [Déclaration des constructeurs](#cpcondeclaringconstructors)  
  
-   [Déclaration des propriétés](#cpcondeclaringproperties)  
  
 Cette section décrit chacune de ces étapes et se termine par un [exemple d’attribut personnalisé](#cpconcustomattributeexample).  
  
<a name="cpconapplyingattributeusageattribute"></a>   
## Application d’AttributeUsageAttribute  
 Une déclaration d’attribut personnalisé commence par **AttributeUsageAttribute**, qui définit certaines caractéristiques clés de votre classe d’attributs. Par exemple, vous pouvez spécifier si votre attribut peut être hérité par d’autres classes ou spécifier les éléments auxquels l’attribut peut être appliqué. Le fragment de code suivant montre comment utiliser **AttributeUsageAttribute**.  
  
 [!code-cpp[Conceptual.Attributes.Usage#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#5)]
 [!code-csharp[Conceptual.Attributes.Usage#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#5)]
 [!code-vb[Conceptual.Attributes.Usage#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#5)]  
  
 <xref:System.AttributeUsageAttribute?displayProperty=fullName> possède trois membres importants pour la création d’attributs personnalisés : [AttributeTargets](#cpconwritingcustomattributesanchor1), [Inherited](#cpconwritingcustomattributesanchor2) et [AllowMultiple](#cpconwritingcustomattributesanchor3).  
  
<a name="cpconwritingcustomattributesanchor1"></a>   
### Membre AttributeTargets  
 Dans l’exemple précédent, **AttributeTargets.All** est spécifié, ce qui indique que cet attribut peut être appliqué à tous les éléments de programme. Vous pouvez également spécifier **AttributeTargets.Class**, qui indique que votre attribut peut être appliqué uniquement à une classe, ou **AttributeTargets.Method**, qui indique que votre attribut peut être appliqué uniquement à une méthode. Tous les éléments de programme peuvent être marqués pour description par un attribut personnalisé de cette manière.  
  
 Vous pouvez également transmettre plusieurs instances de <xref:System.AttributeTargets>. Le fragment de code suivant spécifie qu’un attribut personnalisé peut être appliqué à n’importe quelle classe ou méthode.  
  
 [!code-cpp[Conceptual.Attributes.Usage#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#6)]
 [!code-csharp[Conceptual.Attributes.Usage#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#6)]
 [!code-vb[Conceptual.Attributes.Usage#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#6)]  
  
<a name="cpconwritingcustomattributesanchor2"></a>   
### Propriété Inherited  
 La propriété <xref:System.AttributeUsageAttribute.Inherited%2A?displayProperty=fullName> indique si votre attribut peut être hérité par les classes qui sont dérivées des classes auxquelles votre attribut est appliqué. Cette propriété reçoit un indicateur **true** \(par défaut\) ou **false**. Dans l’exemple suivant, la valeur <xref:System.AttributeUsageAttribute.Inherited%2A> par défaut de `MyAttribute` est **true**, tandis que la valeur <xref:System.AttributeUsageAttribute.Inherited%2A> de `YourAttribute` est **false**.  
  
 [!code-cpp[Conceptual.Attributes.Usage#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#7)]
 [!code-csharp[Conceptual.Attributes.Usage#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#7)]
 [!code-vb[Conceptual.Attributes.Usage#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#7)]  
  
 Les deux attributs sont ensuite appliqués à une méthode dans la classe de base `MyClass`.  
  
 [!code-cpp[Conceptual.Attributes.Usage#9](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#9)]
 [!code-csharp[Conceptual.Attributes.Usage#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#9)]
 [!code-vb[Conceptual.Attributes.Usage#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#9)]  
  
 Enfin, la classe `YourClass` est héritée de la classe de base `MyClass`. La méthode `MyMethod` affiche `MyAttribute`, mais pas `YourAttribute`.  
  
 [!code-cpp[Conceptual.Attributes.Usage#10](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#10)]
 [!code-csharp[Conceptual.Attributes.Usage#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#10)]
 [!code-vb[Conceptual.Attributes.Usage#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#10)]  
  
<a name="cpconwritingcustomattributesanchor3"></a>   
### Propriété AllowMultiple  
 La propriété <xref:System.AttributeUsageAttribute.AllowMultiple%2A?displayProperty=fullName> indique si plusieurs instances de votre attribut peuvent exister sur un élément. Si la valeur est **true**, plusieurs instances sont autorisées, si la valeur est **false** \(par défaut\), une seule instance est autorisée.  
  
 Dans l’exemple suivant, la valeur <xref:System.AttributeUsageAttribute.AllowMultiple%2A> par défaut de `MyAttribute` est **true**, tandis que la valeur de `YourAttribute` est **false**.  
  
 [!code-cpp[Conceptual.Attributes.Usage#11](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#11)]
 [!code-csharp[Conceptual.Attributes.Usage#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#11)]
 [!code-vb[Conceptual.Attributes.Usage#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#11)]  
  
 Quand plusieurs instances de ces attributs sont appliquées, `MyAttribute` génère une erreur du compilateur. L’exemple de code suivant illustre l’utilisation valide de `YourAttribute` et l’utilisation non valide de `MyAttribute`.  
  
 [!code-cpp[Conceptual.Attributes.Usage#13](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#13)]
 [!code-csharp[Conceptual.Attributes.Usage#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#13)]
 [!code-vb[Conceptual.Attributes.Usage#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#13)]  
  
 Si la propriété <xref:System.AttributeUsageAttribute.AllowMultiple%2A> et la propriété <xref:System.AttributeUsageAttribute.Inherited%2A> ont la valeur **true**, une classe héritée d’une autre classe peut hériter d’un attribut et avoir une autre instance du même attribut appliquée dans la même classe enfant. Si <xref:System.AttributeUsageAttribute.AllowMultiple%2A> a la valeur **false**, les valeurs des attributs de la classe parente sont remplacées par les nouvelles instances du même attribut dans la classe enfant.  
  
<a name="cpcondeclaringattributeclass"></a>   
## Déclaration de la classe d’attributs  
 Une fois que vous avez appliqué <xref:System.AttributeUsageAttribute>, vous pouvez commencer à définir les particularités de votre attribut. La déclaration d’une classe d’attributs ressemble à la déclaration d’une classe traditionnelle, comme illustré dans le code suivant.  
  
 [!code-cpp[Conceptual.Attributes.Usage#14](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#14)]
 [!code-csharp[Conceptual.Attributes.Usage#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#14)]
 [!code-vb[Conceptual.Attributes.Usage#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#14)]  
  
 Cette définition de l’attribut illustre les points suivants :  
  
-   Les classes d’attributs doivent être déclarées comme des classes publiques.  
  
-   Par convention, le nom de la classe d’attributs se termine par le mot **Attribute**. Même si elle n’est pas obligatoire, cette convention est recommandée pour une meilleure lisibilité. Quand l’attribut est appliqué, l’inclusion du mot Attribute est facultative.  
  
-   Toutes les classes d’attributs doivent hériter directement ou indirectement de **System.Attribute**.  
  
-   Dans Microsoft Visual Basic, toutes les classes d’attributs personnalisés doivent avoir l’attribut **AttributeUsageAttribute**.  
  
<a name="cpcondeclaringconstructors"></a>   
## Déclaration des constructeurs  
 Les attributs sont initialisés avec des constructeurs de la même façon que les classes traditionnelles. Le fragment de code suivant illustre un constructeur d’attribut classique. Ce constructeur public accepte un paramètre et définit sa valeur sur une variable membre.  
  
 [!code-cpp[Conceptual.Attributes.Usage#15](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#15)]
 [!code-csharp[Conceptual.Attributes.Usage#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#15)]
 [!code-vb[Conceptual.Attributes.Usage#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#15)]  
  
 Vous pouvez surcharger le constructeur pour qu’il reçoive différentes combinaisons de valeurs. Si vous définissez également une [propriété](../Topic/Properties%20Overview.md) pour votre classe d’attributs personnalisés, vous pouvez utiliser une combinaison de paramètres nommés et positionnels lors de l’initialisation de l’attribut. En général, vous définissez tous les paramètres obligatoires comme des paramètres positionnels et tous les paramètres facultatifs comme des paramètres nommés. Dans ce cas, l’attribut ne peut pas être initialisé sans le paramètre obligatoire. Tous les autres paramètres sont facultatifs. Notez que dans Visual Basic, les constructeurs d’une classe d’attributs ne doivent pas utiliser d’argument ParamArray.  
  
 L’exemple de code suivant montre comment un attribut qui utilise le constructeur précédent peut être appliqué à l’aide de paramètres obligatoires et facultatifs. Il suppose que l’attribut a une valeur booléenne obligatoire et une propriété de chaîne facultative.  
  
 [!code-cpp[Conceptual.Attributes.Usage#17](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#17)]
 [!code-csharp[Conceptual.Attributes.Usage#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#17)]
 [!code-vb[Conceptual.Attributes.Usage#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#17)]  
  
<a name="cpcondeclaringproperties"></a>   
## Déclaration des propriétés  
 Si vous voulez définir un paramètre nommé ou fournir un moyen facile de retourner les valeurs stockées par votre attribut, déclarez une [propriété](../Topic/Properties%20Overview.md). Les propriétés d’attribut doivent être déclarées comme des entités publiques avec une description du type de données à retourner. Définissez la variable qui contient la valeur de votre propriété et associez\-la aux méthodes **get** et **set**. L’exemple de code suivant montre comment implémenter une propriété simple dans votre attribut.  
  
 [!code-cpp[Conceptual.Attributes.Usage#16](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#16)]
 [!code-csharp[Conceptual.Attributes.Usage#16](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#16)]
 [!code-vb[Conceptual.Attributes.Usage#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#16)]  
  
<a name="cpconcustomattributeexample"></a>   
## Exemple d’attribut personnalisé  
 Cette section intègre les informations précédentes et montre comment concevoir un attribut simple qui documente des informations sur l’auteur d’une section de code. L’attribut de cet exemple stocke le nom et le niveau du programmeur, et indique si le code a été révisé. Il utilise trois variables privées pour stocker les valeurs réelles à enregistrer. Chaque variable est représentée par une propriété publique qui obtient et définit les valeurs. Enfin, le constructeur est défini avec deux paramètres obligatoires.  
  
 [!code-cpp[Conceptual.Attributes.Usage#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#4)]
 [!code-csharp[Conceptual.Attributes.Usage#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#4)]
 [!code-vb[Conceptual.Attributes.Usage#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#4)]  
  
 Vous pouvez appliquer cet attribut à l’aide du nom complet, `DeveloperAttribute`, ou à l’aide du nom abrégé, `Developer`, de l’une des manières suivantes.  
  
 [!code-cpp[Conceptual.Attributes.Usage#12](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#12)]
 [!code-csharp[Conceptual.Attributes.Usage#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#12)]
 [!code-vb[Conceptual.Attributes.Usage#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#12)]  
  
 Le premier exemple montre l’attribut appliqué uniquement avec les paramètres nommés obligatoires, tandis que le deuxième exemple montre l’attribut appliqué avec les paramètres obligatoires et facultatifs.  
  
## Voir aussi  
 <xref:System.Attribute?displayProperty=fullName>   
 <xref:System.AttributeUsageAttribute>   
 [Attributs](../../../docs/standard/attributes/index.md)