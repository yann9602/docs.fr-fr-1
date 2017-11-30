---
title: "Portée dans Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- module scope [Visual Basic]
- scope [Visual Basic], levels
- module level
- procedures [Visual Basic], scope
- declared elements [Visual Basic], scope
- namespaces [Visual Basic], scope
- scope [Visual Basic], declared elements
- scope [Visual Basic], about scope
- levels of scope [Visual Basic]
- block scope [Visual Basic]
- scope [Visual Basic], Visual Basic
- procedure scope [Visual Basic]
ms.assetid: 208106fe-79c9-4eec-93c6-55f08548895f
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a9bfda19b9f5ee96d45a0322541b35dfab7635d7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="scope-in-visual-basic"></a>Portée dans Visual Basic
Le *étendue* d’un élément déclaré est l’ensemble du code qui peut faire référence à ce dernier sans qualifier son nom ou le rendre disponible via une [Imports, instruction (.NET Namespace et Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md). Un élément peut avoir la portée à un des niveaux suivants :  
  
|Niveau|Description|  
|-----------|-----------------|  
|Portée de bloc|Disponible uniquement dans le code de bloc dans lequel elle est déclarée|  
|Portée de procédure|Disponible à tout le code dans la procédure dans laquelle elle est déclarée|  
|Portée de module|Disponible pour tout le code dans le module, classe ou structure dans laquelle elle est déclarée|  
|Namespace étendue|Disponible à tout le code dans l’espace de noms dans lequel elle est déclarée|  
  
 Ces niveaux de portée plus étroite (bloc) au plus large (espace de noms), où *plus petite portée* signifie que le plus petit ensemble de code qui peut faire référence à l’élément sans qualification. Pour plus d’informations, consultez « Niveaux de portée » dans cette page.  
  
## <a name="specifying-scope-and-defining-variables"></a>Spécifier la portée et la définition de Variables  
 Vous spécifiez l’étendue d’un élément lors de sa déclaration. L’étendue peut dépendre des facteurs suivants :  
  
-   La région dans laquelle vous déclarez l’élément (bloc, procédure, module, classe ou structure)  
  
-   L’espace de noms contenant la déclaration de l’élément  
  
-   Le niveau d’accès que vous déclarez pour l’élément  
  
 Soyez prudent lorsque vous définissez des variables avec le même nom mais une portée différente, car cela peut provoquer des résultats inattendus. Pour plus d'informations, consultez [References to Declared Elements](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
## <a name="levels-of-scope"></a>Niveaux de portée  
 Un élément de programmation est disponible dans l’ensemble de la région dans laquelle vous la déclarez. Tout le code dans la même région peut faire référence à l’élément sans qualifier son nom.  
  
### <a name="block-scope"></a>Portée de bloc  
 Un bloc est un ensemble d’instructions placées entre le début et de fin des instructions de déclaration, telles que les éléments suivants :  
  
-   `Do` et `Loop`  
  
-   `For`[`Each`] et`Next`  
  
-   `If` et `End If`  
  
-   `Select` et `End Select`  
  
-   `SyncLock` et `End SyncLock`  
  
-   `Try` et `End Try`  
  
-   `While` et `End While`  
  
-   `With` et `End With`  
  
 Si vous déclarez une variable dans un bloc, vous pouvez l’utiliser uniquement dans ce bloc. Dans l’exemple suivant, la portée de la variable entière `cube` est le bloc entre `If` et `End If`, et vous pouvez faire référence n’est plus à `cube` lorsque l’exécution passe hors du bloc.  
  
```  
If n < 1291 Then  
    Dim cube As Integer  
    cube = n ^ 3  
End If  
```  
  
> [!NOTE]
>  Même si l’étendue d’une variable est limitée à un bloc, sa durée de vie est toujours celui de l’ensemble de la procédure. Si vous entrez le bloc plusieurs fois au cours de la procédure, chaque variable de bloc conserve sa valeur précédente. Pour éviter des résultats inattendus dans ce cas, il est préférable d’initialiser des variables de bloc au début du bloc.  
  
### <a name="procedure-scope"></a>Portée de procédure  
 Un élément déclaré dans une procédure n’est pas disponible en dehors de celle-ci. Uniquement la procédure qui contient la déclaration peut l’utiliser. Variables à ce niveau sont également appelés *variables locales*. Vous les déclarez avec le [instruction Dim](../../../../visual-basic/language-reference/statements/dim-statement.md), avec ou sans le [statique](../../../../visual-basic/language-reference/modifiers/static.md) (mot clé).  
  
 Portée de bloc et de procédure sont étroitement liés. Si vous déclarez une variable à l’intérieur d’une procédure, mais en dehors de tout bloc de cette procédure, vous pouvez considérer la variable comme ayant une portée de bloc, le bloc représentant toute la procédure.  
  
> [!NOTE]
>  Tous les éléments locaux, même s’ils sont `Static` variables, appartiennent à la procédure dans laquelle ils apparaissent. Vous ne pouvez pas déclarer d’élément à l’aide de la [Public](../../../../visual-basic/language-reference/modifiers/public.md) mot clé contenu dans une procédure.  
  
### <a name="module-scope"></a>Portée de module  
 Pour plus de commodité, le terme unique *au niveau du module* s’applique aussi aux modules, les classes et structures. Vous pouvez déclarer des éléments à ce niveau en plaçant l’instruction de déclaration en dehors d’une procédure ou un bloc, mais dans le module, classe ou structure.  
  
 Lorsque vous faites une déclaration au niveau du module, le niveau d’accès que vous choisissez détermine la portée. L’espace de noms qui contient le module, classe ou structure affecte également la portée.  
  
 Les éléments que vous déclarez [privé](../../../../visual-basic/language-reference/modifiers/private.md) niveau d’accès sont disponibles pour toutes les procédures de ce module, mais pas pour le code dans un autre module. Le `Dim` instruction au niveau du module par défaut est `Private` si vous n’utilisez pas le mot clé de niveau d’accès. Toutefois, vous pouvez vous le niveau d’accès et de portée plus évidente à l’aide de la `Private` mot clé dans la `Dim` instruction.  
  
 Dans l’exemple suivant, toutes les procédures définies dans le module peuvent faire référence à la variable chaîne `strMsg`. Lorsque la deuxième procédure est appelée, elle affiche le contenu de la variable chaîne `strMsg` dans une boîte de dialogue.  
  
```  
' Put the following declaration at module level (not in any procedure).  
Private strMsg As String  
' Put the following Sub procedure in the same module.  
Sub initializePrivateVariable()  
    strMsg = "This variable cannot be used outside this module."  
End Sub  
' Put the following Sub procedure in the same module.  
Sub usePrivateVariable()  
    MsgBox(strMsg)  
End Sub  
```  
  
### <a name="namespace-scope"></a>Namespace étendue  
 Si vous déclarez un élément au niveau du module à l’aide du [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) ou [Public](../../../../visual-basic/language-reference/modifiers/public.md) (mot clé), il est accessible à toutes les procédures dans l’ensemble de l’espace de noms dans lequel l’élément est déclaré. Avec la modification suivante apportée à l’exemple précédent, la variable chaîne `strMsg` peuvent être référencés par le code n’importe où dans l’espace de noms de sa déclaration.  
  
```  
' Include this declaration at module level (not inside any procedure).  
Public strMsg As String  
```  
  
 Namespace étendue inclut des espaces de noms imbriqués. Un élément disponible dans un espace de noms est également accessible à partir de n’importe quel espace de noms imbriqué dans cet espace de noms.  
  
 Si votre projet ne contient pas de [Namespace instruction](../../../../visual-basic/language-reference/statements/namespace-statement.md), tous les éléments dans le projet se trouve dans le même espace de noms. Dans ce cas, la portée espace de noms peut être considérée comme la portée du projet. `Public`les éléments dans un module, une classe ou une structure sont également accessibles à tout projet qui fait référence à son projet.  
  
## <a name="choice-of-scope"></a>Choix de la portée  
 Lorsque vous déclarez une variable, vous devez conserver à l’esprit les points suivants lors du choix de sa portée.  
  
### <a name="advantages-of-local-variables"></a>Avantages des Variables locales  
 Variables locales sont un bon choix pour tout type de calcul temporaire, pour les raisons suivantes :  
  
-   **Prévention du conflit de nom.** Noms de variables locales ne sont pas susceptibles d’être en conflit. Par exemple, vous pouvez créer plusieurs procédures différentes qui contiennent une variable appelée `intTemp`. Tant que chaque `intTemp` est déclarée comme variable locale, chaque procédure ne reconnaît que sa propre version de `intTemp`. Toute procédure peut modifier la valeur de son local `intTemp` sans affecter `intTemp` variables dans d’autres procédures.  
  
-   **Consommation de mémoire.** Variables locales consomment la mémoire que lorsque leur procédure s’exécute. Leur mémoire est libérée lorsque la procédure retourne au code appelant. En revanche, [Shared](../../../../visual-basic/language-reference/modifiers/shared.md) et [statique](../../../../visual-basic/language-reference/modifiers/static.md) variables consomment des ressources mémoire tant que votre application est en cours d’exécution, donc les utiliser uniquement lorsque cela est nécessaire. *Variables d’instance* consomment de la mémoire alors que leur instance continue d’exister, qui les rend moins efficaces que les variables locales, mais potentiellement plus efficaces que `Shared` ou `Static` variables.  
  
### <a name="minimizing-scope"></a>Réduire la portée  
 En général, lorsque vous déclarez une variable ou une constante, il est conseillé de définir une portée aussi courtes que possible (la portée de bloc est la plus étroite). Cela permet d’économiser la mémoire et réduit les risques de votre code fasse référence à la variable incorrecte. De même, vous devez déclarer une variable qui doit être [statique](../../../../visual-basic/language-reference/modifiers/static.md) uniquement lorsqu’il est nécessaire de conserver sa valeur entre les appels de procédure.  
  
## <a name="see-also"></a>Voir aussi  
 [Caractéristiques d’éléments déclarés](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)  
 [Guide pratique : contrôler la portée d'une variable](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-control-the-scope-of-a-variable.md)  
 [Durée de vie dans Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)  
 [Niveaux d’accès dans Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
 [Références aux éléments déclarés](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 [Déclaration de variable](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
