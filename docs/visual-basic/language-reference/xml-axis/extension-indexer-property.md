---
title: "Extension Indexer Property (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.XmlPropertyExtensionIndexer"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Visual Basic code, accessing XML"
  - "XML extension indexer [Visual Basic]"
  - "extension indexer [Visual Basic]"
  - "XML [Visual Basic], accessing"
ms.assetid: a16a4b13-54be-432c-82b3-a87091464ada
caps.latest.revision: 22
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 22
---
# Extension Indexer Property (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Fournit l'accès aux éléments individuels d'une collection.  
  
## Syntaxe  
  
```  
  
object(index)  
```  
  
## Composants  
  
|||  
|-|-|  
|Terme|Définition|  
|`object`|Obligatoire.  Collection requêtable.  Autrement dit, une collection qui implémente <xref:System.Collections.Generic.IEnumerable%601> ou <xref:System.Linq.IQueryable%601>.|  
|\(|Obligatoire.  Dénote le démarrage de la propriété de l'indexeur.|  
|`index`|Obligatoire.  Expression entière qui spécifie la position de base zéro d'un élément de la collection.|  
|\)|Obligatoire.  Dénote la fin de la propriété de l'indexeur.|  
  
## Valeur de retour  
 Objet de l'emplacement spécifié dans la collection, ou `Nothing` si l'index est hors limites.  
  
## Notes  
 Pour accéder à différents éléments d'une collection, utilisez la propriété de l'indexeur d'extension.  Cette propriété d'indexeur s'utilise en général sur la sortie de propriétés d'axe XML.  L'enfant XML et propriétés de l'axe du descendant XML retournent des collections d'objets <xref:System.Xml.Linq.XElement> ou une valeur d'attribut.  
  
 Le compilateur [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] convertit les propriétés de l'indexeur de l'extension en appels à la méthode `ElementAtOrDefault`. Contrairement à un indexeur de table, la méthode `ElementAtOrDefault` renvoie `Nothing` si l'index est hors limites.  Ce comportement est utile lorsque vous ne pouvez pas déterminer facilement le nombre d'éléments d'une collection.  
  
 Cette propriété d'indexeur est semblable à une propriété d'extension dans le cas de collections qui implémentent <xref:System.Collections.Generic.IEnumerable%601> ou <xref:System.Linq.IQueryable%601> : elle n'est utilisée que si la collection n'a ni indexeur, ni propriété par défaut.  
  
 Pour accéder à la valeur du premier élément d'une collection d'objets <xref:System.Xml.Linq.XElement> ou <xref:System.Xml.Linq.XAttribute>, vous pouvez utiliser la propriété XML `Value`.  Pour plus d'informations, consultez [XML Value Property](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).  
  
## Exemple  
 L'exemple suivant indique comment utiliser l'indexeur d'extension pour accéder au deuxième nœud enfant dans une collection d'objets <xref:System.Xml.Linq.XElement>.  Pour accéder à la collection, utilisez la propriété d'axe enfant, qui obtient tous les éléments enfants nommés `phone` dans l'objet `contact`.  
  
 [!code-vb[VbXMLSamples#24](../../../visual-basic/language-reference/operators/codesnippet/visualbasic/extension-indexer-property_1.vb)]  
  
 Ce code affiche le texte suivant :  
  
 `Second phone number: 425-555-0145`  
  
## Voir aussi  
 <xref:System.Xml.Linq.XElement>   
 [XML Axis Properties](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)   
 [XML Literals](../../../visual-basic/language-reference/xml-literals/index.md)   
 [Creating XML in Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)   
 [XML Value Property](../../../visual-basic/language-reference/xml-axis/xml-value-property.md)