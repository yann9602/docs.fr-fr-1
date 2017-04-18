---
title: "Espace blanc dans les littéraux XML (Visual Basic) | Documents Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- white space [XML in Visual Basic]
- XML literals [Visual Basic], white space
ms.assetid: dfe3a9ff-d69a-418e-a6b5-476f4ed84219
caps.latest.revision: 14
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
ms.openlocfilehash: b98a88696f24cc0b95401812471d13acea4faa6d
ms.lasthandoff: 03/13/2017

---
# <a name="white-space-in-xml-literals-visual-basic"></a>Espaces blancs dans les littéraux XML (Visual Basic)
Le [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compilateur incorpore uniquement les caractères d’espaces blancs significatifs d’un littéral XML, lorsqu’il crée un [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] objet. Les espaces blancs non significatifs ne sont pas incorporés.  
  
## <a name="significant-and-insignificant-white-space"></a>Espaces blancs significatifs et non significatifs  
 Espaces blancs dans les littéraux XML sont significatifs que dans trois zones :  
  
-   Lorsqu’ils sont dans une valeur d’attribut.  
  
-   Lorsqu’ils font partie d’un élément contenu de texte et le texte contient également d’autres caractères.  
  
-   Lorsqu’ils sont dans une expression incorporée pour le contenu de texte d’un élément.  
  
 Dans le cas contraire, le compilateur traite les caractères d’espace blanc comme insignifiants et ne les inclut pas dans le [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] objet du littéral.  
  
 Pour inclure des espaces blancs non significatifs dans un littéral XML, utilisez une expression incorporée contenant un littéral de chaîne avec les espaces blancs.  
  
> [!NOTE]
>  Si le `xml:space` attribut apparaît dans un élément XML littéral, le [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compilateur inclut l’attribut dans le <xref:System.Xml.Linq.XElement>objet, mais l’ajout de cet attribut ne modifie pas la façon dont le compilateur traite l’espace blanc.</xref:System.Xml.Linq.XElement>  
  
## <a name="examples"></a>Exemples  
 L’exemple suivant contient deux éléments XML, externes et internes. Les deux éléments contiennent un espace blanc dans leur contenu de texte. L’espace blanc dans l’élément externe est insignifiant, car elle contient uniquement un espace blanc et un élément XML. L’espace blanc dans l’élément interne est significatif, car elle contient un espace blanc et texte.  
  
 [!code-vb[VbXMLSamples&#29;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/white-space-in-xml-literals_1.vb)]  
  
 Lors de l’exécution, ce code affiche le texte suivant.  
  
```  
<outer>  
  <inner>  
                                          Inner text  
                                      </inner>  
</outer>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Création de code XML en Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
