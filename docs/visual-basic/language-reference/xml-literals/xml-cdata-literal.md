---
title: "XML CDATA Literal (Visual Basic) | Microsoft Docs"
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
  - "vb.XmlLiteralCdata"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "CDATA literal [Visual Basic]"
  - "XML CDATA literal [Visual Basic]"
  - "XML literals [Visual Basic], CDATA"
ms.assetid: 9eafb6a4-dd9d-4866-85e8-0654c65abc44
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# XML CDATA Literal (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Littéral représentant un objet <xref:System.Xml.Linq.XCData>.  
  
## Syntaxe  
  
```  
<![CDATA[content]]>  
```  
  
## Composants  
 `<![CDATA[`  
 Obligatoire.  Dénote le démarrage de la section XML CDATA.  
  
 `content`  
 Obligatoire.  Contenu de texte devant s'afficher dans la section XML CDATA.  
  
 `]]>`  
 Obligatoire.  Dénote la fin de la section.  
  
## Valeur de retour  
 Objet <xref:System.Xml.Linq.XCData>.  
  
## Notes  
 Les sections XML CDATA contiennent du texte brut qui doit être inclus, mais non analysé, avec le XML qui le contient.  Une section XML CDATA peut contenir n'importe quel texte,  notamment les caractères XML réservés.  La section XML CDATA se termine par la séquence « \]\]\> »,  ce qui implique les points suivants :  
  
-   Vous ne pouvez pas utiliser d'expression incorporée dans un littéral XML CDATA, parce que les délimiteurs d'expression sont des contenus XML CDATA valides.  
  
-   Les sections XML CDATA ne peuvent pas être imbriquées, parce que `content` ne peut pas contenir la valeur « \]\]\> ».  
  
 Vous pouvez assigner un littéral XML CDATA à une variable ou l'inclure dans un littéral d'élément XML.  
  
> [!NOTE]
>  Un littéral XML peut couvrir plusieurs lignes, mais n'utilise pas de caractères de continuation de ligne.  Cela vous permet de copier le contenu d'un document XML et de le coller directement dans un programme [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].  
  
 Le compilateur [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] convertit le littéral XML CDATA en un appel au constructeur <xref:System.Xml.Linq.XCData.%23ctor%2A>.  
  
## Exemple  
 L'exemple suivant crée une section CDATA qui contient le texte « Can contain literal \<XML\> tags » \(Peut contenir des balises \<XML\> littérales\).  
  
 [!code-vb[VbXMLSamples#23](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-cdata-literal_1.vb)]  
  
## Voir aussi  
 <xref:System.Xml.Linq.XCData>   
 [XML Element Literal](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)   
 [XML Literals](../../../visual-basic/language-reference/xml-literals/index.md)   
 [Creating XML in Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)