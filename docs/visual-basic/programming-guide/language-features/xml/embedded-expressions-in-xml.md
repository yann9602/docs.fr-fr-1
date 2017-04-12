---
title: "Les Expressions incorporées en XML (Visual Basic) | Documents Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vb.XmlEmbeddedExpression
dev_langs:
- VB
helpviewer_keywords:
- embedded expressions [Visual Basic]
- LINQ to XML [Visual Basic], embedded expressions
- XML literals [Visual Basic], embedded expressions
ms.assetid: bf2eb779-b751-4b7c-854f-9f2161482352
caps.latest.revision: 22
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
ms.openlocfilehash: e5cd40e55ec23de3ad1bb2f5f065762c893d9cb3
ms.lasthandoff: 03/13/2017

---
# <a name="embedded-expressions-in-xml-visual-basic"></a>Expressions incorporées en XML (Visual Basic)
Expressions incorporées permettent de créer des littéraux XML qui contiennent des expressions évaluées au moment de l’exécution. La syntaxe pour une expression incorporée est `<%=` `expression` `%>`, qui est la même que la syntaxe utilisée dans [!INCLUDE[vstecasp](../../../../csharp/language-reference/preprocessor-directives/includes/vstecasp_md.md)].  
  
 Par exemple, vous pouvez créer un élément XML littérale, combinant des expressions incorporées au contenu de texte littéral.  
  
 [!code-vb[27 VbXMLSamples](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_1.vb)]  
  
 Si `isbnNumber` contient l’entier 12345 et `modifiedDate` contient la date 3/5/2006, lorsque ce code s’exécute, la valeur de `book` est :  
  
```  
<book category="fiction" isbn="12345">  
  <modifiedDate>3/5/2006</modifiedDate>  
</book>  
```  
  
## <a name="embedded-expression-location-and-validation"></a>Validation et l’emplacement d’Expression incorporée  
 Expressions incorporées peuvent apparaître uniquement à certains emplacements dans des expressions littérales XML. Les contrôles d’emplacement expression les types de l’expression peuvent retourner et comment `Nothing` est gérée. Le tableau suivant décrit les emplacements autorisés et les types d’expressions incorporées.  
  
|Emplacement dans le littéral|Type d’expression|Gestion des`Nothing`|  
|---|---|---|  
|Nom d’élément XML|<xref:System.Xml.Linq.XName></xref:System.Xml.Linq.XName>|Erreur|  
|Contenu d’élément XML|`Object`ou un tableau de`Object`|Ignoré|  
|Nom d’attribut élément XML|<xref:System.Xml.Linq.XName></xref:System.Xml.Linq.XName>|Erreur, sauf si la valeur d’attribut est également`Nothing`|  
|Valeur d’attribut élément XML|`Object`|Déclaration attribute ignorée|  
|Attribut d’élément XML|<xref:System.Xml.Linq.XAttribute>ou une collection de<xref:System.Xml.Linq.XAttribute></xref:System.Xml.Linq.XAttribute></xref:System.Xml.Linq.XAttribute>|Ignoré|  
|Élément racine du document XML|<xref:System.Xml.Linq.XElement>ou une collection d’un <xref:System.Xml.Linq.XElement>objet et un nombre arbitraire <xref:System.Xml.Linq.XProcessingInstruction> <xref:System.Xml.Linq.XComment>d’objets</xref:System.Xml.Linq.XComment> et</xref:System.Xml.Linq.XProcessingInstruction> </xref:System.Xml.Linq.XElement></xref:System.Xml.Linq.XElement>|Ignoré|  
  
-   Exemple d’expression incorporée dans un nom d’élément XML :  
  
     [!code-vb[VbXMLSamples n°&32;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_2.vb)]  
  
-   Exemple d’expression incorporée dans le contenu d’un élément XML :  
  
     [!code-vb[VbXMLSamples&#33;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_3.vb)]  
  
-   Exemple d’expression incorporée dans un nom d’attribut XML élément :  
  
     [!code-vb[VbXMLSamples&#34;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_4.vb)]  
  
-   Exemple d’expression incorporée dans la valeur d’un attribut d’élément XML :  
  
     [!code-vb[VbXMLSamples&#35;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_5.vb)]  
  
-   Exemple d’expression incorporée dans un attribut d’élément XML :  
  
     [!code-vb[VbXMLSamples n °&36;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_6.vb)]  
  
-   Exemple d’expression incorporée dans un élément racine du document XML :  
  
     [!code-vb[VbXMLSamples&#37;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_7.vb)]  
  
 Si vous activez `Option Strict`, le compilateur vérifie que le type de chaque expression incorporée s’étend au type requis. La seule exception concerne l’élément racine d’un document XML, qui est vérifié lorsque le code s’exécute. Si vous compilez sans `Option Strict`, vous pouvez incorporer des expressions de type `Object` et leur type est vérifié au moment de l’exécution.  
  
 Dans les emplacements où le contenu est facultatif, les expressions incorporées qui contiennent `Nothing` sont ignorés. Cela signifie que vous n’avez pas à ce contenu d’élément, les valeurs d’attribut, et les éléments de tableau ne sont pas `Nothing` avant d’utiliser un littéral XML. Requis de valeurs, telles que les noms d’élément et d’attribut, ne peuvent pas être `Nothing`.  
  
 Pour plus d’informations sur l’utilisation d’une expression incorporée dans un type particulier de littéral, consultez [littéral de Document XML](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md), [XML Element Literal](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).  
  
## <a name="scoping-rules"></a>Règles de portée  
 Le compilateur convertit chaque littéral XML en un appel de constructeur pour le type de littéral approprié. Le contenu littéral et les expressions incorporées dans un littéral XML sont passées comme arguments au constructeur. Cela signifie que tous les [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] les éléments de programmation disponibles pour un littéral XML sont également disponibles pour ses expressions incorporées.  
  
 Dans un littéral XML, vous pouvez accéder à l’espace de noms XML préfixes déclarés avec la `Imports` instruction. Vous pouvez déclarer un nouveau préfixe d’espace de noms XML ou masquer un préfixe d’espace de noms XML existant dans un élément à l’aide de la `xmlns` attribut. Le nouvel espace de noms est disponible pour les nœuds enfants de cet élément, mais pas pour les littéraux XML des expressions incorporées.  
  
> [!NOTE]
>  Lorsque vous déclarez un préfixe d’espace de noms XML à l’aide de la `xmlns` attribut d’espace de noms, la valeur d’attribut doit être une chaîne constante. À cet égard, à l’aide de la `xmlns` attribut ressemble à l’aide de la `Imports` instruction pour déclarer un espace de noms XML. Vous ne pouvez pas utiliser une expression incorporée pour spécifier la valeur d’espace de noms XML.  
  
## <a name="see-also"></a>Voir aussi  
 [Création de code XML en Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)   
 [Littéral de Document XML](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)   
 [Littéral d’élément XML](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)   
 [Option Strict, instruction](../../../../visual-basic/language-reference/statements/option-strict-statement.md)   
 [Instruction Imports (espace de noms et type .NET)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)   
 [Vue d’ensemble des littéraux XML](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-overview.md)
