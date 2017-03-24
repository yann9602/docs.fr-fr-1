---
title: "Propriété d’indexeur d’extension (Visual Basic) | Documents Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.XmlPropertyExtensionIndexer
dev_langs:
- VB
helpviewer_keywords:
- Visual Basic code, accessing XML
- XML extension indexer [Visual Basic]
- extension indexer [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: a16a4b13-54be-432c-82b3-a87091464ada
caps.latest.revision: 22
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
ms.openlocfilehash: 25f434a5b5f8caf013ad5f778897e4e98e3d825d
ms.lasthandoff: 03/13/2017

---
# <a name="extension-indexer-property-visual-basic"></a>Propriété d’indexeur d’extension (Visual Basic)
Fournit un accès aux différents éléments d’une collection.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
object(index)  
```  
  
## <a name="parts"></a>Composants  
  
|Terme|Définition|  
|---|---|  
|`object`|Obligatoire. Collection pouvant être interrogée. Autrement dit, une collection qui implémente <xref:System.Collections.Generic.IEnumerable%601>ou <xref:System.Linq.IQueryable%601>.</xref:System.Linq.IQueryable%601> </xref:System.Collections.Generic.IEnumerable%601>|  
|(|Requis. Indique le début de la propriété d’indexeur.|  
|`index`|Obligatoire. Expression entière qui spécifie la position de base zéro d’un élément de la collection.|  
|)|Requis. Indique la fin de la propriété d’indexeur.|  
  
## <a name="return-value"></a>Valeur de retour  
 L’objet à partir de l’emplacement spécifié dans la collection, ou `Nothing` si l’index est hors limites.  
  
## <a name="remarks"></a>Notes  
 Vous pouvez utiliser la propriété d’indexeur d’extension pour accéder aux différents éléments d’une collection. Cette propriété d’indexeur est généralement utilisée lors de la sortie des propriétés d’axe XML. L’enfant XML et les propriétés d’axe de descendant XML retournent des collections de <xref:System.Xml.Linq.XElement>objets ou une valeur d’attribut.</xref:System.Xml.Linq.XElement>  
  
 Le [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compilateur convertit les propriétés indexeur d’extension en appels à la`ElementAtOrDefault` (méthode). Contrairement à un indexeur, le`ElementAtOrDefault` méthode `Nothing` si l’index est hors limites. Ce comportement est utile lorsque vous ne pouvez pas facilement déterminer le nombre d’éléments dans une collection.  
  
 Cette propriété d’indexeur est semblable à une propriété d’extension pour les collections qui implémentent <xref:System.Collections.Generic.IEnumerable%601>ou <xref:System.Linq.IQueryable%601>: elle est utilisée uniquement si la collection n’a pas un indexeur ou une propriété par défaut.</xref:System.Linq.IQueryable%601> </xref:System.Collections.Generic.IEnumerable%601>  
  
 Pour accéder à la valeur du premier élément dans une collection de <xref:System.Xml.Linq.XElement>ou <xref:System.Xml.Linq.XAttribute>des objets, vous pouvez utiliser le code XML `Value` propriété.</xref:System.Xml.Linq.XAttribute> </xref:System.Xml.Linq.XElement> Pour plus d’informations, consultez [propriété de valeur XML](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment utiliser l’indexeur d’extension pour accéder au deuxième nœud enfant dans une collection de <xref:System.Xml.Linq.XElement>objets.</xref:System.Xml.Linq.XElement> La collection est accessible à l’aide de la propriété d’axe enfant, qui obtient tous les éléments enfants nommés `phone` dans les `contact` objet.  
  
 [!code-vb[VbXMLSamples&#24;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/extension-indexer-property_1.vb)]  
  
 Ce code affiche le texte suivant :  
  
 `Second phone number: 425-555-0145`  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Xml.Linq.XElement>   
 [Propriétés d’axe XML](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)   
 [Littéraux XML](../../../visual-basic/language-reference/xml-literals/index.md)   
 [Création de code XML en Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)   
 [Propriété de valeur XML](../../../visual-basic/language-reference/xml-axis/xml-value-property.md)
