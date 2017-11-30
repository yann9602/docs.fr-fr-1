---
title: "Propriété de valeur XML (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.XmlPropertyExtensionValue
helpviewer_keywords:
- Value property [Visual Basic]
- Visual Basic code, accessing XML
- XML axis [Visual Basic], Value
- XML Value property [Visual Basic]
ms.assetid: 7ddd057a-a195-4e9b-ad8b-2ee0e615a20f
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6c52ac09e209d6e3f0cfd877a071cbbe3ab96f18
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="xml-value-property-visual-basic"></a>Propriété de valeur XML (Visual Basic)
Fournit l’accès à la valeur du premier élément d’une collection de <xref:System.Xml.Linq.XElement> objets.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
object.Value  
```  
  
## <a name="parts"></a>Composants  
  
|Terme|Définition|  
|---|---|  
|`object`|Obligatoire. Collection d'objets <xref:System.Xml.Linq.XElement>.|  
  
## <a name="return-value"></a>Valeur de retour  
 A `String` qui contient la valeur du premier élément de la collection, ou `Nothing` si la collection est vide.  
  
## <a name="remarks"></a>Remarques  
 Le <xref:System.Xml.Linq.XElement.Value%2A> propriété permet d’accéder à la valeur du premier élément dans une collection de <xref:System.Xml.Linq.XElement> objets. Cette propriété vérifie d’abord si la collection contient au moins un objet. Si la collection est vide, cette propriété retourne `Nothing`. Sinon, cette propriété retourne la valeur de la <xref:System.Xml.Linq.XElement.Value%2A> propriété du premier élément dans la collection.  
  
> [!NOTE]
>  Quand vous accédez à la valeur d’un attribut XML à l’aide du ' @' identificateur, la valeur d’attribut est retournée en tant qu’un `String` et vous n’avez pas besoin de spécifier explicitement le <xref:System.Xml.Linq.XAttribute.Value%2A> propriété.  
  
 Pour accéder aux autres éléments d’une collection, vous pouvez utiliser la propriété indexeur d’extension XML. Pour plus d’informations, consultez [propriété d’indexeur d’Extension](../../../visual-basic/language-reference/xml-axis/extension-indexer-property.md).  
  
## <a name="inheritance"></a>Héritage  
 La plupart des utilisateurs n’aura pas d’implémenter <xref:System.Collections.Generic.IEnumerable%601>et peuvent donc ignorer cette section.  
  
 Le <xref:System.Xml.Linq.XElement.Value%2A> propriété est une propriété d’extension pour les types qui implémentent `IEnumerable(Of XElement)`. La liaison de cette propriété d’extension est similaire à la liaison de méthodes d’extension : si un type implémente l’une des interfaces et définit une propriété portant le nom « Valeur », cette propriété est prioritaire sur la propriété d’extension. En d’autres termes, cela <xref:System.Xml.Linq.XElement.Value%2A> propriété peut être substituée en définissant une nouvelle propriété dans une classe qui implémente `IEnumerable(Of XElement)`.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment utiliser le <xref:System.Xml.Linq.XElement.Value%2A> propriété pour accéder au premier nœud dans une collection de <xref:System.Xml.Linq.XElement> objets. L’exemple utilise la propriété d’axe enfant pour obtenir la collection de tous les nœuds enfants nommés `phone` qui se trouvent dans le `contact` objet.  
  
 [!code-vb[VbXMLSamples#15](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-value-property_1.vb)]  
  
 Ce code affiche le texte suivant :  
  
 `Phone number: 206-555-0144`  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment obtenir la valeur d’un attribut XML à partir d’une collection de <xref:System.Xml.Linq.XAttribute> objets. L’exemple utilise la propriété axe d’attribut pour afficher la valeur de la `type` attribut pour tous les le `phone` éléments.  
  
 [!code-vb[VbXMLSamples#16](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-value-property_2.vb)]  
  
 Ce code affiche le texte suivant :  
  
 `home`  
  
 `work`  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Xml.Linq.XElement>  
 <xref:System.Collections.Generic.IEnumerable%601>  
 [Propriétés d’axe XML](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)  
 [Littéraux XML](../../../visual-basic/language-reference/xml-literals/index.md)  
 [Création de code XML dans Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [Méthodes d’extension](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)  
 [Propriété d’indexeur d’extension](../../../visual-basic/language-reference/xml-axis/extension-indexer-property.md)  
 [Propriété d’axe enfant XML](../../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md)  
 [Propriété d’axe d’attribut XML](../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md)
