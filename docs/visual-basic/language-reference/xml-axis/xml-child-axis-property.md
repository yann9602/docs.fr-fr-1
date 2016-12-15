---
title: "XML Child Axis Property (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.XmlPropertyChildAxis"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Visual Basic code, accessing XML"
  - "XML axis [Visual Basic], child"
  - "child axis property [Visual Basic]"
  - "XML child axis property [Visual Basic]"
  - "XML [Visual Basic], accessing"
ms.assetid: 89a59d00-985e-4f5c-b59f-29b47bad11cb
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# XML Child Axis Property (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Fournit un accès aux enfants de l'un des éléments suivants : un objet <xref:System.Xml.Linq.XElement>, un objet <xref:System.Xml.Linq.XDocument>, une collection d'objets <xref:System.Xml.Linq.XElement> ou une collection d'objets <xref:System.Xml.Linq.XDocument>.  
  
## Syntaxe  
  
```  
  
object.<child>  
```  
  
## Composants  
  
|||  
|-|-|  
|Terme|Définition|  
|`object`|Obligatoire.  Un objet <xref:System.Xml.Linq.XElement>, un objet <xref:System.Xml.Linq.XDocument>, une collection d'objets <xref:System.Xml.Linq.XElement> ou une collection d'objets <xref:System.Xml.Linq.XDocument>.|  
|.\<|Requis.  Indique le début d'une propriété d'axe enfant.|  
|`child`|Obligatoire.  Nom des nœuds enfants auxquels accéder, de la forme \[`prefix``:`\]`name`.<br /><br /> -   `Prefix` : facultatif.  Préfixe d'espace de noms XML pour le nœud enfant.  Doit être un espace de noms XML global défini avec une instruction `Imports`.<br />-   `Name` \- Requis.  Nom de nœud enfant local.  Consultez [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).|  
|\>|Requis.  Indique la fin d'une propriété d'axe enfant.|  
  
## Valeur de retour  
 Collection d'objets <xref:System.Xml.Linq.XElement>.  
  
## Notes  
 Vous pouvez utiliser une propriété d'axe enfant XML pour accéder aux nœuds enfants par nom, à partir d'un objet <xref:System.Xml.Linq.XElement> ou <xref:System.Xml.Linq.XDocument>, ou à partir d'une collection d'objets <xref:System.Xml.Linq.XElement> ou <xref:System.Xml.Linq.XDocument>.  Utilisez la propriété XML `Value` pour accéder à la valeur du premier nœud enfant dans la collection retournée.  Pour plus d'informations, consultez [XML Value Property](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).  
  
 Le compilateur [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] convertit les propriétés d'axes enfants en appels à la méthode <xref:System.Xml.Linq.XContainer.Elements%2A>.  
  
## Espaces de noms XML  
 Le nom inclus dans une propriété d'axe enfant peut utiliser uniquement des préfixes d'espace de noms XML déclarés globalement à l'aide de l'instruction `Imports`.  Il ne peut pas utiliser des préfixes d'espace de noms XML déclarés localement dans des littéraux d'éléments XML.  Pour plus d'informations, consultez [Imports Statement \(XML Namespace\)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).  
  
## Exemple  
 L'exemple suivant montre comment accéder aux nœuds enfants nommés `phone` à partir de l'objet `contact`.  
  
 [!code-vb[VbXMLSamples#17](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-child-axis-property_1.vb)]  
  
 Ce code affiche le texte suivant :  
  
 `Home Phone = 206-555-0144`  
  
## Exemple  
 L'exemple suivant montre comment accéder aux nœuds enfants nommés `phone` à partir de la collection retournée par la propriété d'axe enfant `contact` de l'objet `contacts`.  
  
 [!code-vb[VbXMLSamples#18](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-child-axis-property_2.vb)]  
  
 Ce code affiche le texte suivant :  
  
 `Home Phone = 206-555-0144`  
  
## Exemple  
 L'exemple suivant déclare `ns` en tant que préfixe d'espace de noms XML.  Il utilise ensuite le préfixe de l'espace de noms pour créer un littéral XML et accéder au premier nœud enfant avec le nom qualifié `ns:name`.  
  
 [!code-vb[VbXMLSamples#19](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-child-axis-property_3.vb)]  
  
 Ce code affiche le texte suivant :  
  
 `Patrick Hines`  
  
## Voir aussi  
 <xref:System.Xml.Linq.XElement>   
 [XML Axis Properties](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)   
 [XML Literals](../../../visual-basic/language-reference/xml-literals/index.md)   
 [Creating XML in Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)   
 [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)