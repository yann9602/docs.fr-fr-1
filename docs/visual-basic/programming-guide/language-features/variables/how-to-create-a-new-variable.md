---
title: "Comment : créer une Variable (Visual Basic) | Documents Microsoft"
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
- Dim statement
- variables [Visual Basic], creating
ms.assetid: 35300be3-77b0-4bef-a156-034d3cdedde0
caps.latest.revision: 29
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 2856fe19ddc48a14385aaae7b1c331fcb96c0554
ms.contentlocale: fr-fr
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-create-a-new-variable-visual-basic"></a>Comment : créer une variable (Visual Basic)
Vous créez une variable avec un [une instruction Dim](../../../../visual-basic/language-reference/statements/dim-statement.md).  
  
### <a name="to-create-a-new-variable"></a>Pour créer une variable  
  
1.  Déclarez la variable dans une `Dim` instruction.  
  
    ```  
    Dim newCustomer  
    ```  
  
2.  Incluent des spécifications pour les caractéristiques de la variable, comme [privé](../../../../visual-basic/language-reference/modifiers/private.md), [statique](../../../../visual-basic/language-reference/modifiers/static.md), [ombres](../../../../visual-basic/language-reference/modifiers/shadows.md), ou [WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md). Pour plus d’informations, consultez [caractéristiques d’éléments déclarés](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md).  
  
    ```  
    Public Static newCustomer  
    ```  
  
     Vous n’avez pas besoin du `Dim` (mot clé) si vous utilisez d’autres mots clés dans la déclaration.  
  
3.  Suivez les spécifications de nom de la variable, qui doit respecter [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] règles et conventions. Pour plus d’informations, consultez [noms d’éléments déclarés](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
    ```  
    Public Static newCustomer  
    ```  
  
4.  Suivre le nom de la [comme](../../../../visual-basic/language-reference/statements/as-clause.md) clause pour spécifier le type de données de la variable.  
  
    ```  
    Public Static newCustomer As Customer  
    ```  
  
     Si vous ne spécifiez pas le type de données, il utilise la valeur par défaut : `Object`.  
  
5.  Suivez les `As` clause par un signe égal (`=`) et suivez le signe égal de la valeur initiale de la variable.  
  
     [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]assigne la valeur spécifiée à la variable chaque fois qu’il exécute la `Dim` instruction. Si vous ne spécifiez pas de valeur initiale, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] assigne la valeur initiale par défaut pour le type de données de la variable lorsqu’il pénètre dans le code qui contient la `Dim` instruction.  
  
     Si la variable est un type référence, vous pouvez créer une instance de sa classe en incluant le [nouveau opérateur](../../../../visual-basic/language-reference/operators/new-operator.md) mot clé dans le `As` clause. Si vous n’utilisez pas `New`, la valeur initiale de la variable est [rien](../../../../visual-basic/language-reference/nothing.md).  
  
    ```  
    Public Static newCustomer As New Customer  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Variables](../../../../visual-basic/programming-guide/language-features/variables/index.md)   
 [Déclaration de variable](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)   
 [Noms d’éléments déclarés](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)   
 [Caractéristiques d’éléments déclarés](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)   
 [Types valeur et Types référence](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)   
 [Instructions](../../../../visual-basic/language-reference/statements/index.md)   
 [Inférence de Type local](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)   
 [Option Infer (instruction)](../../../../visual-basic/language-reference/statements/option-infer-statement.md)

