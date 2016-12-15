---
title: "White Space in XML Literals (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "white space [XML in Visual Basic]"
  - "XML literals [Visual Basic], white space"
ms.assetid: dfe3a9ff-d69a-418e-a6b5-476f4ed84219
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# White Space in XML Literals (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Le compilateur [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] n'incorpore que les caractères d'espace blanc significatifs d'un littéral XML, lorsqu'il crée un objet [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)].  Les caractères d'espace blanc insignifiants ne sont pas incorporés.  
  
## Espace blanc significatif et insignifiant  
 Les caractères d'espace blanc dans les littéraux XML ne sont significatifs que dans trois zones :  
  
-   Lorsqu'ils se trouvent dans une valeur d'attribut.  
  
-   Lorsqu'ils font partie du contenu du texte d'un élément et lorsque le texte contient également d'autres caractères.  
  
-   Lorsqu'ils se trouvent dans une expression incorporée pour le contenu du texte d'un élément.  
  
 Dans le cas contraire, le compilateur traite les caractères d'espace blanc comme insignifiants et ne les inclut pas à l'objet [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] du littéral.  
  
 Pour inclure un espace blanc insignifiant dans un littéral XML, utilisez une expression incorporée contenant un littéral de chaîne avec espace blanc.  
  
> [!NOTE]
>  Si l'attribut `xml:space` apparaît dans un littéral d'élément XML, le compilateur [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] inclut l'attribut dans l'objet <xref:System.Xml.Linq.XElement>, mais l'ajout de cet attribut ne change pas la manière dont le compilateur traite l'espace blanc.  
  
## Exemples  
 L'exemple suivant contient deux éléments XML, externe et interne.  Ces deux éléments contiennent un espace blanc dans leur contenu de texte.  L'espace blanc de l'élément externe est insignifiant, parce qu'il ne contient qu'un espace blanc et un élément XML.  L'espace blanc de l'élément interne est significatif, parce qu'il contient un espace blanc et du texte.  
  
 [!code-vb[VbXMLSamples#29](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/white-space-in-xml-literals_1.vb)]  
  
 Au moment de l'exécution ce code affiche le texte suivant.  
  
```  
<outer>  
  <inner>  
                                          Inner text  
                                      </inner>  
</outer>  
```  
  
## Voir aussi  
 [Creating XML in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)