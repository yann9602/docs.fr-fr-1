---
title: "Vue d'ensemble des littéraux XML (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XML literals [Visual Basic], about XML literals
- declaring XML literals [Visual Basic]
- LINQ to XML [Visual Basic], XML literals
- literals [Visual Basic], XML
ms.assetid: 37987c15-4ab8-471b-bd45-399816bfb57f
caps.latest.revision: "27"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 59ce79995025692428263120f9c21c7baf5cf231
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="xml-literals-overview-visual-basic"></a>Vue d'ensemble des littéraux XML (Visual Basic)
Un *littéral XML* vous permet d’incorporer directement du XML dans votre [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] code. La syntaxe de littéral XML représente [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objets et il est similaire à la syntaxe XML 1.0. Cela rend plus facile de créer par programme des documents et des éléments XML, car votre code possède la même structure que le XML final.  
  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]Compile des littéraux XML en [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objets. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]fournit un modèle objet simple pour la création et la manipulation de données XML et ce modèle s’intègre parfaitement aux [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]. Pour plus d'informations, consultez <xref:System.Xml.Linq.XElement>.  
  
 Vous pouvez incorporer un [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] expression dans un littéral XML. Au moment de l’exécution, votre application crée un [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objet pour chaque littéral, en intégrant les valeurs des expressions incorporées. Cela vous permet de spécifier le contenu dynamique dans un littéral XML. Pour plus d’informations, consultez [Expressions incorporées en XML](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).  
  
 Pour plus d’informations sur les différences entre la syntaxe de littéral XML et la syntaxe XML 1.0, consultez [les littéraux XML et la spécification de 1.0 XML](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification.md).  
  
## <a name="simple-literals"></a>Littéraux simples  
 Vous pouvez créer un [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] de l’objet dans votre [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] code en tapant ou en collant du code XML valide. Un littéral d’élément XML retourne un <xref:System.Xml.Linq.XElement> objet. Pour plus d’informations, consultez [XML élément Literal](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md) et [les littéraux XML et la spécification de 1.0 XML](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification.md). L’exemple suivant crée un élément XML qui comporte plusieurs éléments enfants.  
  
 [!code-vb[VbXMLSamples#5](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-literals-overview_1.vb)]  
  
 Vous pouvez créer un document XML en démarrant un littéral XML avec `<?xml version="1.0"?>`, comme illustré dans l’exemple suivant. Un littéral de document XML retourne un <xref:System.Xml.Linq.XDocument> objet. Pour plus d’informations, consultez [littéral de Document XML](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md).  
  
 [!code-vb[VbXMLSamples#6](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-literals-overview_2.vb)]  
  
> [!NOTE]
>  La syntaxe de littéral XML dans [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] n’est pas identique à la syntaxe de la spécification XML 1.0. Pour plus d’informations, consultez [les littéraux XML et la spécification de 1.0 XML](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification.md).  
  
## <a name="line-continuation"></a>Continuation de ligne  
 Un littéral XML peut couvrir plusieurs lignes sans utiliser de caractères de continuation de ligne (la séquence espace-trait de soulignement-entrée). Cela facilite la comparaison des littéraux XML dans le code avec des documents XML.  
  
 Le compilateur traite les caractères de continuation de ligne dans le cadre d’un littéral XML. Par conséquent, vous devez utiliser la séquence espace-trait de soulignement-entrée uniquement lorsqu’elle appartient à la [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objet.  
  
 Toutefois, les caractères de continuation de ligne est nécessaire si vous avez une expression multiligne dans une expression incorporée. Pour plus d’informations, consultez [Expressions incorporées en XML](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).  
  
## <a name="embedding-queries-in-xml-literals"></a>Incorporation de requêtes dans les littéraux XML  
 Vous pouvez utiliser une requête dans une expression incorporée. Dans ce cas, les éléments retournés par la requête sont ajoutés à l’élément XML. Cela vous permet d’ajouter du contenu dynamique, tel que le résultat de requête de l’utilisateur, à un littéral XML.  
  
 Par exemple, le code suivant utilise une requête incorporée pour créer des éléments XML à partir des membres de la `phoneNumbers2` de tableau, puis ajoutez ces éléments en tant qu’enfants de `contact2`.  
  
 [!code-vb[VbXMLSamples#7](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-literals-overview_3.vb)]  
  
## <a name="how-the-compiler-creates-objects-from-xml-literals"></a>Comment le compilateur crée des objets à partir des littéraux XML  
 Le [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compilateur traduit les littéraux XML en appels à l’équivalent [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] constructeurs pour créer le [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objet. Par exemple, le [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compilateur convertit le code suivant dans un appel à la <xref:System.Xml.Linq.XProcessingInstruction> appels de constructeur pour l’instruction de version XML, à la <xref:System.Xml.Linq.XElement> constructeur pour le `<contact>`, `<name>`et `<phone>`des éléments et les appels à la <xref:System.Xml.Linq.XAttribute> constructeur pour le `type` attribut. Plus précisément, étant donné les attributs dans l’exemple suivant, la [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compilateur appellera le <xref:System.Xml.Linq.XAttribute.%23ctor%28System.Xml.Linq.XName%2CSystem.Object%29> constructeur à deux reprises. La première passe la valeur `type` pour le `name` paramètre et la valeur `home` pour la `value` paramètre. La deuxième passe également la valeur `type` pour le `name` paramètre, mais la valeur `work` pour la `value` paramètre.  
  
 [!code-vb[VbXMLSamples#6](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-literals-overview_2.vb)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Xml.Linq.XElement>  
 [Création de code XML dans Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [Expressions incorporées en XML](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)  
 [Littéral de document XML](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)  
 [Littéral d’élément XML](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)  
 [Littéraux XML](../../../../visual-basic/language-reference/xml-literals/index.md)
