---
title: "Propriété d’axe Descendant XML (Visual Basic) | Documents Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.XmlPropertyDescendantsAxis
dev_langs:
- VB
helpviewer_keywords:
- Visual Basic code, accessing XML
- XML descendant axis property [Visual Basic]
- descendant axis property [Visual Baisc]
- XML axis [Visual Basic], descendant
- XML [Visual Basic], accessing
ms.assetid: a178f85b-5d54-438f-8479-40b62af6fe76
caps.latest.revision: 14
author: stevehoag
ms.author: shoag
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
ms.openlocfilehash: 434dc90c643381bdc27b2da54a7418e39bf15e98
ms.lasthandoff: 03/13/2017

---
# <a name="xml-descendant-axis-property-visual-basic"></a>Propriété d'axe descendant XML (Visual Basic)
Fournit l’accès aux descendants de ce qui suit : un <xref:System.Xml.Linq.XElement>objet, un <xref:System.Xml.Linq.XDocument>objet, une collection de <xref:System.Xml.Linq.XElement>objets, ou une collection de <xref:System.Xml.Linq.XDocument>objets.</xref:System.Xml.Linq.XDocument> </xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XDocument> </xref:System.Xml.Linq.XElement>  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
object...<descendant>  
```  
  
## <a name="parts"></a>Composants  
 `object`  
 Obligatoire. Un <xref:System.Xml.Linq.XElement>objet, un <xref:System.Xml.Linq.XDocument>objet, une collection de <xref:System.Xml.Linq.XElement>objets, ou une collection de <xref:System.Xml.Linq.XDocument>objets.</xref:System.Xml.Linq.XDocument> </xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XDocument> </xref:System.Xml.Linq.XElement>  
  
 ...<  
 Requis. Indique le début d’une propriété d’axe descendant.  
  
 `descendant`  
 Obligatoire. Nom des nœuds descendants auxquels accéder, sous la forme [`prefix``:`]`name`.  
  
|Élément|Description|  
|----------|-----------------|  
|`prefix`|Facultatif. Préfixe d’espace de noms XML pour le nœud descendant. Doit être un espace de noms XML global qui est défini en utilisant un `Imports` instruction.|  
|`name`|Obligatoire. Nom local du nœud descendant. Consultez la page [nom des attributs et éléments XML déclarés](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).|  
  
 \>  
 Obligatoire. Indique la fin d’une propriété d’axe descendant.  
  
## <a name="return-value"></a>Valeur de retour  
 Une collection de <xref:System.Xml.Linq.XElement>objets.</xref:System.Xml.Linq.XElement>  
  
## <a name="remarks"></a>Remarques  
 Vous pouvez utiliser une propriété d’axe descendant XML pour accéder aux nœuds descendants par nom d’un <xref:System.Xml.Linq.XElement>ou <xref:System.Xml.Linq.XDocument>objet, ou à partir d’une collection de <xref:System.Xml.Linq.XElement>ou <xref:System.Xml.Linq.XDocument>objets.</xref:System.Xml.Linq.XDocument> </xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XDocument> </xref:System.Xml.Linq.XElement> Utilisez le code XML `Value` propriété pour accéder à la valeur du premier nœud descendant dans la collection retournée. Pour plus d’informations, consultez [propriété de valeur XML](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).  
  
 Le [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compilateur convertit des propriétés d’axes descendants en appels à la <xref:System.Xml.Linq.XContainer.Descendants%2A>méthode.</xref:System.Xml.Linq.XContainer.Descendants%2A>  
  
## <a name="xml-namespaces"></a>Espaces de noms XML  
 Le nom d’une propriété d’axe descendant peut utiliser uniquement les espaces de noms XML déclarés globalement avec le `Imports` instruction. Il ne peut pas utiliser les espaces de noms XML déclarés localement dans les littéraux d’éléments XML. Pour plus d’informations, consultez [l’instruction Imports (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment accéder à la valeur du premier nœud descendant nommé `name` et les valeurs de tous les nœuds descendants nommés `phone` à partir de la `contacts` objet.  
  
 [!code-vb[VbXMLSamples&#25;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-descendant-axis-property_1.vb)]  
  
 Ce code affiche le texte suivant :  
  
 `Name: Patrick Hines`  
  
 `Home Phone = 206-555-0144`  
  
## <a name="example"></a>Exemple  
 L'exemple suivant déclare `ns` en tant que préfixe d'espace de noms XML. Il utilise ensuite le préfixe d’espace de noms pour créer un littéral XML et accéder à la valeur du premier nœud enfant avec le nom qualifié `ns:name`.  
  
 [!code-vb[VbXMLSamples&#26;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-descendant-axis-property_2.vb)]  
  
 Ce code affiche le texte suivant :  
  
 `Name: Patrick Hines`  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Xml.Linq.XElement>   
 [Propriétés d’axe XML](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)   
 [Littéraux XML](../../../visual-basic/language-reference/xml-literals/index.md)   
 [Création de code XML en Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)   
 [Nom des attributs et des éléments XML déclarés](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
