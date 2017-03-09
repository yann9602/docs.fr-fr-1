---
title: "XML Descendant Axis Property (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.XmlPropertyDescendantsAxis"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Visual Basic code, accessing XML"
  - "XML descendant axis property [Visual Basic]"
  - "descendant axis property [Visual Baisc]"
  - "XML axis [Visual Basic], descendant"
  - "XML [Visual Basic], accessing"
ms.assetid: a178f85b-5d54-438f-8479-40b62af6fe76
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 14
---
# XML Descendant Axis Property (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Fournit l'accès aux descendants de l'un des éléments suivants : un objet <xref:System.Xml.Linq.XElement>, un objet <xref:System.Xml.Linq.XDocument>, une collection d'objets <xref:System.Xml.Linq.XElement> ou une collection d'objets <xref:System.Xml.Linq.XDocument>.  
  
## Syntaxe  
  
```  
  
object...<descendant>  
```  
  
## Composants  
 `object`  
 Obligatoire.  Un objet <xref:System.Xml.Linq.XElement>, un objet <xref:System.Xml.Linq.XDocument>, une collection d'objets <xref:System.Xml.Linq.XElement> ou une collection d'objets <xref:System.Xml.Linq.XDocument>.  
  
 ...\<  
 Obligatoire.  Dénote le démarrage d'une propriété d'axe descendant.  
  
 `descendant`  
 Obligatoire.  Nom des nœuds descendants auxquels accéder, sous la forme \[`prefix``:`\]`name`.  
  
|Élément|Description|  
|-------------|-----------------|  
|`prefix`|Facultatif.  Préfixe d'espace de noms XML pour le nœud descendant.  Doit être un espace de noms XML global défini à l'aide de l'instruction `Imports`.|  
|`name`|Obligatoire.  Nom local du nœud descendant.  Consultez [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).|  
  
 \>  
 Obligatoire.  Dénote la fin d'une propriété d'axe descendant.  
  
## Valeur de retour  
 Collection d'objets <xref:System.Xml.Linq.XElement>.  
  
## Notes  
 Vous pouvez utiliser une propriété d'axe descendant XML pour accéder aux nœuds descendants par nom, à partir d'un objet <xref:System.Xml.Linq.XElement> ou <xref:System.Xml.Linq.XDocument>, ou d'une collection d'objets <xref:System.Xml.Linq.XElement> ou <xref:System.Xml.Linq.XDocument>.  Utilisez la propriété XML `Value` pour accéder à la valeur du premier nœud descendant dans la collection retournée.  Pour plus d'informations, consultez [XML Value Property](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).  
  
 Le compilateur [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] convertit des propriétés d'axes descendants en appels à la méthode <xref:System.Xml.Linq.XContainer.Descendants%2A>.  
  
## Espaces de noms XML  
 Dans une propriété d'axe descendant, le nom ne peut utiliser que les espaces de noms XML déclarés globalement à l'aide de l'instruction `Imports`.  Il ne peut utiliser d'espaces de noms XML déclarés localement dans les littéraux d'éléments XML.  Pour plus d'informations, consultez [Imports Statement \(XML Namespace\)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).  
  
## Exemple  
 L'exemple suivant indique comment accéder à la valeur du premier nœud descendant nommé `name` et aux valeurs de tous les nœuds descendants nommés `phone` à partir de l'objet `contacts`.  
  
 [!code-vb[VbXMLSamples#25](../../../visual-basic/language-reference/operators/codesnippet/visualbasic/xml-descendant-axis-prop_1.vb)]  
  
 Ce code affiche le texte suivant :  
  
 `Name: Patrick Hines`  
  
 `Home Phone = 206-555-0144`  
  
## Exemple  
 L'exemple suivant déclare `ns` en tant que préfixe d'espace de noms XML.  Il utilise alors le préfixe de l'espace de noms pour créer un littéral XML et accéder à la valeur du premier nœud enfant, avec le nom qualifié "`ns:name`".  
  
 [!code-vb[VbXMLSamples#26](../../../visual-basic/language-reference/operators/codesnippet/visualbasic/xml-descendant-axis-prop_2.vb)]  
  
 Ce code affiche le texte suivant :  
  
 `Name: Patrick Hines`  
  
## Voir aussi  
 <xref:System.Xml.Linq.XElement>   
 [XML Axis Properties](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)   
 [XML Literals](../../../visual-basic/language-reference/xml-literals/index.md)   
 [Creating XML in Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)   
 [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)