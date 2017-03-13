---
title: "How to: Pass Arguments to a Procedure (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "arguments [Visual Basic], passing to procedures"
  - "procedures, arguments"
  - "procedures, parameters"
  - "procedure arguments"
  - "Visual Basic code, procedures"
  - "procedure parameters"
  - "procedures, calling"
  - "argument passing, procedures"
ms.assetid: 08723588-3890-4ddc-8249-79e049e0f241
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 14
---
# How to: Pass Arguments to a Procedure (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

Lorsque vous appelez une procédure, vous devez faire suivre le nom de procédure d'une liste d'arguments entre parenthèses.  Vous devez fournir un argument qui correspond à chaque paramètre requis que la procédure définit et vous pouvez fournir facultativement des arguments aux paramètres `Optional`.  Si vous ne fournissez pas de paramètre `Optional` lors de l'appel, vous devez inclure une virgule pour marquer sa place dans la liste d'arguments si vous fournissez des arguments suivants.  
  
 Si vous voulez passer un argument d'un type de données différent de celui du paramètre correspondant, tel que `Byte` à `String`, vous pouvez affecter la valeur `Off` au commutateur de vérification de type \([Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)\).  Si `Option Strict` a la valeur `On`, vous devez utiliser des conversions étendues ou des mots clés de conversion explicite.  Pour plus d'informations, consultez [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) et [Type Conversion Functions](../../../../visual-basic/language-reference/functions/type-conversion-functions.md).  
  
 Pour plus d'informations, consultez [Procedure Parameters and Arguments](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md).  
  
### Pour passer un ou plusieurs arguments à une procédure  
  
1.  Dans l'instruction appelante, faites suivre le nom de procédure de parenthèses.  
  
2.  À l'intérieur des parenthèses, placez une liste d'arguments.  Incluez un argument pour chaque paramètre requis que la procédure définit et séparez les arguments avec des virgules.  
  
3.  Assurez\-vous que chaque argument est une expression valide qui correspond à un type de données convertible au type que la procédure définit pour le paramètre correspondant.  
  
4.  Si un paramètre est défini comme [Optional](../../../../visual-basic/language-reference/modifiers/optional.md), vous pouvez l'inclure dans la liste d'arguments ou l'omettre.  Si vous l'omettez, la procédure utilise la valeur par défaut définie pour ce paramètre.  
  
5.  Si vous omettez un argument pour un paramètre `Optional` et s'il y a un autre paramètre après lui dans la liste de paramètres, vous pouvez marquer la place de l'argument omis par une virgule supplémentaire dans la liste d'arguments.  
  
     L'exemple suivant appelle la fonction [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>.  
  
     [!code-vb[VbVbcnProcedures#34](./codesnippet/VisualBasic/how-to-pass-arguments-to-a-procedure_1.vb)]  
  
     L'exemple précédent fournit le premier argument requis qui représente la chaîne de message à afficher.  Omet un argument pour le deuxième paramètre facultatif qui spécifie les boutons à afficher sur le message.  Parce que l'appel ne fournit pas de valeur, `MsgBox` utilise la valeur par défaut, `MsgBoxStyle.OKOnly` qui affiche uniquement un bouton **OK**.  
  
     La deuxième virgule dans la liste d'arguments marque la place du deuxième argument omis et la dernière chaîne est passée au troisième paramètre facultatif de `MsgBox` qui représente le texte à afficher dans la barre de titre.  
  
## Voir aussi  
 [Sub Procedures](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md)   
 [Function, procédures](../../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md)   
 [Procédures de propriété](../../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)   
 [Operator Procedures](../../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)   
 [How to: Define a Parameter for a Procedure](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-parameter-for-a-procedure.md)   
 [Passing Arguments by Value and by Reference](../../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)   
 [Recursive Procedures](../../../../visual-basic/programming-guide/language-features/procedures/recursive-procedures.md)   
 [Procedure Overloading](../../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)   
 [Objects and Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)   
 [Programmation orientée objet dans Visual Basic](../Topic/Object-Oriented%20Programming%20\(C%23%20and%20Visual%20Basic\).md)