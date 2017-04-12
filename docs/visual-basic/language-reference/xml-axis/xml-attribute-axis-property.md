---
title: "Propriété d’axe attribut XML (Visual Basic) | Documents Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.XmlPropertyAttributeAxis
dev_langs:
- VB
helpviewer_keywords:
- attribute axis property [Visual Basic]
- Visual Basic code, accessing XML
- XML attribute axis property [Visual Basic]
- XML axis [Visual Basic], attribute
- XML [Visual Basic], accessing
ms.assetid: 7a4777e1-0618-4de9-9510-fb9ace2bf4db
caps.latest.revision: 23
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 94211f7c951976426ba17e73df214444a6c227b4
ms.lasthandoff: 03/13/2017

---
# <a name="xml-attribute-axis-property-visual-basic"></a>Propriété d'axe d'attribut XML (Visual Basic)
Fournit l’accès à la valeur d’un attribut pour un <xref:System.Xml.Linq.XElement>objet ou au premier élément dans une collection de <xref:System.Xml.Linq.XElement>objets.</xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XElement>  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      object.@attribute  
-or-  
object.@<attribute>  
```  
  
## <a name="parts"></a>Composants  
 `object`  
 Obligatoire. Un <xref:System.Xml.Linq.XElement>objet ou une collection de <xref:System.Xml.Linq.XElement>objets.</xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XElement>  
  
 .@  
 Requis. Indique le début d’une propriété d’axe d’attribut.  
  
 <  
 Facultatif. Indique le début du nom de l’attribut lorsque `attribute` n’est pas un identificateur valide dans [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].  
  
 `attribute`  
 Obligatoire. Nom de l’attribut auquel accéder, du formulaire [`prefix`:]`name`.  
  
|Élément|Description|  
|----------|-----------------|  
|`prefix`|Facultatif. Préfixe d’espace de noms XML pour l’attribut. Doit être un espace de noms XML global défini avec une instruction `Imports`.|  
|`name`|Obligatoire. Nom d’attribut local. Consultez la page [nom des attributs et éléments XML déclarés](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).|  
  
 \>  
 Facultatif. Indique la fin du nom de l’attribut lorsque `attribute` n’est pas un identificateur valide dans [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].  
  
## <a name="return-value"></a>Valeur de retour  
 Chaîne qui contient la valeur de `attribute`. Si le nom de l’attribut n’existe pas, `Nothing` est retourné.  
  
## <a name="remarks"></a>Remarques  
 Vous pouvez utiliser une propriété d’axe XML attribut pour accéder à la valeur d’un attribut par nom d’un <xref:System.Xml.Linq.XElement>objet ou du premier élément dans une collection de <xref:System.Xml.Linq.XElement>objets.</xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XElement> Vous pouvez récupérer une valeur d’attribut par nom ou ajouter un nouvel attribut à un élément en spécifiant un nouveau nom précédé par l’identificateur @.  
  
 Lorsque vous faites référence à un attribut XML en utilisant l’identificateur @, la valeur d’attribut est retournée sous forme de chaîne et vous n’avez pas besoin de spécifier explicitement le <xref:System.Xml.Linq.XAttribute.Value%2A>propriété.</xref:System.Xml.Linq.XAttribute.Value%2A>  
  
 Les règles d’affectation de noms pour les attributs XML diffèrent des règles d’affectation de noms pour les [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] identificateurs. Pour accéder à un attribut XML qui a un nom qui n’est pas un identificateur Visual Basic valid, placez le nom entre crochets pointus (\< et >).  
  
## <a name="xml-namespaces"></a>Espaces de noms XML  
 Le nom de la propriété d’axe d’attribut peut utiliser uniquement des préfixes d’espace de noms XML, déclarés globalement à l’aide de la `Imports` instruction. Il ne peut pas utiliser des préfixes d'espace de noms XML déclarés localement dans des littéraux d'éléments XML. Pour plus d’informations, consultez [l’instruction Imports (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment obtenir les valeurs des attributs XML nommés `type` à partir d’une collection d’éléments XML nommés `phone`.  
  
 [!code-vb[VbXMLSamples&#12;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-attribute-axis-property_1.vb)]  
  
 Ce code affiche le texte suivant :  
  
 `<phoneTypes>`  
  
 `<type>home</type>`  
  
 `<type>work</type>`  
  
 `</phoneTypes>`  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment créer des attributs pour un élément XML de façon déclarative, dans le cadre du XML et dynamiquement en ajoutant un attribut à une instance d’un <xref:System.Xml.Linq.XElement>objet.</xref:System.Xml.Linq.XElement> Le `type` attribut est créé de façon déclarative et `owne`r attribut est créée dynamiquement.  
  
 [!code-vb[VbXMLSamples&#44;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-attribute-axis-property_2.vb)]  
  
 Ce code affiche le texte suivant :  
  
```  
<phone type="home" owner="Harris, Phyllis">206-555-0144</phone>  
```  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise la syntaxe de crochets pointus pour obtenir la valeur de l’attribut XML nommé `number-type`, qui n’est pas un identificateur valide dans [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].  
  
 [!code-vb[VbXMLSamples&#13;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-attribute-axis-property_3.vb)]  
  
 Ce code affiche le texte suivant :  
  
 `Phone type: work`  
  
## <a name="example"></a>Exemple  
 L'exemple suivant déclare `ns` en tant que préfixe d'espace de noms XML. Il utilise ensuite le préfixe d’espace de noms pour créer un littéral XML et accéder au premier nœud enfant avec le nom qualifié «`ns:name`».  
  
 [!code-vb[VbXMLSamples&#14;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-attribute-axis-property_4.vb)]  
  
 Ce code affiche le texte suivant :  
  
 `Phone type: home`  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Xml.Linq.XElement>   
 [Propriétés d’axe XML](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)   
 [Littéraux XML](../../../visual-basic/language-reference/xml-literals/index.md)   
 [Création de code XML en Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)   
 [Nom des attributs et des éléments XML déclarés](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
