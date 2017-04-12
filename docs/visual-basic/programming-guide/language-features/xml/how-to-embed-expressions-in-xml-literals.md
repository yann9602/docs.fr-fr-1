---
title: "Comment : incorporer des Expressions dans des littéraux XML (Visual Basic) | Documents Microsoft"
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
- embedded expressions [Visual Basic]
- XML literals [Visual Basic], embedded expressions
ms.assetid: 75016fad-0141-42de-8564-5051be29487e
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
ms.openlocfilehash: 40b0e4273223093262bc54a2b13d28fc93a44c69
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-embed-expressions-in-xml-literals-visual-basic"></a>Comment : incorporer des expressions dans des littéraux XML (Visual Basic)
Vous pouvez combiner des littéraux XML avec des expressions incorporées pour créer un document XML, fragment ou élément qui contient le contenu créé au moment de l’exécution. Les exemples suivants montrent comment utiliser des expressions incorporées pour remplir le contenu de l’élément, les attributs et les noms d’élément en cours d’exécution.  
  
 La syntaxe pour une expression incorporée est `<%=` `exp` `%>`, qui est la même syntaxe que [!INCLUDE[vstecasp](../../../../csharp/language-reference/preprocessor-directives/includes/vstecasp_md.md)] utilise. Pour plus d’informations, consultez [Expressions incorporées en XML](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).  
  
 Vous pouvez également utiliser le [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] API pour créer des [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] objets. Pour plus d’informations, consultez <xref:System.Xml.Linq.XElement>.</xref:System.Xml.Linq.XElement>  
  
## <a name="procedures"></a>Procédures  
  
#### <a name="to-insert-text-as-element-content"></a>Pour insérer du texte en tant que contenu de l’élément  
  
-   L’exemple suivant montre comment insérer le texte contenu dans le `contactName` variable entre les éléments de nom d’ouverture et de fermeture.  
  
     [!code-vb[VbXMLSamples n °&39;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-embed-expressions-in-xml-literals_1.vb)]  
  
     Cet exemple génère la sortie suivante :  
  
    ```  
    <contact>  
      <name>Patrick Hines</name>  
    </contact>  
    ```  
  
#### <a name="to-insert-text-as-an-attribute-value"></a>Pour insérer du texte comme valeur d’attribut  
  
-   L’exemple suivant montre comment insérer le texte contenu dans le `phoneType` variable comme valeur de la `type` attribut.  
  
     [!code-vb[VbXMLSamples numéro&40;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-embed-expressions-in-xml-literals_2.vb)]  
  
     Cet exemple génère la sortie suivante :  
  
    ```  
    <contact>  
      <phone type="home">206-555-0144</phone>  
    </contact>  
    ```  
  
#### <a name="to-insert-text-for-an-element-name"></a>Pour insérer du texte pour un nom d’élément  
  
-   L’exemple suivant montre comment insérer le texte contenu dans le `elementName` variable en tant que le nom d’un élément.  
  
     Lorsque vous créez des éléments à l’aide de cette technique, vous devez les fermer avec la \</ > balise.  
  
     [!code-vb[# VbXMLSamples&41;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-embed-expressions-in-xml-literals_3.vb)]  
  
     Cet exemple génère la sortie suivante :  
  
    ```  
    <contact>  
      <name>Patrick Hines</name>  
    </contact>  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : créer des littéraux XML](../../../../visual-basic/programming-guide/language-features/xml/how-to-create-xml-literals.md)   
 [Expressions incorporées en XML](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)   
 [Création de code XML en Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)   
 [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)
