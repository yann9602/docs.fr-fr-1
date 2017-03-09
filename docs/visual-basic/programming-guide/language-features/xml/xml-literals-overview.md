---
title: "XML Literals Overview (Visual Basic) | Microsoft Docs"
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
  - "XML literals [Visual Basic], about XML literals"
  - "declaring XML literals [Visual Basic]"
  - "LINQ to XML [Visual Basic], XML literals"
  - "literals [Visual Basic], XML"
ms.assetid: 37987c15-4ab8-471b-bd45-399816bfb57f
caps.latest.revision: 27
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 27
---
# XML Literals Overview (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

Un *littéral XML* vous permet d'incorporer directement du XML dans votre code [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)]. La syntaxe littérale XML, similaire à la syntaxe XML 1.0, représente des objets [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq-md.md)]. Cela facilite la création par programmation des éléments et des documents XML, car votre code possède la même structure que le XML final.  
  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)]compile des littéraux XML dans des objets [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq-md.md)].  [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq-md.md)] fournit un modèle objet simple pour la création et la manipulation du XML, et ce modèle s'intègre bien à [!INCLUDE[vbteclinqext](../../../../csharp/getting-started/includes/vbteclinqext-md.md)].  Pour plus d'informations, consultez <xref:System.Xml.Linq.XElement>.  
  
 Vous pouvez incorporer une expression [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] dans un littéral XML.  Au moment de l'exécution, votre application crée un objet [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq-md.md)] pour chaque littéral, en intégrant les valeurs des expressions incorporées.  Cela vous permet de spécifier du contenu dynamique dans un littéral XML.  Pour plus d'informations, consultez [Embedded Expressions in XML](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).  
  
 Pour plus d'informations sur les différences entre la syntaxe de littéral XML et la syntaxe XML 1.0, consultez [XML Literals and the XML 1.0 Specification](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification.md).  
  
## Littéraux simples  
 Vous pouvez créer un objet [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq-md.md)] dans votre code [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] en tapant ou collant du code XML valide.  Un littéral d'élément XML retourne un objet <xref:System.Xml.Linq.XElement>.  Pour plus d'informations, consultez [XML Element Literal](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md) et [XML Literals and the XML 1.0 Specification](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification.md).  L'exemple suivant crée un élément XML possédant plusieurs éléments enfants.  
  
 [!code-vb[VbXMLSamples#5](../../../../visual-basic/language-reference/operators/codesnippet/visualbasic/xml-literals-overview_1.vb)]  
  
 Vous pouvez créer un document XML en commençant un littéral XML par `<?xml version="1.0"?>`, comme indiqué dans l'exemple suivant.  Un littéral de document XML retourne un objet <xref:System.Xml.Linq.XDocument>.  Pour plus d'informations, consultez [XML Document Literal](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md).  
  
 [!code-vb[VbXMLSamples#6](../../../../visual-basic/language-reference/operators/codesnippet/visualbasic/xml-literals-overview_2.vb)]  
  
> [!NOTE]
>  La syntaxe de littéral XML de [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] n'est pas identique à la syntaxe de la spécification XML 1.0.  Pour plus d'informations, consultez [XML Literals and the XML 1.0 Specification](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification.md).  
  
## Continuation de ligne  
 Un littéral XML peut couvrir plusieurs lignes sans utiliser des caractères de continuation de ligne \(la séquence espace\-trait de soulignement\-entrée\).  Cela facilite la comparaison des littéraux XML du code avec les documents XML.  
  
 Le compilateur traite les caractères de continuation de ligne en tant que partie d'un littéral XML.  Par conséquent, vous devez utiliser la séquence espace\-trait de soulignement\-entrée uniquement lorsqu'elle appartient à l'objet [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq-md.md)].  
  
 Toutefois, vous avez besoin de caractères de continuation de ligne si vous avez une expression multiligne dans une expression incorporée.  Pour plus d'informations, consultez [Embedded Expressions in XML](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).  
  
## Incorporation de requêtes dans les littéraux XML  
 Vous pouvez utiliser une requête dans une expression incorporée.  Dans ce cas, les éléments retournés par la requête sont ajoutés à l'élément XML.  Cela vous permet d'ajouter du contenu dynamique, tel que le résultat de la requête d'un utilisateur, à un littéral XML.  
  
 Par exemple, le code suivant utilise une requête incorporée pour créer des éléments XML à partir des membres du tableau `phoneNumbers2`, puis ajoute ces éléments comme enfants de `contact2`.  
  
 [!code-vb[VbXMLSamples#7](../../../../visual-basic/language-reference/operators/codesnippet/visualbasic/xml-literals-overview_3.vb)]  
  
## Comment le compilateur crée des objets à partir des littéraux XML  
 Le compilateur [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] traduit des littéraux XML en appels aux constructeurs [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq-md.md)] équivalents pour développer l'objet [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq-md.md)].  Par exemple, le compilateur [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] traduira l'exemple de code suivant en appel au constructeur <xref:System.Xml.Linq.XProcessingInstruction> pour l'instruction de version XML, en appels au constructeur <xref:System.Xml.Linq.XElement> pour les éléments `<contact>`, `<name>`et `<phone>` et en appels au constructeur <xref:System.Xml.Linq.XAttribute> pour l'attribut `type`.  Plus précisément, étant donné les attributs dans l'exemple suivant, le compilateur [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] appellera deux fois le constructeur <xref:System.Xml.Linq.XAttribute.%23ctor%28System.Xml.Linq.XName%2CSystem.Object%29>.  Les premiers passeront la valeur `type` pour le paramètre `name` et la valeur `home` pour le paramètre `value`.  Le deuxième passera également la valeur `type` pour le paramètre `name`, mais la valeur `work` pour le paramètre `value`.  
  
 [!code-vb[VbXMLSamples#6](../../../../visual-basic/language-reference/operators/codesnippet/visualbasic/xml-literals-overview_2.vb)]  
  
## Voir aussi  
 <xref:System.Xml.Linq.XElement>   
 [Creating XML in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)   
 [Embedded Expressions in XML](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)   
 [XML Document Literal](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)   
 [XML Element Literal](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)   
 [XML Literals](../../../../visual-basic/language-reference/xml-literals/index.md)