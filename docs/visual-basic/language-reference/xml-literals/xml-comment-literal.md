---
title: "XML Comment Literal (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.XmlLiteralComment"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "comment literal [Visual Basic]"
  - "XML comments, adding [Visual Basic]"
  - "XML comment literal [Visual Basic]"
  - "XML literals [Visual Basic], comment"
ms.assetid: 634c1cee-5e01-48d0-88d7-2dd55e4a9e52
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 19
---
# XML Comment Literal (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Littéral représentant un objet <xref:System.Xml.Linq.XComment>.  
  
## Syntaxe  
  
```  
<!-- content -->  
```  
  
## Composants  
  
|||  
|-|-|  
|Terme|Définition|  
|`<!--`|Obligatoire.  Dénote le début du commentaire XML.|  
|`content`|Obligatoire.  Texte qui apparaît dans le commentaire XML.  Ne peut pas contenir une série de deux traits d'union \(\-\-\) ou finir par un trait d'union adjacent à la balise de fermeture.|  
|`-->`|Obligatoire.  Dénote la fin du commentaire XML.|  
  
## Valeur de retour  
 Objet <xref:System.Xml.Linq.XComment>.  
  
## Notes  
 Les littéraux de commentaire XML n'ont pas de contenu de document ; ils contiennent des informations à propos du document.  La section de commentaire XML se termine par la séquence « \-\-\> »,  ce qui implique les points suivants :  
  
-   Vous ne pouvez pas utiliser d'expression incorporée dans un littéral de commentaire XML parce que les séparateurs d'expression incorporés constituent un contenu de commentaire XML valide.  
  
-   Les sections de commentaire XML ne peuvent pas être imbriquées, parce que `content` ne peut pas contenir la valeur « \-\-\> ».  
  
 Vous pouvez assigner un littéral de commentaire XML à une variable ou vous pouvez l'inclure dans un littéral d'élément XML.  
  
> [!NOTE]
>  Un littéral XML peut couvrir plusieurs lignes, sans utiliser de caractères de continuation de ligne.  Cette fonctionnalité vous permet de copier le contenu d'un document XML et de le coller directement dans un programme [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)].  
  
 Le compilateur [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] convertit le commentaire littéral XML en appel au constructeur <xref:System.Xml.Linq.XComment.%23ctor%2A>.  
  
## Exemple  
 L'exemple suivant crée un commentaire XML qui contient le texte « Ceci est un commentaire ».  
  
 [!code-vb[VbXMLSamples#9](../../../visual-basic/language-reference/operators/codesnippet/visualbasic/xml-comment-literal_1.vb)]  
  
## Voir aussi  
 <xref:System.Xml.Linq.XComment>   
 [XML Element Literal](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)   
 [XML Literals](../../../visual-basic/language-reference/xml-literals/index.md)   
 [Creating XML in Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)