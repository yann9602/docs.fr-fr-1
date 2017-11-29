---
title: "Comment : accéder à des éléments enfants XML (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XML axis [Visual Basic], child
- child axis property [Visual Basic]
- XML child axis property [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: 6689eb36-c471-469f-a82d-099ab8197b25
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5d3a708b787ad38f08d4673d4003db839f6cf6a9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-access-xml-child-elements-visual-basic"></a>Comment : accéder à des éléments enfants XML (Visual Basic)
Cet exemple montre comment utiliser un enfant de propriété d’axe pour accéder à tous les éléments enfants XML portant un nom spécifié dans un élément XML. En particulier, il utilise le <xref:System.Xml.Linq.XElement.Value%2A> propriété à obtenir la valeur du premier élément dans la collection qui le `name` retourne de propriété d’axe enfant. Le `name` propriété d’axe enfant obtient tous les éléments enfants nommés `phone` dans le `contact` objet. Cet exemple utilise également la `phone` propriété d’axe enfant pour accéder à tous les éléments enfants nommés `phone` qui sont contenues dans le `contact` objet.  
  
## <a name="example"></a>Exemple  
 [!code-vb[VbXMLSamples#10](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-access-xml-child-elements_1.vb)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Cet exemple nécessite :  
  
-   une référence à l'espace de noms <xref:System.Xml.Linq>.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>  
 [Propriété d’axe enfant XML](../../../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md)  
 [Propriété de valeur XML](../../../../visual-basic/language-reference/xml-axis/xml-value-property.md)  
 [Accès au code XML dans Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)  
 [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)
