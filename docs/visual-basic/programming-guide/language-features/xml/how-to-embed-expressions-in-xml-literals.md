---
title: "How to: Embed Expressions in XML Literals (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "embedded expressions [Visual Basic]"
  - "XML literals [Visual Basic], embedded expressions"
ms.assetid: 75016fad-0141-42de-8564-5051be29487e
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 16
---
# How to: Embed Expressions in XML Literals (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

Vous pouvez combiner des littéraux XML avec des expressions incorporées pour créer un document, un fragment ou un élément XML, qui contient le contenu créé au moment de l'exécution.  Les exemples suivants montrent comment utiliser des expressions incorporées pour remplir le contenu, les attributs et les noms de l'élément au moment de l'exécution.  
  
 La syntaxe pour une expression incorporée est `<%=` `exp` `%>`, identique à la syntaxe utilisée par [!INCLUDE[vstecasp](../../../../csharp/language-reference/preprocessor-directives/includes/vstecasp-md.md)]. Pour plus d'informations, consultez [Embedded Expressions in XML](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).  
  
 Vous pouvez également utiliser les API [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq-md.md)] pour créer des objets [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq-md.md)].  Pour plus d'informations, consultez <xref:System.Xml.Linq.XElement>.  
  
## Procédures  
  
#### Pour insérer du texte comme élément contenu  
  
-   L'exemple suivant indique comment insérer le texte contenu dans la variable `contactName` entre l'ouverture et la fermeture des éléments de nom.  
  
     [!code-vb[VbXMLSamples#39](../../../../visual-basic/language-reference/operators/codesnippet/visualbasic/how-to-embed-expressions_1.vb)]  
  
     Cet exemple produit la sortie suivante :  
  
    ```  
    <contact>  
      <name>Patrick Hines</name>  
    </contact>  
    ```  
  
#### Pour insérer le texte en tant que valeur d'attribut  
  
-   L'exemple suivant indique comment insérer le texte contenu dans la variable `phoneType` comme valeur de l'attribut `type`.  
  
     [!code-vb[VbXMLSamples#40](../../../../visual-basic/language-reference/operators/codesnippet/visualbasic/how-to-embed-expressions_2.vb)]  
  
     Cet exemple produit la sortie suivante :  
  
    ```  
    <contact>  
      <phone type="home">206-555-0144</phone>  
    </contact>  
    ```  
  
#### Pour insérer le texte pour un nom d'élément  
  
-   L'exemple suivant indique comment insérer le texte contenu dans la variable `elementName` comme nom d'un élément.  
  
     Lorsque vous créez des éléments à l'aide de cette technique, vous devez les fermer avec la balise \<\/\>.  
  
     [!code-vb[VbXMLSamples#41](../../../../visual-basic/language-reference/operators/codesnippet/visualbasic/how-to-embed-expressions_3.vb)]  
  
     Cet exemple produit la sortie suivante :  
  
    ```  
    <contact>  
      <name>Patrick Hines</name>  
    </contact>  
    ```  
  
## Voir aussi  
 [How to: Create XML Literals](../../../../visual-basic/programming-guide/language-features/xml/how-to-create-xml-literals.md)   
 [Embedded Expressions in XML](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)   
 [Creating XML in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)   
 [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)