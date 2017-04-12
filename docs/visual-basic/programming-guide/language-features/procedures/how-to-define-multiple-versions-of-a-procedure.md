---
title: "Comment : définir plusieurs Versions d’une procédure (Visual Basic) | Documents Microsoft"
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
- procedures, defining
- Visual Basic code, procedures
- procedures, overloading
- procedures, multiple versions
- procedure overloading, multiple versions
ms.assetid: 71ccdd66-1b00-4b66-bee4-6926c0d696f4
caps.latest.revision: 14
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
ms.openlocfilehash: 0228083ce00a0f552227fd7ae8f0f5a24f65148e
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-define-multiple-versions-of-a-procedure-visual-basic"></a>Comment : définir plusieurs versions d'une procédure (Visual Basic)
Vous pouvez définir une procédure dans plusieurs versions en *surcharge* il, en utilisant le même nom mais une liste de paramètres différente pour chaque version. L’objectif de la surcharge consiste à définir plusieurs versions étroitement liées d’une procédure sans avoir à les différencier par nom.  
  
 Pour plus d’informations, consultez [surcharge de procédure](./procedure-overloading.md).  
  
### <a name="to-define-multiple-versions-of-a-procedure"></a>Pour définir plusieurs versions d’une procédure  
  
1.  Écrire un `Sub` ou `Function` instruction de déclaration pour chaque version de la procédure que vous souhaitez définir. Utilisez le même nom de procédure dans chaque déclaration.  
  
2.  Faites précéder le `Sub` ou `Function` (mot clé) dans chaque déclaration le [surcharges](../../../../visual-basic/language-reference/modifiers/overloads.md) (mot clé). Vous pouvez omettre `Overloads` dans les déclarations, mais si vous l’incluez dans une des déclarations, vous devez l’inclure dans toutes les déclarations.  
  
3.  Après chaque instruction de déclaration, écrivez le code de procédure pour gérer le cas où le code appelant fournit les arguments qui correspondent à liste de paramètres de cette version. Vous n’avez pas à tester pour quels paramètres le code appelant a fourni. [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]passe le contrôle à la version correspondante de votre procédure.  
  
4.  Terminez chaque version de la procédure avec le `End Sub` ou `End Function` instruction comme il convient.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant définit un `Sub` procédure pour publier une transaction relative au solde d’un client. Il utilise le `Overloads` (mot clé) pour définir deux versions de la procédure, un qui accepte le client par nom et l’autre par numéro de compte.  
  
 [!code-vb[VbVbcnProcedures&#72;](./codesnippet/VisualBasic/how-to-define-multiple-versions-of-a-procedure_1.vb)]  
  
 Le code appelant peut obtenir l’identification du client selon un `String` ou `Integer`, puis utilisez la même instruction appelante dans les deux cas.  
  
 Pour plus d’informations sur l’appel de ces versions de la `post` procédure, consultez la page [Comment : appeler une procédure surchargée](./how-to-call-an-overloaded-procedure.md).  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Assurez-vous que chacun de vos versions surchargées a le même nom de procédure, mais une liste de paramètres différente.  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures](./index.md)   
 [Arguments et paramètres de procédure](./procedure-parameters-and-arguments.md)   
 [Procédures de dépannage](./troubleshooting-procedures.md)   
 [Comment : surcharger une procédure qui accepte des paramètres optionnels](./how-to-overload-a-procedure-that-takes-optional-parameters.md)   
 [Comment : surcharger une procédure qui accepte un nombre indéfini de paramètres](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)   
 [Considérations sur les surcharges de procédures](./considerations-in-overloading-procedures.md)   
 [Résolution de surcharge](./overload-resolution.md)
