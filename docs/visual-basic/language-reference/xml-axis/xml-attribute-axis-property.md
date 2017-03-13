---
title: "XML Attribute Axis Property (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.XmlPropertyAttributeAxis"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "attribute axis property [Visual Basic]"
  - "Visual Basic code, accessing XML"
  - "XML attribute axis property [Visual Basic]"
  - "XML axis [Visual Basic], attribute"
  - "XML [Visual Basic], accessing"
ms.assetid: 7a4777e1-0618-4de9-9510-fb9ace2bf4db
caps.latest.revision: 23
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 23
---
# XML Attribute Axis Property (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Fournit l'accès à la valeur d'un attribut pour un objet <xref:System.Xml.Linq.XElement> ou au premier élément d'une collection d'objets <xref:System.Xml.Linq.XElement>.  
  
## Syntaxe  
  
```  
  
      object.@attribute  
-or-  
object.@<attribute>  
```  
  
## Composants  
 `object`  
 Obligatoire.  Objet <xref:System.Xml.Linq.XElement> ou collection d'objets <xref:System.Xml.Linq.XElement>.  
  
 .@  
 Obligatoire.  Dénote le début d'une propriété d'axe d'attribut.  
  
 \<  
 Facultatif.  Dénote le début du nom de l'attribut lorsque `attribute` n'est pas un identificateur valide dans [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)].  
  
 `attribute`  
 Obligatoire.  Nom de l'attribut auquel accéder, du formulaire \[`prefix`:\]`name`.  
  
|Élément|Description|  
|-------------|-----------------|  
|`prefix`|Facultatif.  Préfixe d'espace de noms XML de l'attribut.  Doit être un espace de noms XML global, défini avec une instruction `Imports`.|  
|`name`|Obligatoire.  Nom d'attribut local.  Consultez [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).|  
  
 \>  
 Facultatif.  Dénote la fin du nom de l'attribut lorsque `attribute` n'est pas un identificateur valide dans [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)].  
  
## Valeur de retour  
 Chaîne contenant la valeur de `attribute`.  Si le nom de l'attribut n'existe pas, `Nothing` est retourné.  
  
## Notes  
 Vous pouvez utiliser une propriété d'axe d'attribut XML pour accéder à la valeur d'un attribut par nom à partir d'un objet <xref:System.Xml.Linq.XElement> ou à partir du premier élément d'une collection d'objets <xref:System.Xml.Linq.XElement>.  Vous pouvez récupérer une valeur d'attribut par nom ou ajouter un nouvel attribut à un élément en spécifiant un nouveau nom précédé de l'identificateur @.  
  
 Lorsque vous faites référence à la valeur d'un attribut XML à l'aide de l'identificateur @, la valeur de l'attribut est retournée sous la forme d'une chaîne et vous n'avez pas besoin de spécifier la propriété <xref:System.Xml.Linq.XAttribute.Value%2A> explicitement.  
  
 Les règles d'affectation de noms pour les attributs XML diffèrent de celles pour les identificateurs [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)]. Pour accéder à un attribut XML avec un nom qui ne correspond pas à un identificateur Visual Basic valide, placez le nom entre signes "inférieur à" et "supérieur à" \(\< et \>\).  
  
## Espaces de noms XML  
 Le nom dans une propriété de l'axe de l'attribut peut utiliser uniquement des préfixes d'espace de noms XML déclarés globalement à l'aide de l'instruction `Imports`.  Il ne peut pas utiliser de préfixes d'espaces de noms XML déclarés localement dans des littéraux d'éléments XML.  Pour plus d'informations, consultez [Imports Statement \(XML Namespace\)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).  
  
## Exemple  
 L'exemple suivant illustre comment obtenir les valeurs des attributs XML nommés `type` à partir d'une collection d'éléments XML nommés `phone`.  
  
 [!code-vb[VbXMLSamples#12](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-attribute-axis-property_1.vb)]  
  
 Ce code affiche le texte suivant :  
  
 `<phoneTypes>`  
  
 `<type>home</type>`  
  
 `<type>work</type>`  
  
 `</phoneTypes>`  
  
## Exemple  
 L'exemple suivant indique comment créer des attributs pour un élément XML de façon déclarative, dans le cadre du XML, et dynamiquement en ajoutant un attribut à une instance d'un objet <xref:System.Xml.Linq.XElement>.  L'attribut `type` est créé de façon déclarative tandis que l'attribut `owne` est créé dynamiquement.  
  
 [!code-vb[VbXMLSamples#44](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-attribute-axis-property_2.vb)]  
  
 Ce code affiche le texte suivant :  
  
```  
<phone type="home" owner="Harris, Phyllis">206-555-0144</phone>  
```  
  
## Exemple  
 L'exemple suivant utilise la syntaxe de crochets pointus pour obtenir la valeur de l'attribut XML nommé `number-type`, qui n'est pas un identificateur valide dans [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)].  
  
 [!code-vb[VbXMLSamples#13](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-attribute-axis-property_3.vb)]  
  
 Ce code affiche le texte suivant :  
  
 `Phone type: work`  
  
## Exemple  
 L'exemple suivant déclare `ns` en tant que préfixe d'espace de noms XML.  Il utilise alors le préfixe de l'espace de noms pour créer un littéral XML et accéder au premier nœud enfant avec le nom qualifié "`ns:name`".  
  
 [!code-vb[VbXMLSamples#14](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-attribute-axis-property_4.vb)]  
  
 Ce code affiche le texte suivant :  
  
 `Phone type: home`  
  
## Voir aussi  
 <xref:System.Xml.Linq.XElement>   
 [XML Axis Properties](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)   
 [XML Literals](../../../visual-basic/language-reference/xml-literals/index.md)   
 [Creating XML in Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)   
 [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)