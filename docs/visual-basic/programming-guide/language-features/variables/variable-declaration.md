---
title: "D&#233;claration de variable en Visual Basic | Microsoft Docs"
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
  - "variables [Visual Basic], déclarer"
  - "variables membres, déclarations"
  - "instruction Dim, déclaration de variable"
  - "déclarer des variables"
  - "variables [Visual Basic], étendue"
  - "variables [Visual Basic], types de données"
  - "types de données [Visual Basic], déclarations de variables"
  - "durée de vie, variables"
  - "variables [Visual Basic], durée de vie"
  - "niveaux d’accès, variables"
  - "étendue, instructions de déclaration"
  - "variables [Visual Basic], niveau d’accès"
  - "variables locales, déclarations"
  - "étendue, variables"
ms.assetid: d8f10226-92b1-480f-9f53-df377b2d7e15
caps.latest.revision: 31
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 31
---
# D&#233;claration de variable en Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

Vous devez déclarer une variable pour spécifier son nom et ses caractéristiques.  L'instruction de déclaration de variables est [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md).  Son emplacement et son contenu déterminent les caractéristiques de la variable.  
  
 Pour plus d'informations sur les règles et les considérations relatives à l'affectation de noms de variables, consultez [Declared Element Names](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
## Niveaux de déclaration  
  
### Variables locales et membres  
 Une *variable locale* est une variable déclarée dans une procédure.  Une *variable membre* est un membre de type [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)]. Elle est déclarée au niveau module, à l'intérieur d'une classe, d'une structure ou d'un module, mais pas dans une procédure interne à cette classe, structure ou module.  
  
### Variables d'instance et variables partagées  
 Dans une classe ou une structure, la catégorie d'une variable membre dépend du fait qu'elle est partagée ou non.  Si elle est déclarée à l'aide du mot clé [Shared](../../../../visual-basic/language-reference/modifiers/shared.md), il s'agit d'une *variable partagée* dont il n'existe qu'une seule copie partagée entre toutes les instances de la classe ou de la structure.  
  
 Sinon, il s'agit d'une *variable d'instance* dont la copie séparée est créée pour chaque instance de la classe ou de la structure.  Une copie donnée d'une variable d'instance est uniquement disponible à l'instance de la classe ou la structure dans laquelle elle a été créée.  C'est indépendante d'une copie de la variable d'instance dans une autre instance de la classe ou de la structure.  
  
## Déclaration du type de données  
 La clause [As](../../../../visual-basic/language-reference/statements/as-clause.md) dans l'instruction de déclaration vous permet de définir le type de données ou le type d'objet de la variable déclarée.  Vous pouvez spécifier l'un des types suivants pour une variable :  
  
-   Type de données élémentaire, tel que `Boolean`, `Long` ou `Decimal`  
  
-   Type de données composite, tel qu'un tableau ou une structure  
  
-   Type d'objet, ou classe, défini dans votre application ou dans une autre application  
  
-   Classe [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort-md.md)], comme <xref:System.Windows.Forms.Label> ou <xref:System.Windows.Forms.TextBox>  
  
-   Type d'interface, tel que <xref:System.IComparable> ou <xref:System.IDisposable>  
  
 Vous pouvez déclarer plusieurs variables dans une instruction sans devoir répéter le type de données.  Dans les instructions suivantes, les variables `i`, `j` et `k` sont déclarées comme type `Integer`, `l` et `m` comme `Long` et `x` et `y` comme `Single` :  
  
```  
Dim i, j, k As Integer  
' All three variables in the preceding statement are declared as Integer.  
Dim l, m As Long, x, y As Single  
' In the preceding statement, l and m are Long, x and y are Single.  
```  
  
 Pour plus d'informations sur les types de données, consultez [Types de données](../../../../visual-basic/programming-guide/language-features/data-types/index.md).  Pour plus d'informations sur les objets, consultez [Objects and Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md) et [Programming with Components](../Topic/Programming%20with%20Components.md).  
  
## Inférence de type local  
 L'*inférence de type* permet de déterminer les types de données des variables locales déclarées sans clause `As`.  Le compilateur déduit le type de variable à partir du type d'expression d'initialisation.  Ceci vous permet de déclarer des variables sans déclarer de type de manière explicite.  Dans l'exemple suivant, `num1` et `num2` sont fortement typés comme entiers.  
  
 [!code-vb[VbVbalrTypeInference#1](../../../../visual-basic/language-reference/statements/codesnippet/visualbasic/variable-declaration_1.vb)]  
  
 Si vous souhaitez utiliser l'inférence de type locale, `Option Infer` doit avoir la valeur `On`.  Pour plus d'informations, consultez [Local Type Inference](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md) et [Option Infer Statement](../../../../visual-basic/language-reference/statements/option-infer-statement.md).  
  
## Caractéristiques des variables déclarées  
 La *durée de vie* d'une variable correspond à la durée pendant laquelle elle peut être utilisée.  En général, une variable existe tant que l'élément qui la déclare \(tel qu'une procédure ou une classe\) continue à exister.  Si la variable n'a pas besoin de continuer à exister au delà de la durée de vie de l'élément qui la contient, vous n'avez besoin de faire rien de spécial dans la déclaration.  Si la variable doit continuer d'exister plus longtemps que l'élément qui la contient, vous pouvez inclure les mots clés `Static` ou `Shared` dans son instruction `Dim`.  Pour plus d'informations, consultez [Lifetime in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md).  
  
 La *portée* d'une variable correspond à l'ensemble du code qui peut s'y référer sans qualifier son nom.  La portée d'une variable est déterminée par l'emplacement où elle est déclarée.  Le code situé dans une zone donnée peut utiliser les variables définies dans cette zone sans devoir qualifier leurs noms.  Pour plus d'informations, consultez [Scope in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md).  
  
 Le *niveau d'accès* d'une variable est l'étendue de code qui a l'autorisation d'y accéder.  Il est déterminé par le modificateur d'accès \(tel que [Public](../../../../visual-basic/language-reference/modifiers/public.md) ou [Private](../../../../visual-basic/language-reference/modifiers/private.md)\) que vous utilisez dans l'instruction `Dim`.  Pour plus d'informations, consultez [Access Levels in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
## Voir aussi  
 [How to: Create a New Variable](../../../../visual-basic/programming-guide/language-features/variables/how-to-create-a-new-variable.md)   
 [How to: Move Data Into and Out of a Variable](../../../../visual-basic/programming-guide/language-features/variables/how-to-move-data-into-and-out-of-a-variable.md)   
 [Data Types](../../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Protected](../../../../visual-basic/language-reference/modifiers/protected.md)   
 [Friend](../../../../visual-basic/language-reference/modifiers/friend.md)   
 [Static](../../../../visual-basic/language-reference/modifiers/static.md)   
 [Declared Element Characteristics](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)   
 [Local Type Inference](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)   
 [Option Infer Statement](../../../../visual-basic/language-reference/statements/option-infer-statement.md)