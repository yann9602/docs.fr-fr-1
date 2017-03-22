---
title: "Procédures de dépannage (Visual Basic) | Documents Microsoft"
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
- troubleshooting Visual Basic, procedures
- procedures, troubleshooting
- Visual Basic code, procedures
- troubleshooting procedures
- procedures, about procedures
ms.assetid: 525721e8-2e02-4f75-b5d8-6b893462cf2b
caps.latest.revision: 17
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
ms.openlocfilehash: a5445d6da982e4eea5b1047505e4bee3380ed472
ms.lasthandoff: 03/13/2017

---
# <a name="troubleshooting-procedures-visual-basic"></a>Procédures de dépannage (Visual Basic)
Cette page répertorie quelques problèmes courants qui peuvent se produire lorsque vous travaillez avec des procédures.  
  
## <a name="returning-an-array-type-from-a-function-procedure"></a>Retourner un Type de tableau à partir d’une procédure (fonction)  
 Si un `Function` procédure retourne un type de données de tableau, vous ne pouvez pas utiliser le `Function` nom pour stocker des valeurs dans les éléments du tableau. Si vous tentez cette opération, le compilateur interprète comme un appel à la `Function`. L’exemple suivant génère des erreurs du compilateur.  
  
 `Function allOnes(ByVal n As Integer) As Integer()`  
  
 `For i As Integer = 1 To n - 1`  
  
 `' The following statement generates a`   `COMPILER ERROR`  `.`  
  
 `allOnes(i) = 1`  
  
 `Next i`  
  
 `' The following statement generates a`   `COMPILER ERROR`  `.`  
  
 `Return allOnes()`  
  
 `End Function`  
  
 L’instruction `allOnes(i) = 1` génère une erreur du compilateur parce qu’elle semble appeler `allOnes` avec un argument de type de données incorrect (un singleton `Integer` au lieu d’un `Integer` tableau). L’instruction `Return allOnes()` génère une erreur du compilateur parce qu’elle semble appeler `allOnes` sans aucun argument.  
  
 **Approche correcte :** pour être en mesure de modifier les éléments d’un tableau qui doit être retourné, définir un tableau interne en tant que variable locale. L’exemple suivant compile sans erreur.  
  
 [!code-vb[VbVbcnProcedures&#66;](./codesnippet/VisualBasic/troubleshooting-procedures_1.vb)]  
  
## <a name="argument-not-being-modified-by-procedure-call"></a>Argument non modifié par un appel de procédure  
 Si vous souhaitez autoriser une procédure modifier un élément de programmation sous-jacent d’un argument dans le code appelant, vous devez le passer par référence. Mais une procédure peut accéder aux éléments d’un argument de type référence même si vous le passez par valeur.  
  
-   **Sous-jacent Variable**. Pour permettre à la procédure de remplacer la valeur de l’élément variable sous-jacent lui-même, la procédure doit déclarer le paramètre [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md). En outre, le code appelant ne doit pas mettre l’argument entre parenthèses, parce qui remplace le `ByRef` mécanisme de transmission.  
  
-   **Référence des éléments de Type**. Si vous déclarez un paramètre [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md), la procédure ne peut pas modifier l’élément variable sous-jacent lui-même. Toutefois, si l’argument est un type référence, la procédure peut modifier les membres de l’objet sur lequel il pointe, même si elle ne peut pas remplacer la valeur de la variable. Par exemple, si l’argument est une variable tableau, la procédure ne peut pas affecter un nouveau tableau à elle, mais elle peut modifier un ou plusieurs de ses éléments. Les éléments modifiés sont réfléchis dans la variable tableau sous-jacente dans le code appelant.  
  
 L’exemple suivant définit deux procédures qui acceptent une variable tableau par valeur et opèrent sur ses éléments. Procédure `increase` ajoute simplement la valeur&1; à chaque élément. Procédure `replace` assigne un nouveau tableau au paramètre `a()` , puis l’ajoute à chaque élément. Cependant, la réassignation n’affecte pas la variable tableau sous-jacente dans le code appelant, car `a()` est déclarée `ByVal`.  
  
 [!code-vb[VbVbcnProcedures&#35;](./codesnippet/VisualBasic/troubleshooting-procedures_2.vb)]  
  
 [!code-vb[VbVbcnProcedures&#38;](./codesnippet/VisualBasic/troubleshooting-procedures_3.vb)]  
  
 L’exemple suivant effectue des appels à `increase` et `replace`.  
  
 [!code-vb[VbVbcnProcedures&#37;](./codesnippet/VisualBasic/troubleshooting-procedures_4.vb)]  
  
 Le premier `MsgBox` appel affiche « après Increase (n) : 11, 21, 31, 41 ». Étant donné que `n` est un type référence, `increase` peut modifier ses membres, même s’il est passé `ByVal`.  
  
 La seconde `MsgBox` appel affiche « après Replace (n) : 11, 21, 31, 41 ». Étant donné que `n` est passée `ByVal`, `replace` ne peut pas modifier la variable `n` en lui assignant un nouveau tableau. Lors de la `replace` crée la nouvelle instance de tableau `k` et l’assigne à la variable locale `a`, il perd la référence à `n` passée par le code appelant. Lorsqu’il incrémente les membres de `a`, seul le tableau local `k` est affecté.  
  
 **Approche correcte :** pour être en mesure de modifier un élément de variable sous-jacent lui-même, passer par référence. L’exemple suivant montre la modification dans la déclaration de `replace` qui lui permet de remplacer un tableau par un autre dans le code appelant.  
  
 [!code-vb[VbVbcnProcedures&#64;](./codesnippet/VisualBasic/troubleshooting-procedures_5.vb)]  
  
## <a name="unable-to-define-an-overload"></a>Impossible de définir une surcharge  
 Si vous souhaitez définir une version surchargée d’une procédure, vous devez utiliser le même nom mais une signature différente. Si le compilateur ne peut pas différencier votre déclaration d’une surcharge avec la même signature, il génère une erreur.  
  
 Le *signature* d’une procédure est déterminée par le nom de la procédure et la liste de paramètres. Chaque surcharge doit avoir le même nom que les autres surcharges, mais doit être différent de tous les dans au moins un des autres composants de la signature. Pour plus d’informations, consultez [surcharge de procédure](./procedure-overloading.md).  
  
 Les éléments suivants, même si elles se rapportent à la liste de paramètres, ne sont pas des composants de la signature d’une procédure :  
  
-   Mots clés de modificateur de procédure, tel que `Public`, `Shared`, et`Static`  
  
-   Noms de paramètres  
  
-   Mots clés de modificateur de paramètre, tel que `ByRef` et`Optional`  
  
-   Le type de données de la valeur de retour (à l’exception d’un opérateur de conversion)  
  
 Vous ne pouvez pas surcharger une procédure en faisant varier uniquement un ou plusieurs des éléments précédents.  
  
 **Approche correcte :** pour pouvoir définir une surcharge de procédure, vous devez varier la signature. Étant donné que vous devez utiliser le même nom, vous devez varier le nombre, l’ordre ou les types de données des paramètres. Dans une procédure générique, vous pouvez varier le nombre de paramètres de type. Un opérateur de conversion ([CType, fonction](../../../../visual-basic/language-reference/functions/ctype-function.md)), vous pouvez modifier le type de retour.  
  
### <a name="overload-resolution-with-optional-and-paramarray-arguments"></a>Surcharge de résolution en option et les Arguments ParamArray  
 Si vous surchargez une procédure avec un ou plusieurs [facultatif](../../../../visual-basic/language-reference/modifiers/optional.md) paramètres ou un [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) paramètre, vous devez éviter de dupliquer de la *surcharges implicites*. Pour plus d’informations, consultez [considérations dans les procédures](./considerations-in-overloading-procedures.md).  
  
## <a name="calling-a-wrong-version-of-an-overloaded-procedure"></a>Appel d’une Version incorrecte d’une procédure surchargée  
 Si une procédure dispose de plusieurs versions surchargées, vous devez être familiarisé avec toutes leurs listes de paramètres et comprendre comment [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] résout les appels parmi les surcharges. Dans le cas contraire, vous pouvez appeler une surcharge différent de celui prévu.  
  
 Lorsque vous avez identifié la surcharge à appeler, veillez à respecter les règles suivantes :  
  
-   Fournissez le nombre correct d’arguments et dans l’ordre correct.  
  
-   Dans l’idéal, vos arguments doivent avoir les mêmes types de données exacts que les paramètres correspondants. Dans tous les cas, le type de données de chaque argument doit s’étendre à celui de son paramètre correspondant. Cela est vrai même avec la [Option Strict, instruction](../../../../visual-basic/language-reference/statements/option-strict-statement.md) la valeur `Off`. Si une surcharge requiert une conversion restrictive de votre liste d’arguments, cette surcharge n’est pas susceptible d’être appelée.  
  
-   Si vous fournissez des arguments qui requièrent l’extension, vérifiez les types de données aussi proche que possible pour les types de données de paramètre correspondant. Si deux ou plusieurs surcharges acceptent vos types de données d’argument, le compilateur résout votre appel à la surcharge qui demande le moins importante.  
  
 Vous pouvez réduire les risques d’incompatibilité de type de données à l’aide de la [CType, fonction](../../../../visual-basic/language-reference/functions/ctype-function.md) mot clé de conversion lors de la préparation de vos arguments.  
  
### <a name="overload-resolution-failure"></a>Échec de résolution de surcharge  
 Lorsque vous appelez une procédure surchargée, le compilateur tente de conserver une seule des surcharges. Si elle réussit, il résout l’appel à cette surcharge. S’il élimine toutes les surcharges, ou si elle ne peut pas réduire les surcharges admissibles à un seul candidat, il génère une erreur.  
  
 L’exemple suivant illustre le processus de résolution de surcharge.  
  
 [!code-vb[VbVbcnProcedures&#62;](./codesnippet/VisualBasic/troubleshooting-procedures_6.vb)]  
  
 [!code-vb[VbVbcnProcedures&#63;](./codesnippet/VisualBasic/troubleshooting-procedures_7.vb)]  
  
 Dans le premier appel, le compilateur élimine la première surcharge parce que le type du premier argument (`Short`) restreint au type du paramètre correspondant (`Byte`). Il élimine ensuite la troisième surcharge parce que chaque argument de type dans la deuxième surcharge (`Short` et `Single`) s’étend au type correspondant dans la troisième surcharge (`Integer` et `Single`). La deuxième surcharge requérant une extension moins importante, donc le compilateur utilise pour l’appel.  
  
 Dans le deuxième appel, le compilateur ne peut pas supprimer les surcharges en fonction restrictives. Il élimine la troisième surcharge pour la même raison que le premier appel, car il peut appeler la deuxième surcharge moyennant une extension moins importante des types d’arguments. Toutefois, le compilateur ne peut pas résoudre entre les premier et deuxième surcharges. Chacune possède un type de paramètre défini qui s’étend au type correspondant dans l’autre (`Byte` à `Short`, mais `Single` à `Double`). Par conséquent, le compilateur génère une erreur de résolution de surcharge.  
  
 **Approche correcte :** pour être en mesure d’appeler une procédure surchargée sans ambiguïté, utilisez [CType, fonction](../../../../visual-basic/language-reference/functions/ctype-function.md) pour faire correspondre les types de données d’argument pour les types de paramètres. L’exemple suivant montre un appel à `z` qui force la résolution sur la deuxième surcharge.  
  
 [!code-vb[VbVbcnProcedures&#65;](./codesnippet/VisualBasic/troubleshooting-procedures_8.vb)]  
  
### <a name="overload-resolution-with-optional-and-paramarray-arguments"></a>Surcharge de résolution en option et les Arguments ParamArray  
 Si deux surcharges d’une procédure ont des signatures identiques, mais que le dernier paramètre est déclaré [facultatif](../../../../visual-basic/language-reference/modifiers/optional.md) dans un et [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) dans l’autre, le compilateur résout un appel à cette procédure en fonction de la correspondance la plus proche. Pour plus d’informations, consultez [résolution de surcharge](./overload-resolution.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures](./index.md)   
 [Procédures Sub](./sub-procedures.md)   
 [Procédures Function](./function-procedures.md)   
 [Procédures de propriété](./property-procedures.md)   
 [Procédures d’opérateur](./operator-procedures.md)   
 [Arguments et paramètres de procédure](./procedure-parameters-and-arguments.md)   
 [Surcharge de procédure](./procedure-overloading.md)   
 [Considérations sur les surcharges de procédures](./considerations-in-overloading-procedures.md)   
 [Résolution de surcharge](./overload-resolution.md)
