---
title: "Comment : passer des Arguments à une procédure (Visual Basic) | Documents Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- arguments [Visual Basic], passing to procedures
- procedures, arguments
- procedures, parameters
- procedure arguments
- Visual Basic code, procedures
- procedure parameters
- procedures, calling
- argument passing, procedures
ms.assetid: 08723588-3890-4ddc-8249-79e049e0f241
caps.latest.revision: 14
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
ms.openlocfilehash: ddccd476b2347368d0435f637edf3882db306f45
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-pass-arguments-to-a-procedure-visual-basic"></a>Comment : passer des arguments à une procédure (Visual Basic)
Lorsque vous appelez une procédure, vous suivez le nom de la procédure avec une liste d’arguments entre parenthèses. Vous fournissez un argument correspondant à chaque paramètre requis que la procédure définit et vous pouvez éventuellement fournir des arguments à le `Optional` paramètres. Si vous ne fournissez pas une `Optional` paramètre dans l’appel, vous devez inclure une virgule pour marquer sa place dans la liste d’arguments si vous fournissez des arguments suivants.  
  
 Si vous souhaitez passer un argument d’un type de données différent de celui de son paramètre correspondant, tel que `Byte` à `String`, vous pouvez définir le commutateur de vérification de type ([Option Strict, instruction](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) à `Off`. Si `Option Strict` est `On`, vous devez utiliser l’élargissement des conversions ou des mots clés de conversion explicite. Pour plus d’informations, consultez [Conversions étendues et restrictives](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) et [les fonctions de Conversion de Type](../../../../visual-basic/language-reference/functions/type-conversion-functions.md).  
  
 Pour plus d’informations, consultez [paramètres de procédure et les Arguments](./procedure-parameters-and-arguments.md).  
  
### <a name="to-pass-one-or-more-arguments-to-a-procedure"></a>Pour passer un ou plusieurs arguments à une procédure  
  
1.  Dans l’instruction appelante, suivre le nom de la procédure entre parenthèses.  
  
2.  À l’intérieur des parenthèses, placez une liste d’arguments. Inclure un argument pour chaque paramètre requis que la procédure définit et séparez les arguments par des virgules.  
  
3.  Assurez-vous que chaque argument est une expression valide qui correspond à un type de données convertible au type de la procédure définit pour le paramètre correspondant.  
  
4.  Si un paramètre est défini en tant que [facultatif](../../../../visual-basic/language-reference/modifiers/optional.md), vous pouvez inclure dans la liste d’arguments ou l’omettre. Si vous l’omettez, la procédure utilise la valeur par défaut définie pour ce paramètre.  
  
5.  Si vous omettez un argument pour un `Optional` paramètre et qu’un autre paramètre après lui dans la liste de paramètres, vous pouvez marquer la place de l’argument omis par une virgule supplémentaire dans la liste d’arguments.  
  
     L’exemple suivant appelle la [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>fonction.</xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>  
  
     [!code-vb[VbVbcnProcedures&#34;](./codesnippet/VisualBasic/how-to-pass-arguments-to-a-procedure_1.vb)]  
  
     L’exemple précédent fournit le premier argument requis, qui est la chaîne de message à afficher. Omet un argument pour le second paramètre facultatif qui spécifie les boutons à afficher dans la boîte de message. Étant donné que l’appel ne fournit pas de valeur, `MsgBox` utilise la valeur par défaut, `MsgBoxStyle.OKOnly`, qui affiche uniquement une **OK** bouton.  
  
     La deuxième virgule dans la liste d’arguments marque la place du deuxième argument omis et la dernière chaîne est passée au troisième paramètre facultatif de `MsgBox`, qui représente le texte à afficher dans la barre de titre.  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures Sub](./sub-procedures.md)   
 [Procédures Function](./function-procedures.md)   
 [Procédures de propriété](./property-procedures.md)   
 [Procédures d’opérateur](./operator-procedures.md)   
 [Comment : définir un paramètre pour une procédure](./how-to-define-a-parameter-for-a-procedure.md)   
 [Passage des Arguments par valeur et par référence](./passing-arguments-by-value-and-by-reference.md)   
 [Procédures récursives](./recursive-procedures.md)   
 [Surcharge de procédure](./procedure-overloading.md)   
 [Objets et Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)   
 [Programmation orientée objet](http://msdn.microsoft.com/library/1cf6e655-3f30-45f1-9a5d-4a88ca24a1c2)
