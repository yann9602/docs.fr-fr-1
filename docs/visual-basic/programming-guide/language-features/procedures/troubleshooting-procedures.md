---
title: "Troubleshooting Procedures (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "troubleshooting Visual Basic, procedures"
  - "procedures, troubleshooting"
  - "Visual Basic code, procedures"
  - "troubleshooting procedures"
  - "procedures, about procedures"
ms.assetid: 525721e8-2e02-4f75-b5d8-6b893462cf2b
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Troubleshooting Procedures (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Cette page répertorie quelques problèmes courants qui peuvent se produire lors de l'utilisation des procédures.  
  
## Retour d'un type tableau à partir d'une procédure Function  
 Si une procédure `Function` retourne un type de données tableau, vous ne pouvez pas utiliser le nom `Function` pour stocker des valeurs dans les éléments du tableau.  Si vous essayez, le compilateur interprète cette tentative comme un appel à `Function`.  L'exemple suivant génère des erreurs du compilateur.  
  
 `Function allOnes(ByVal n As Integer) As Integer()`  
  
 `For i As Integer = 1 To n - 1`  
  
 `' The following statement generates a`   `COMPILER ERROR`  `.`  
  
 `allOnes(i) = 1`  
  
 `Next i`  
  
 `' The following statement generates a`   `COMPILER ERROR`  `.`  
  
 `Return allOnes()`  
  
 `End Function`  
  
 L'instruction `allOnes(i) = 1` génère une erreur du compilateur parce qu'elle semble appeler `allOnes` avec un argument de type de données incorrect \(un `Integer` singleton au lieu d'un tableau `Integer`\).  L'instruction `Return allOnes()` génère une erreur du compilateur parce qu'elle semble appeler `allOnes` sans aucun argument.  
  
 **Approche correcte :** pour pouvoir modifier les éléments d'un tableau qui doit être retourné, définissez un tableau interne comme variable locale.  L'exemple suivant se compile sans erreur.  
  
 [!code-vb[VbVbcnProcedures#66](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/troubleshooting-procedures_1.vb)]  
  
## Argument non modifié par un appel de procédure  
 Si vous envisagez de permettre à une procédure de modifier un élément de programmation sous\-jacent d'un argument dans le code appelant, vous devez le passer par référence.  Cependant, une procédure peut accéder aux éléments d'un argument de type référence même si vous le passez par valeur.  
  
-   **Variable sous\-jacente**.  Afin de permettre à la procédure de remplacer la valeur de l'élément variable sous\-jacent lui\-même, la procédure doit déclarer le paramètre [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md).  De plus, le code appelant ne doit pas mettre l'argument entre parenthèses, parce que cela substituerait le mécanisme de passage `ByRef`.  
  
-   **Éléments de type référence**.  Si vous déclarez un paramètre [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md), la procédure ne peut pas modifier l'élément variable sous\-jacent lui\-même.  Cependant, si l'argument est un type référence, la procédure peut modifier les membres de l'objet vers lequel elle pointe, même si elle ne peut pas remplacer la valeur de la variable.  Par exemple, si l'argument est une variable tableau, la procédure ne peut pas lui assigner un nouveau tableau, mais elle peut modifier un ou plusieurs de ses éléments.  Les éléments modifiés sont réfléchis dans la variable tableau sous\-jacente du code appelant.  
  
 L'exemple suivant permet de définir deux procédures qui acceptent une variable tableau par valeur et opèrent sur ses éléments.  La procédure `increase` ajoute simplement la valeur 1 à chaque élément.  La procédure `replace` assigne un nouveau tableau au paramètre `a()`, puis ajoute la valeur 1 à chaque élément.  Cependant, la réassignation n'affecte pas la variable tableau sous\-jacente dans le code appelant, car `a()` est déclaré `ByVal`.  
  
 [!code-vb[VbVbcnProcedures#35](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/troubleshooting-procedures_2.vb)]  
  
 [!code-vb[VbVbcnProcedures#38](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/troubleshooting-procedures_3.vb)]  
  
 L'exemple suivant permet d'appeler `increase` et `replace`.  
  
 [!code-vb[VbVbcnProcedures#37](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/troubleshooting-procedures_4.vb)]  
  
 Le premier appel `MsgBox` affiche "After increase\(n\): 11, 21, 31, 41".  Parce que `n` est un type référence, `increase` peut modifier ses membres, même s'il est passé `ByVal`.  
  
 Le second appel `MsgBox` affiche "After replace\(n\): 11, 21, 31, 41".  Étant donné que `n` est passé `ByVal`, `replace` ne peut pas modifier la variable `n` en lui assignant un nouveau tableau.  Lorsque `replace` crée la nouvelle instance de tableau `k` et l'assigne à la variable locale `a`, il perd la référence à `n` passée par le code appelant.  Lorsqu'il incrémente les membres de `a`, seul le tableau local `k` est affecté.  
  
 **Approche correcte :** pour pouvoir modifier un élément variable sous\-jacent lui\-même, passez\-le par référence.  L'exemple suivant illustre la modification dans la déclaration de `replace` qui lui permet de remplacer un tableau par un autre dans le code appelant.  
  
 [!code-vb[VbVbcnProcedures#64](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/troubleshooting-procedures_5.vb)]  
  
## Impossible de définir une surcharge  
 Si vous souhaitez définir une version surchargée d'une procédure, vous devez utiliser le même nom, mais une signature différente.  Si le compilateur ne peut pas différencier votre déclaration d'une surcharge assortie de la même signature, il génère une erreur.  
  
 La *signature* d'une procédure est déterminée par la liste de paramètres et le nom de la procédure.  Chaque surcharge doit avoir le même nom que toutes les autres surcharges, mais elle doit différer des autres au moins au niveau d'un des autres composants de la signature.  Pour plus d'informations, consultez [Procedure Overloading](../../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md).  
  
 Les éléments suivants, bien qu'ils soient relatifs à la liste des paramètres, ne sont pas des composants de la signature d'une procédure :  
  
-   Mots clés de modificateur de procédure, tels que `Public`, `Shared` et `Static`  
  
-   Noms des paramètres  
  
-   Mots clés de modificateur de paramètre, tels que `ByRef` et `Optional`  
  
-   Type de données de la valeur de retour \(à l'exception d'un opérateur de conversion\)  
  
 Vous ne pouvez pas surcharger une procédure en faisant varier uniquement un ou plusieurs des éléments précédents.  
  
 **Approche correcte :** pour pouvoir définir une surcharge de procédure, vous devez faire varier la signature.  Étant donné vous devez utiliser le même nom, vous devez faire varier le nombre, l'ordre ou les types de données des paramètres.  Dans une procédure générique, vous pouvez faire varier le nombre des paramètres de type.  Pour un opérateur de conversion \([CType, fonction](../../../../visual-basic/language-reference/functions/ctype-function.md)\), vous pouvez modifier le type de retour.  
  
### Résolution de surcharge avec des arguments Optional et ParamArray  
 Si vous surchargez une procédure avec un ou plusieurs paramètres [Optional](../../../../visual-basic/language-reference/modifiers/optional.md) ou un paramètre [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md), vous devez éviter de dupliquer une des *surcharges implicites*.  Pour plus d'informations, consultez [Considerations in Overloading Procedures](../../../../visual-basic/programming-guide/language-features/procedures/considerations-in-overloading-procedures.md).  
  
## Appel d'une version incorrecte d'une procédure surchargée  
 Si une procédure dispose de plusieurs versions surchargées, vous devez être familiarisé avec toutes leurs listes de paramètres et comprendre comment [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] résout les appels parmi les surcharges,  faute de quoi vous risquez d'appeler une surcharge qui n'est pas celle voulue.  
  
 Lorsque vous avez identifié la surcharge à appeler, veillez à observer les règles suivantes :  
  
-   Fournissez le nombre correct d'arguments dans le bon ordre.  
  
-   Dans l'idéal, vos arguments doivent disposer exactement des mêmes types de données que les paramètres correspondants.  Dans tous les cas, le type de données de chaque argument doit être étendu à celui de son paramètre correspondant.  Cette règle est valable même lorsque l'[Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md) a la valeur `Off`.  Si une surcharge requiert une conversion restrictive de votre liste d'arguments, cette surcharge ne peut pas être appelée.  
  
-   Si vous fournissez des arguments qui requièrent l'extension, rendez leurs types de données aussi proches que possible des types de données des paramètres correspondants.  Si plusieurs surcharges acceptent les types de données de vos arguments, le compilateur résout votre appel en fonction de la surcharge qui exige l'extension la moins importante.  
  
 Vous pouvez réduire le risque d'incompatibilité de type de données en utilisant le mot clé de conversion de la [CType, fonction](../../../../visual-basic/language-reference/functions/ctype-function.md) lors de la préparation de vos arguments.  
  
### Échec de la résolution de surcharge  
 Lorsque vous appelez une procédure surchargée, le compilateur tente de conserver une seule surcharge.  S'il y parvient, il résout l'appel à cette surcharge.  S'il élimine toutes les surcharges ou ne parvient pas à réduire les surcharges admissibles à un seul candidat, il génère une erreur.  
  
 L'exemple suivant illustre le processus de résolution de surcharge.  
  
 [!code-vb[VbVbcnProcedures#62](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/troubleshooting-procedures_6.vb)]  
  
 [!code-vb[VbVbcnProcedures#63](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/troubleshooting-procedures_7.vb)]  
  
 Dans le premier appel, le compilateur élimine la première surcharge parce que le type du premier argument \(`Short`\) est restreint au type du paramètre correspondant \(`Byte`\).  Il élimine ensuite la troisième surcharge parce que chaque type d'argument dans la deuxième surcharge \(`Short` et `Single`\) est étendu au type correspondant dans la troisième surcharge \(`Integer` et `Single`\).  La deuxième surcharge requérant une extension moins importante, le compilateur l'utilise pour l'appel.  
  
 Dans le deuxième appel, le compilateur ne peut éliminer aucune des surcharges sur la base de la restriction.  Il élimine la troisième surcharge pour la même raison que dans le premier appel, parce qu'il peut appeler la deuxième surcharge moyennant une extension moins importante des types des arguments.  Toutefois, le compilateur ne peut pas effectuer de résolution entre la première et la deuxième surcharges.  Chaque surcharge possède un type de paramètre défini qui s'étend au type correspondant de l'autre \(`Byte` vers `Short`, mais `Single` vers `Double`\).  Par conséquent, le compilateur génère une erreur de résolution de surcharge.  
  
 **Approche correcte :** pour pouvoir appeler une procédure surchargée sans ambiguïté, utilisez la [CType, fonction](../../../../visual-basic/language-reference/functions/ctype-function.md) pour faire correspondre les types de données des arguments aux types des paramètres.  L'exemple suivant illustre un appel à `z` qui force la résolution sur la deuxième surcharge.  
  
 [!code-vb[VbVbcnProcedures#65](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/troubleshooting-procedures_8.vb)]  
  
### Résolution de surcharge avec des arguments Optional et ParamArray  
 Si deux surcharges d'une procédure ont des signatures identiques, mais que le dernier paramètre est déclaré [Optional](../../../../visual-basic/language-reference/modifiers/optional.md) dans l'une et [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) dans l'autre, le compilateur résout un appel à cette procédure d'après la correspondance la plus proche.  Pour plus d'informations, consultez [Overload Resolution](../../../../visual-basic/programming-guide/language-features/procedures/overload-resolution.md).  
  
## Voir aussi  
 [Procedures](../../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Sub Procedures](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md)   
 [Function, procédures](../../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md)   
 [Procédures de propriété](../../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)   
 [Operator Procedures](../../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)   
 [Procedure Parameters and Arguments](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [Procedure Overloading](../../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)   
 [Considerations in Overloading Procedures](../../../../visual-basic/programming-guide/language-features/procedures/considerations-in-overloading-procedures.md)   
 [Overload Resolution](../../../../visual-basic/programming-guide/language-features/procedures/overload-resolution.md)