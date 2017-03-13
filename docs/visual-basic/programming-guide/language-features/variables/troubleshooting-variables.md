---
title: "D&#233;pannage des variables en Visual Basic | Microsoft Docs"
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
  - "dépannage [Visual Basic] (variables)"
  - "variables [Visual Basic] (dépannage)"
ms.assetid: 928a2dc8-e565-4ae4-8ba3-80cc0cb50090
caps.latest.revision: 20
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 19
---
# D&#233;pannage des variables en Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

Cette page répertorie quelques problèmes courants qui peuvent se produire quand vous utilisez des variables en [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)].  
  
## Impossible d’accéder aux membres d’un objet  
 Si votre code tente d’accéder à une propriété ou à une méthode sur un objet, il existe deux résultats possibles en cas d’erreur :  
  
-   Le compilateur peut générer un message d’erreur si vous déclarez la variable objet comme étant d’un type spécifique et que vous faites ensuite référence à un membre non défini par ce type.  
  
-   Une exception <xref:System.MemberAccessException> runtime se produit quand l’objet assigné à une variable objet n’expose pas le membre auquel votre code essaie d’accéder. Dans le cas d’une variable de [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md), vous pouvez également recevoir cette exception si le membre n’est pas `Public`. Cela est dû au fait que la liaison tardive autorise l’accès uniquement aux membres `Public`.  
  
 Quand l’[Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md) affecte la valeur `On` à la vérification de type, une variable objet peut accéder uniquement aux méthodes et aux propriétés de la classe avec laquelle vous la déclarez. L'exemple suivant illustre ce comportement.  
  
 [!CODE [VbVbalrStatements#49](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrStatements#49)]  
  
 [!code-vb[VbVbalrVariables#2](../../../../visual-basic/programming-guide/language-features/variables/codesnippet/VisualBasic/troubleshooting-variables_1.vb)]  
  
 Dans cet exemple, `p` peut utiliser uniquement les membres de la <xref:System.Object> classe proprement dite, qui n’incluent pas la propriété `Left`. En revanche, `q` a été déclaré comme étant de type <xref:System.Windows.Forms.Label>. Il peut donc utiliser toutes les méthodes et propriétés de la classe <xref:System.Windows.Forms.Label> dans l’espace de noms <xref:System.Windows.Forms>.  
  
### Approche correcte  
 Pour pouvoir accéder à tous les membres d’un objet d’une classe particulière, déclarez la variable objet comme étant du type de cette classe dans la mesure du possible. Si c’est impossible, par exemple si vous ne connaissez pas le type de l’objet au moment de la compilation, vous devez affecter la valeur `Off` à `Option Strict` et déclarer la variable comme étant [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md). Cela permet d’affecter des objets de tout type à la variable, et vous devez prendre les mesures nécessaires pour vous assurer que l’objet actuellement affecté est d’un type acceptable. Vous pouvez utiliser [TypeOf Operator](../../../../visual-basic/language-reference/operators/typeof-operator.md) pour effectuer cette détermination.  
  
## D’autres composants ne peuvent pas accéder à votre variable  
 Les noms en [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)]*ne respectent pas la casse*. Si deux noms diffèrent uniquement par la casse, le compilateur les interprète comme étant identiques. Par exemple, il considère que `ABC` et `abc` font référence au même élément déclaré.  
  
 Toutefois, le Common Language Runtime \(CLR\) utilise la liaison *qui respecte la casse*. Ainsi, quand vous générez un assembly ou une DLL et que vous le mettez à disposition d’autres assemblys, la casse de vos noms est respectée. Par exemple, si vous définissez une classe avec un élément nommé `ABC` et que d’autres assemblys utilisent votre classe par le biais du Common Language Runtime, ils doivent faire référence à l’élément en tant que `ABC`. Si, par la suite, vous recompilez votre classe et que vous changez le nom de l’élément en `abc`, les autres assemblys qui utilisent votre classe ne peuvent plus accéder à cet élément. Ainsi, quand vous publiez une version mise à jour d’un assembly, vous ne devez pas modifier la casse des éléments publics.  
  
 Pour plus d'informations, consultez [Common Language Runtime](../Topic/Common%20Language%20Runtime%20\(CLR\).md).  
  
### Approche correcte  
 Pour permettre à d’autres composants d’accéder à vos variables, traitez leurs noms comme s’ils respectaient la casse. Quand vous testez votre classe ou module, vérifiez que les autres assemblys se lient aux variables prévues. Une fois que vous avez publié un composant, ne modifiez pas les noms de variables existants, notamment leur casse.  
  
## Variable incorrecte utilisée  
 Quand plusieurs variables portent le même nom, le compilateur [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] essaie de résoudre chaque référence à ce nom. Si les variables ont une portée différente, le compilateur résout une référence à la déclaration dont la portée est la plus petite. Si elles ont la même portée, la résolution échoue et le compilateur signale une erreur. Pour plus d'informations, consultez [References to Declared Elements](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
### Approche correcte  
 Évitez d’utiliser des variables ayant le même nom mais une portée différente. Si vous utilisez d’autres assemblys ou projets, évitez d’utiliser des noms définis dans ces composants externes. Si plusieurs variables ont le même nom, n’oubliez pas de qualifier chaque référence à celui\-ci. Pour plus d'informations, consultez [References to Declared Elements](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
## Voir aussi  
 [Variables](../../../../visual-basic/programming-guide/language-features/variables/index.md)   
 [Déclaration de variable](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)   
 [Object Variables](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)   
 [Object Variable Declaration](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)   
 [How to: Access Members of an Object](../../../../visual-basic/programming-guide/language-features/variables/how-to-access-members-of-an-object.md)   
 [Object Variable Values](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)   
 [How to: Determine What Type an Object Variable Refers To](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-what-type-an-object-variable-refers-to.md)   
 [References to Declared Elements](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)   
 [Declared Element Names](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)