---
title: "XML Value Property (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.XmlPropertyExtensionValue"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Value property [Visual Basic]"
  - "Visual Basic code, accessing XML"
  - "XML axis [Visual Basic], Value"
  - "XML Value property [Visual Basic]"
ms.assetid: 7ddd057a-a195-4e9b-ad8b-2ee0e615a20f
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# XML Value Property (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Fournit l'accès à la valeur du premier élément d'une collection d'objets <xref:System.Xml.Linq.XElement>.  
  
## Syntaxe  
  
```  
  
object.Value  
```  
  
## Composants  
  
|||  
|-|-|  
|Terme|Définition|  
|`object`|Obligatoire.  Collection d'objets <xref:System.Xml.Linq.XElement>.|  
  
## Valeur de retour  
 `String` qui contient la valeur du premier élément de la collection ou `Nothing` si la collection est vide.  
  
## Notes  
 La propriété <xref:System.Xml.Linq.XElement.Value%2A> facilite l'accès à la valeur du premier élément dans une collection d'objets <xref:System.Xml.Linq.XElement>.  Cette propriété vérifie tout d'abord si la collection contient au moins un objet.  Si la collection est vide, cette propriété ne donne aucun résultat \(`Nothing`\).  Dans le cas contraire, elle renvoie la valeur de la propriété <xref:System.Xml.Linq.XElement.Value%2A> du premier élément de la collection.  
  
> [!NOTE]
>  Lorsque vous accédez à la valeur d'un attribut XML à l'aide de l'identificateur @, la valeur de l'attribut est signalée en tant que `String` et vous n'avez pas besoin de spécifier la propriété <xref:System.Xml.Linq.XAttribute.Value%2A> explicitement.  
  
 Pour accéder à d'autres éléments d'une collection, utilisez la propriété de l'indexeur d'extension XML.  Pour plus d'informations, consultez [Extension Indexer Property](../../../visual-basic/language-reference/xml-axis/extension-indexer-property.md).  
  
## Héritage  
 La plupart des utilisateurs n'ont pas besoin d'implémenter <xref:System.Collections.Generic.IEnumerable%601>et peuvent donc ignorer cette section.  
  
 La propriété <xref:System.Xml.Linq.XElement.Value%2A> est une propriété d'extension pour les types qui implémentent `IEnumerable(Of XElement)`.  La liaison de cette propriété d'extension est similaire à la liaison de méthodes d'extension : si un type implémente l'une des interfaces et définit une propriété portant le nom « Valeur », cette propriété a priorité sur la propriété d'extension.  En d'autres termes, cette propriété <xref:System.Xml.Linq.XElement.Value%2A> peut être substituée en définissant une nouvelle propriété dans une classe qui implémente `IEnumerable(Of XElement)`.  
  
## Exemple  
 L'exemple suivant indique comment utiliser la propriété <xref:System.Xml.Linq.XElement.Value%2A> pour accéder au premier nœud d'une collection d'objets <xref:System.Xml.Linq.XElement>.  Cet exemple utilise la propriété d'axe enfant pour obtenir la collection de tous les nœuds enfants nommés `phone` et se trouvant dans l'objet `contact`.  
  
 [!code-vb[VbXMLSamples#15](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-value-property_1.vb)]  
  
 Ce code affiche le texte suivant :  
  
 `Phone number: 206-555-0144`  
  
## Exemple  
 L'exemple suivant indique comment obtenir la valeur d'un attribut XML à partir d'une collection d'objets <xref:System.Xml.Linq.XAttribute>.  L'exemple utilise la propriété de l'axe de l'attribut pour afficher la valeur de l'attribut `type` pour tous les éléments `phone`.  
  
 [!code-vb[VbXMLSamples#16](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-value-property_2.vb)]  
  
 Ce code affiche le texte suivant :  
  
 `home`  
  
 `work`  
  
## Voir aussi  
 <xref:System.Xml.Linq.XElement>   
 <xref:System.Collections.Generic.IEnumerable%601>   
 [XML Axis Properties](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)   
 [XML Literals](../../../visual-basic/language-reference/xml-literals/index.md)   
 [Creating XML in Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)   
 [méthodes d'extension.](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)   
 [Extension Indexer Property](../../../visual-basic/language-reference/xml-axis/extension-indexer-property.md)   
 [XML Child Axis Property](../../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md)   
 [XML Attribute Axis Property](../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md)