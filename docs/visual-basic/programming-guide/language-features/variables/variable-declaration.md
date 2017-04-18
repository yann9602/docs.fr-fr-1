---
title: "Déclaration de variable en Visual Basic | Documents Microsoft"
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
- variables [Visual Basic], declaring
- member variables, declarations
- Dim statement, variable declaration
- declaring variables
- variables [Visual Basic], scope
- variables [Visual Basic], data types
- data types [Visual Basic], variable declarations
- lifetime, variables
- variables [Visual Basic], lifetime
- access levels, variables
- scope, declaration statements
- variables [Visual Basic], access level
- local variables, declarations
- scope, variables
ms.assetid: d8f10226-92b1-480f-9f53-df377b2d7e15
caps.latest.revision: 31
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 8cabb2d319288653c80099c816e46e822429d6ec
ms.lasthandoff: 03/13/2017

---
# <a name="variable-declaration-in-visual-basic"></a>Déclaration de variable en Visual Basic
Vous déclarez une variable pour spécifier son nom et sa configuration. L’instruction de déclaration de variables est la [une instruction Dim](../../../../visual-basic/language-reference/statements/dim-statement.md). Son emplacement et son contenu déterminent les caractéristiques de la variable.  
  
 Pour les règles d’affectation de noms de variable et les considérations, consultez [noms d’éléments déclarés](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
## <a name="declaration-levels"></a>Niveaux de déclaration  
  
### <a name="local-and-member-variables"></a>Local et les Variables de membre  
 A *variable locale* est celle qui est déclarée dans une procédure. A *variable membre* est un membre d’un [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] type ; elle est déclarée au niveau du module, à l’intérieur d’une classe, une structure ou un module, mais pas dans une procédure interne à cette classe, une structure ou un module.  
  
### <a name="shared-and-instance-variables"></a>Instance et Variables partagées  
 Dans une classe ou structure, la catégorie d’une variable membre dépend d’elle est partagée ou non. Si elle est déclarée avec le [Shared](../../../../visual-basic/language-reference/modifiers/shared.md) (mot clé), il est un *variable partagée*, et il existe une seule copie partagée entre toutes les instances de la classe ou structure.  
  
 Sinon, il est un *variable d’instance*, et une copie séparée est créée pour chaque instance de la classe ou structure. Une copie d’une variable d’instance donnée est disponible uniquement à l’instance de la classe ou la structure dans laquelle elle a été créée. Elle est indépendante d’une copie de la variable d’instance dans une autre instance de la classe ou structure.  
  
## <a name="declaring-data-type"></a>Déclaration de Type de données  
 Le [comme](../../../../visual-basic/language-reference/statements/as-clause.md) clause dans l’instruction de déclaration vous permet de définir le type de données ou le type d’objet de la variable que vous déclarez. Vous pouvez spécifier les types suivants d’une variable :  
  
-   Type de données élémentaire, tel que `Boolean`, `Long`, ou`Decimal`  
  
-   Type de données composite, tel qu’un tableau ou une structure  
  
-   Type d’objet, ou classe, défini dans votre application ou dans une autre application  
  
-   A [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] classe, telle que <xref:System.Windows.Forms.Label>ou <xref:System.Windows.Forms.TextBox></xref:System.Windows.Forms.TextBox> </xref:System.Windows.Forms.Label>  
  
-   Type d’interface, tel que <xref:System.IComparable>ou <xref:System.IDisposable></xref:System.IDisposable> </xref:System.IComparable>  
  
 Vous pouvez déclarer plusieurs variables dans une instruction sans devoir répéter le type de données. Dans les instructions suivantes, les variables `i`, `j`, et `k` sont déclarées en tant que type `Integer`, `l` et `m` en tant que `Long`, et `x` et `y` comme `Single`:  
  
```  
Dim i, j, k As Integer  
' All three variables in the preceding statement are declared as Integer.  
Dim l, m As Long, x, y As Single  
' In the preceding statement, l and m are Long, x and y are Single.  
```  
  
 Pour plus d’informations sur les types de données, consultez la page [des Types de données](../../../../visual-basic/programming-guide/language-features/data-types/index.md). Pour plus d’informations sur les objets, consultez [objets et Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md) et [programmation avec des composants](http://msdn.microsoft.com/library/d4d4fcb4-e0b8-46b3-b679-7ee0026eb9e3).  
  
## <a name="local-type-inference"></a>Inférence de type local  
 *L’inférence de type* est utilisé pour déterminer les types de données des variables locales déclarées sans un `As` clause. Le compilateur déduit le type de la variable du type de l’expression d’initialisation. Cela vous permet de déclarer des variables sans déclarer explicitement un type. Dans l’exemple suivant, les deux `num1` et `num2` sont fortement typés comme entiers.  
  
 [!code-vb[VbVbalrTypeInference n °&1;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/variable-declaration_1.vb)]  
  
 Si vous souhaitez utiliser l’inférence de type local, `Option Infer` doit avoir la valeur `On`. Pour plus d’informations, consultez [l’inférence de Type Local](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md) et [Option Infer, instruction](../../../../visual-basic/language-reference/statements/option-infer-statement.md).  
  
## <a name="characteristics-of-declared-variables"></a>Caractéristiques des Variables déclarées  
 Le *durée de vie* d’une variable est la période pendant laquelle il est disponible pour utilisation. En règle générale, une variable existe tant que l’élément qui le déclare (par exemple, une procédure ou une classe) continue d’exister. Si la variable n’a pas besoin excède la durée de vie de son élément conteneur, il est inutile d’opération spécifique dans la déclaration. Si la variable doit continuer d’exister plus longtemps que son élément conteneur, vous pouvez inclure le `Static` ou `Shared` mot clé dans son `Dim` instruction. Pour plus d’informations, consultez [durée de vie dans Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md).  
  
 Le *étendue* d’une variable est l’ensemble du code que vous pouvez vous y référer sans qualifier son nom. La portée d’une variable est déterminée par l’endroit où elle est déclarée. Le code situé dans une région donnée peut utiliser les variables définies dans cette zone sans devoir qualifier leurs noms. Pour plus d’informations, consultez [portée dans Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md).  
  
 D’une variable *niveau d’accès* est l’étendue de code qui a l’autorisation d’y accéder. Cela est déterminé par le modificateur d’accès (tel que [Public](../../../../visual-basic/language-reference/modifiers/public.md) ou [privé](../../../../visual-basic/language-reference/modifiers/private.md)) que vous utilisez dans la `Dim` instruction. Pour plus d’informations, consultez [niveaux d’accès dans Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : créer une Variable](../../../../visual-basic/programming-guide/language-features/variables/how-to-create-a-new-variable.md)   
 [Comment : déplacer des données dans et hors d’une Variable](../../../../visual-basic/programming-guide/language-features/variables/how-to-move-data-into-and-out-of-a-variable.md)   
 [Types de données](../../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Protégé par](../../../../visual-basic/language-reference/modifiers/protected.md)   
 [Friend](../../../../visual-basic/language-reference/modifiers/friend.md)   
 [Statique](../../../../visual-basic/language-reference/modifiers/static.md)   
 [Caractéristiques d’éléments déclarés](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)   
 [Inférence de Type local](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)   
 [Option Infer (instruction)](../../../../visual-basic/language-reference/statements/option-infer-statement.md)
