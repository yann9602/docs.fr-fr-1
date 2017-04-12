---
title: "Comment : appeler une procédure surchargée (Visual Basic) | Documents Microsoft"
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
- Visual Basic code, procedures
- procedures, overloading
- procedures, calling
- procedures, multiple versions
- procedure calls, overloaded
ms.assetid: 3bb331fb-f6bc-406f-9ca0-9609b497014c
caps.latest.revision: 12
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
ms.openlocfilehash: 0da83aa63bf013d841f2a01a535726f3b03497a1
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-call-an-overloaded-procedure-visual-basic"></a>Comment : appeler une procédure surchargée (Visual Basic)
L’avantage de la surcharge d’une procédure est la flexibilité de l’appel. Le code appelant peut obtenir les informations que nécessaires pour passer à la procédure, puis appelez un seul nom de procédure, quel que soit les arguments qu’il passe.  
  
### <a name="to-call-a-procedure-that-has-more-than-one-version-defined"></a>Pour appeler une procédure qui possède plusieurs versions définies  
  
1.  Dans le code appelant, déterminez les données à passer à la procédure.  
  
2.  Écrire l’appel de procédure normalement, présenter les données dans la liste d’arguments. Assurez-vous que les arguments correspondent à la liste des paramètres dans l’une des versions de la procédure.  
  
3.  Vous n’avez pas à déterminer la version de la procédure à appeler. [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]transmet le contrôle à la version correspondant à votre liste d’arguments.  
  
     L’exemple suivant appelle la `post` procédure déclarée dans [Comment : définir plusieurs Versions d’une procédure](./how-to-define-multiple-versions-of-a-procedure.md). Il obtient l’identification de client, détermine s’il est un `String` ou `Integer`, puis dans les deux cas, appelle la même procédure.  
  
     [!code-vb[VbVbcnProcedures&#56;](./codesnippet/VisualBasic/how-to-call-an-overloaded-procedure_1.vb)]  
  
     [!code-vb[VbVbcnProcedures&#57;](./codesnippet/VisualBasic/how-to-call-an-overloaded-procedure_2.vb)]  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures](./index.md)   
 [Arguments et paramètres de procédure](./procedure-parameters-and-arguments.md)   
 [Surcharge de procédure](./procedure-overloading.md)   
 [Procédures de dépannage](./troubleshooting-procedures.md)   
 [Comment : définir plusieurs Versions d’une procédure](./how-to-define-multiple-versions-of-a-procedure.md)   
 [Comment : surcharger une procédure qui accepte des paramètres optionnels](./how-to-overload-a-procedure-that-takes-optional-parameters.md)   
 [Comment : surcharger une procédure qui accepte un nombre indéfini de paramètres](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)   
 [Considérations sur les surcharges de procédures](./considerations-in-overloading-procedures.md)   
 [Résolution de surcharge](./overload-resolution.md)   
 [Surcharges](../../../../visual-basic/language-reference/modifiers/overloads.md)
