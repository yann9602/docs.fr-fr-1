---
title: "Littéral CDATA XML (Visual Basic) | Documents Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.XmlLiteralCdata
dev_langs:
- VB
helpviewer_keywords:
- CDATA literal [Visual Basic]
- XML CDATA literal [Visual Basic]
- XML literals [Visual Basic], CDATA
ms.assetid: 9eafb6a4-dd9d-4866-85e8-0654c65abc44
caps.latest.revision: 16
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
ms.openlocfilehash: 24e52bf203ff3df57e26137da24abcc2cb7e8e20
ms.lasthandoff: 03/13/2017

---
# <a name="xml-cdata-literal-visual-basic"></a>Littéral CDATA XML (Visual Basic)
Littéral représentant un <xref:System.Xml.Linq.XCData>objet.</xref:System.Xml.Linq.XCData>  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<![CDATA[content]]>  
```  
  
## <a name="parts"></a>Composants  
 `<![CDATA[`  
 Obligatoire. Indique le début de la section CDATA XML.  
  
 `content`  
 Obligatoire. Contenu de texte à afficher dans la section CDATA XML.  
  
 `]]>`  
 Obligatoire. Indique la fin de la section.  
  
## <a name="return-value"></a>Valeur de retour  
 Un <xref:System.Xml.Linq.XCData>objet.</xref:System.Xml.Linq.XCData>  
  
## <a name="remarks"></a>Remarques  
 Les sections XML CDATA contiennent du texte brut qui doit être inclus, mais non analysé, avec le code XML qui le contient. Une section CDATA XML peut contenir n’importe quel texte. Cela inclut les caractères XML réservés. La section XML CDATA se termine par la séquence »]] > ». Cela implique les points suivants :  
  
-   Vous ne pouvez pas utiliser une expression incorporée dans un littéral XML CDATA car les délimiteurs d’expression sont des contenus XML CDATA valides.  
  
-   Les sections XML CDATA ne peuvent pas être imbriquées, parce que `content` ne peut pas contenir la valeur «]] > ».  
  
 Vous pouvez assigner un littéral XML CDATA à une variable ou l’inclure dans un littéral d’élément XML.  
  
> [!NOTE]
>  Un littéral XML peut couvrir plusieurs lignes, mais n’utilise pas de caractères de continuation de ligne. Cela vous permet de copier le contenu d’un document XML et coller directement dans un [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] programme.  
  
 Le [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compilateur convertit le littéral XML CDATA en un appel à la <xref:System.Xml.Linq.XCData.%23ctor%2A>constructeur.</xref:System.Xml.Linq.XCData.%23ctor%2A>  
  
## <a name="example"></a>Exemple  
 L’exemple suivant crée une section CDATA qui contient le texte « peut contenir des littéraux \<XML > balises ».  
  
 [!code-vb[VbXMLSamples n °&23;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-cdata-literal_1.vb)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Xml.Linq.XCData></xref:System.Xml.Linq.XCData>   
 [Littéral d’élément XML](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)   
 [Littéraux XML](../../../visual-basic/language-reference/xml-literals/index.md)   
 [Création de code XML en Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
