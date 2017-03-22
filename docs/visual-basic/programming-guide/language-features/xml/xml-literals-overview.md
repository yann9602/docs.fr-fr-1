---
title: "Vue d’ensemble des littéraux XML (Visual Basic) | Documents Microsoft"
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
- XML literals [Visual Basic], about XML literals
- declaring XML literals [Visual Basic]
- LINQ to XML [Visual Basic], XML literals
- literals [Visual Basic], XML
ms.assetid: 37987c15-4ab8-471b-bd45-399816bfb57f
caps.latest.revision: 27
author: stevehoag
ms.author: shoag
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
ms.openlocfilehash: 57d036910ba9e49385caca28de222a8a8e28ec56
ms.lasthandoff: 03/13/2017

---
# <a name="xml-literals-overview-visual-basic"></a>Vue d'ensemble des littéraux XML (Visual Basic)
Un *littéral XML* vous permet d’incorporer directement du XML dans votre [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] code. La syntaxe de littéral XML représente [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] objets, qui est similaire à la syntaxe XML 1.0. Cela rend plus facile de créer par programme des documents et éléments XML, car votre code possède la même structure que le XML final.  
  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]Compile les littéraux XML en [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] objets. [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]fournit un modèle objet simple pour la création et la manipulation du XML et ce modèle s’intègre bien avec [!INCLUDE[vbteclinqext](../../../../csharp/getting-started/includes/vbteclinqext_md.md)]. Pour plus d’informations, consultez <xref:System.Xml.Linq.XElement>.</xref:System.Xml.Linq.XElement>  
  
 Vous pouvez incorporer un [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] expression dans un littéral XML. Au moment de l’exécution, votre application crée un [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] objet pour chaque littéral, en intégrant les valeurs des expressions incorporées. Cela vous permet de spécifier un contenu dynamique dans un littéral XML. Pour plus d’informations, consultez [Expressions incorporées en XML](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).  
  
 Pour plus d’informations sur les différences entre la syntaxe de littéral XML et la syntaxe XML 1.0, consultez [des littéraux XML et la spécification XML 1.0 mais](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification.md).  
  
## <a name="simple-literals"></a>Littéraux simples  
 Vous pouvez créer un [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] de l’objet dans votre [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] code en tapant ou collant du code XML valide. Un littéral d’élément XML retourne un <xref:System.Xml.Linq.XElement>objet.</xref:System.Xml.Linq.XElement> Pour plus d’informations, consultez [XML Element Literal](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md) et [des littéraux XML et la spécification XML 1.0 mais](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification.md). L’exemple suivant crée un élément XML qui comporte plusieurs éléments enfants.  
  
 [!code-vb[VbXMLSamples n °&5;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-literals-overview_1.vb)]  
  
 Vous pouvez créer un document XML en commençant un littéral XML par `<?xml version="1.0"?>`, comme illustré dans l’exemple suivant. Un littéral de document XML retourne un <xref:System.Xml.Linq.XDocument>objet.</xref:System.Xml.Linq.XDocument> Pour plus d’informations, consultez [littéral de Document XML](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md).  
  
 [!code-vb[VbXMLSamples n °&6;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-literals-overview_2.vb)]  
  
> [!NOTE]
>  La syntaxe de littéral XML dans [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] n’est pas identique à la syntaxe de la spécification XML 1.0. Pour plus d’informations, consultez [des littéraux XML et la spécification XML 1.0 mais](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification.md).  
  
## <a name="line-continuation"></a>Continuation de ligne  
 Un littéral XML peut couvrir plusieurs lignes sans utiliser de caractères de continuation de ligne (la séquence espace-trait de soulignement-entrée). Cela facilite la comparaison des littéraux XML dans le code avec des documents XML.  
  
 Le compilateur traite les caractères de continuation de ligne dans le cadre d’un littéral XML. Par conséquent, vous devez utiliser la séquence espace-trait de soulignement-entrée uniquement lorsqu’elle appartient à le [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] objet.  
  
 En revanche, vous devez les caractères de continuation de ligne si vous avez une expression multiligne dans une expression incorporée. Pour plus d’informations, consultez [Expressions incorporées en XML](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).  
  
## <a name="embedding-queries-in-xml-literals"></a>Incorporation de requêtes dans les littéraux XML  
 Vous pouvez utiliser une requête dans une expression incorporée. Lorsque vous effectuez cette opération, les éléments retournés par la requête sont ajoutés à l’élément XML. Cela vous permet d’ajouter du contenu dynamique, tel que le résultat de la requête de l’utilisateur, à un littéral XML.  
  
 Par exemple, le code suivant utilise une requête incorporée pour créer des éléments XML à partir des membres de la `phoneNumbers2` de tableau, puis ajoutez ces éléments en tant qu’enfants de `contact2`.  
  
 [!code-vb[VbXMLSamples&#7;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-literals-overview_3.vb)]  
  
## <a name="how-the-compiler-creates-objects-from-xml-literals"></a>Comment le compilateur crée des objets à partir des littéraux XML  
 Le [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compilateur traduit les littéraux XML en appels à l’équivalent [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] constructeurs pour créer le [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] objet. Par exemple, le [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compilateur convertit le code suivant dans un appel à la <xref:System.Xml.Linq.XProcessingInstruction>constructeur pour l’instruction de version XML, les appels à la <xref:System.Xml.Linq.XElement>constructeur pour le `<contact>`, `<name>`, et `<phone>` des éléments et les appels à la <xref:System.Xml.Linq.XAttribute>constructeur pour le `type` attribut.</xref:System.Xml.Linq.XAttribute> </xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XProcessingInstruction> En particulier, étant donné les attributs dans l’exemple suivant, la [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compilateur appellera le <xref:System.Xml.Linq.XAttribute.%23ctor%28System.Xml.Linq.XName%2CSystem.Object%29>deux fois le constructeur.</xref:System.Xml.Linq.XAttribute.%23ctor%28System.Xml.Linq.XName%2CSystem.Object%29> La première passe la valeur `type` pour la `name` paramètre et la valeur `home` pour la `value` paramètre. La deuxième passe également la valeur `type` pour la `name` paramètre, mais la valeur `work` pour la `value` paramètre.  
  
 [!code-vb[VbXMLSamples n °&6;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-literals-overview_2.vb)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Xml.Linq.XElement>   
 [Création de code XML en Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)   
 [Expressions incorporées en XML](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)   
 [Littéral de Document XML](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)   
 [Littéral d’élément XML](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)   
 [Littéraux XML](../../../../visual-basic/language-reference/xml-literals/index.md)
