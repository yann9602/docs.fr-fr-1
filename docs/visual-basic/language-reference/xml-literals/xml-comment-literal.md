---
title: "Littéral de commentaire XML (Visual Basic) | Documents Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.XmlLiteralComment
dev_langs:
- VB
helpviewer_keywords:
- comment literal [Visual Basic]
- XML comments, adding [Visual Basic]
- XML comment literal [Visual Basic]
- XML literals [Visual Basic], comment
ms.assetid: 634c1cee-5e01-48d0-88d7-2dd55e4a9e52
caps.latest.revision: 19
author: dotnet-bot
ms.author: dotnetcontent
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
ms.openlocfilehash: 88cfb984be42345ae1e5c998cf82aa1415d2455e
ms.lasthandoff: 03/13/2017

---
# <a name="xml-comment-literal-visual-basic"></a>Littéraux de commentaires XML (Visual Basic)
Littéral représentant un <xref:System.Xml.Linq.XComment>objet.</xref:System.Xml.Linq.XComment>  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<!-- content -->  
```  
  
## <a name="parts"></a>Composants  
  
|Terme|Définition|  
|---|---|  
|`<!--`|Obligatoire. Indique le début du commentaire XML.|  
|`content`|Obligatoire. Texte à afficher dans le commentaire XML. Ne peut pas contenir une série de deux traits d’union (-) ou se terminer par un trait d’union adjacent à la balise de fermeture.|  
|`-->`|Obligatoire. Indique la fin du commentaire XML.|  
  
## <a name="return-value"></a>Valeur de retour  
 Un <xref:System.Xml.Linq.XComment>objet.</xref:System.Xml.Linq.XComment>  
  
## <a name="remarks"></a>Remarques  
 Littéraux de commentaires XML ne contiennent pas de contenu de document ; ils contiennent des informations sur le document. La section de commentaire XML se termine par la séquence «--> ». Cela implique les points suivants :  
  
-   Vous ne pouvez pas utiliser une expression incorporée dans un littéral de commentaire XML parce que les délimiteurs d’expression sont le contenu de commentaire XML valide.  
  
-   Sections de commentaire XML ne peuvent pas être imbriquées, parce que `content` ne peut pas contenir la valeur «--> ».  
  
 Vous pouvez affecter un littéral de commentaire XML à une variable, ou vous pouvez l’inclure dans un littéral d’élément XML.  
  
> [!NOTE]
>  Un littéral XML peut couvrir plusieurs lignes sans utiliser de caractères de continuation de ligne. Cette fonctionnalité vous permet de copier le contenu d’un document XML et coller directement dans un [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] programme.  
  
 Le [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compilateur convertit le commentaire littéral XML en un appel à la <xref:System.Xml.Linq.XComment.%23ctor%2A>constructeur.</xref:System.Xml.Linq.XComment.%23ctor%2A>  
  
## <a name="example"></a>Exemple  
 L’exemple suivant crée un commentaire XML qui contient le texte « Ceci est un commentaire ».  
  
 [!code-vb[VbXMLSamples&#9;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-comment-literal_1.vb)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Xml.Linq.XComment></xref:System.Xml.Linq.XComment>   
 [Littéral d’élément XML](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)   
 [Littéraux XML](../../../visual-basic/language-reference/xml-literals/index.md)   
 [Création de code XML en Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
