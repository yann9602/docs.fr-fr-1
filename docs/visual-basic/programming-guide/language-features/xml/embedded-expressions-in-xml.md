---
title: "Expressions incorporées en XML (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vb.XmlEmbeddedExpression
helpviewer_keywords:
- embedded expressions [Visual Basic]
- LINQ to XML [Visual Basic], embedded expressions
- XML literals [Visual Basic], embedded expressions
ms.assetid: bf2eb779-b751-4b7c-854f-9f2161482352
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b1cdba0a39a932f143ac98c2514240e1696a8fe0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="embedded-expressions-in-xml-visual-basic"></a>Expressions incorporées en XML (Visual Basic)
Expressions incorporées permettent de créer des littéraux XML qui contiennent des expressions qui sont évaluées au moment de l’exécution. La syntaxe pour une expression incorporée est `<%=` `expression` `%>`, qui est le même que la syntaxe utilisée dans [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)].  
  
 Par exemple, vous pouvez créer un élément XML littéral, combinant des expressions incorporées avec un contenu de texte littéral.  
  
 [!code-vb[VbXMLSamples#27](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_1.vb)]  
  
 Si `isbnNumber` contient l’entier 12345 et `modifiedDate` contient la date 3/5/2006, lorsque ce code s’exécute, la valeur de `book` est :  
  
```xml  
<book category="fiction" isbn="12345">  
  <modifiedDate>3/5/2006</modifiedDate>  
</book>  
```  
  
## <a name="embedded-expression-location-and-validation"></a>Validation et l’emplacement de l’Expression incorporée  
 Expressions incorporées peuvent apparaître uniquement à certains emplacements dans des expressions littérales XML. Les contrôles d’emplacement expression les types de l’expression peuvent retourner et comment `Nothing` est gérée. Le tableau suivant décrit les emplacements autorisés et les types d’expressions incorporées.  
  
|Emplacement dans le littéral|Type d’expression|Gestion des`Nothing`|  
|---|---|---|  
|Nom d’élément XML|<xref:System.Xml.Linq.XName>|Erreur|  
|Contenu de l’élément XML|`Object`ou un tableau de`Object`|Ignoré|  
|Nom d’attribut XML élément|<xref:System.Xml.Linq.XName>|Erreur, sauf si la valeur d’attribut est également`Nothing`|  
|Valeur d’attribut XML élément|`Object`|Déclaration d’attribut ignorée|  
|Attribut d’élément XML|<xref:System.Xml.Linq.XAttribute>ou une collection de<xref:System.Xml.Linq.XAttribute>|Ignoré|  
|Élément racine du document XML|<xref:System.Xml.Linq.XElement>ou une collection d’un <xref:System.Xml.Linq.XElement> objet et un nombre arbitraire de <xref:System.Xml.Linq.XProcessingInstruction> et <xref:System.Xml.Linq.XComment> objets|Ignoré|  
  
-   Exemple d’une expression incorporée dans un nom d’élément XML :  
  
     [!code-vb[VbXMLSamples#32](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_2.vb)]  
  
-   Exemple d’une expression incorporée dans le contenu d’un élément XML :  
  
     [!code-vb[VbXMLSamples#33](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_3.vb)]  
  
-   Exemple d’une expression incorporée dans un nom d’attribut XML élément :  
  
     [!code-vb[VbXMLSamples#34](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_4.vb)]  
  
-   Exemple d’une expression incorporée dans une valeur d’attribut XML élément :  
  
     [!code-vb[VbXMLSamples#35](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_5.vb)]  
  
-   Exemple d’une expression incorporée dans un attribut d’élément XML :  
  
     [!code-vb[VbXMLSamples#36](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_6.vb)]  
  
-   Exemple d’une expression incorporée dans un élément racine du document XML :  
  
     [!code-vb[VbXMLSamples#37](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_7.vb)]  
  
 Si vous activez `Option Strict`, le compilateur vérifie que le type de chaque expression incorporée s’étend au type requis. La seule exception concerne l’élément racine d’un document XML, qui est vérifié lorsque le code s’exécute. Si vous compilez sans `Option Strict`, vous pouvez incorporer des expressions de type `Object` et leur type est vérifié au moment de l’exécution.  
  
 Dans les emplacements où le contenu est facultatif, les expressions incorporées qui contiennent des `Nothing` sont ignorés. Cela signifie que vous n’avez pas à vérifier que le contenu élément, les valeurs d’attribut, et les éléments de tableau ne sont pas `Nothing` avant d’utiliser un littéral XML. Requis de valeurs, telles que les noms d’élément et d’attribut ne peut pas être `Nothing`.  
  
 Pour plus d’informations sur l’utilisation d’une expression incorporée dans un type particulier de littéral, consultez [littéral de Document XML](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md), [XML élément Literal](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).  
  
## <a name="scoping-rules"></a>Règles de portée  
 Le compilateur convertit chaque littéral XML en un appel de constructeur pour le type de littéral approprié. Le contenu littéral et les expressions incorporées dans un littéral XML sont passées comme arguments au constructeur. Cela signifie que tous les [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] les éléments de programmation disponibles pour un littéral XML sont également disponibles pour ses expressions incorporées.  
  
 Dans un littéral XML, vous pouvez accéder à l’espace de noms XML préfixes déclarés avec la `Imports` instruction. Vous pouvez déclarer un nouveau préfixe d’espace de noms XML ou masquer un préfixe d’espace de noms XML existant dans un élément à l’aide de la `xmlns` attribut. Le nouvel espace de noms est disponible pour les nœuds enfants de cet élément, mais pas pour les littéraux XML dans des expressions incorporées.  
  
> [!NOTE]
>  Lorsque vous déclarez un préfixe d’espace de noms XML à l’aide de la `xmlns` attribut d’espace de noms, la valeur d’attribut doit être une chaîne constante. À cet égard, à l’aide de la `xmlns` attribut est similaire à la `Imports` instruction pour déclarer un espace de noms XML. Vous ne pouvez pas utiliser une expression incorporée pour spécifier la valeur d’espace de noms XML.  
  
## <a name="see-also"></a>Voir aussi  
 [Création de code XML dans Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [Littéral de document XML](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)  
 [Littéral d’élément XML](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)  
 [Option Strict (instruction)](../../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [Imports (instruction) (espace de noms et type .NET)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)  
 [Vue d’ensemble des littéraux XML](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-overview.md)
