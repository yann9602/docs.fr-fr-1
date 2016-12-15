---
title: "Scope in Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
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
  - "module scope"
  - "scope, levels"
  - "module level"
  - "procedures, scope"
  - "declared elements, scope"
  - "namespaces, scope"
  - "scope, declared elements"
  - "scope, about scope"
  - "levels of scope"
  - "block scope"
  - "scope, Visual Basic"
  - "procedure scope"
ms.assetid: 208106fe-79c9-4eec-93c6-55f08548895f
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Scope in Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

La *portée* d'un élément déclaré est l'ensemble du code qui peut faire référence à cet élément sans qualifier son nom ou le rendre disponible par le biais d'une [Imports Statement \(.NET Namespace and Type\)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).  Il existe différents niveaux de portée d'un élément :  
  
|Niveau|Description|  
|------------|-----------------|  
|Portée de bloc|Élément disponible uniquement dans le bloc de code dans lequel il est déclaré.|  
|Portée de procédure|Disponible pour tout le code dans la procédure dans laquelle il est déclaré|  
|Portée de module|Élément disponible pour tout le code au sein du module, de la classe ou de la structure dans laquelle il est déclaré.|  
|Portée d'espace de noms|Disponible pour tout le code dans l'espace de noms dans lequel il est déclaré|  
  
 Ces niveaux de portée vont du plus restreint \(bloc\) au plus large \(espace de noms\). La *plus petite portée* est le plus petit ensemble de code qui peut référencer l'élément sans le qualifier.  Pour plus d'informations, consultez « Niveaux de portée » dans cette page.  
  
## Spécifier la portée et définir des variables  
 Vous spécifiez la portée d'un élément lorsque vous le déclarez.  Les facteurs suivants sont susceptibles d'affecter la portée :  
  
-   La région \(bloc, procédure, module, classe ou structure\) dans laquelle vous déclarez l'élément ;  
  
-   L'espace de noms contenant la déclaration de l'élément ;  
  
-   Niveau d'accès que vous déclarez pour l'élément  
  
 Soyez très prudent lorsque vous définissez des variables avec le même nom, mais une portée différente ; vous pouvez être confronté à des résultats inattendus.  Pour plus d'informations, consultez [References to Declared Elements](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
## Niveaux de portée  
 Un élément de programmation est disponible dans toute la région dans laquelle vous le déclarez.  Tout le code d'une même région peut faire référence à l'élément sans qualifier son nom.  
  
### Portée de bloc  
 Un bloc est un jeu d'instructions délimité par des instructions de déclaration de début et de fin, telles que les éléments suivants :  
  
-   `Do` et `Loop`  
  
-   `For` \[`Each`\] et `Next`  
  
-   `If` et `End If`  
  
-   `Select` et `End Select`  
  
-   `SyncLock` et `End SyncLock`  
  
-   `Try` et `End Try`  
  
-   `While` et `End While`  
  
-   `With` et `End With`  
  
 Si vous déclarez une variable dans un bloc, vous pouvez l'utiliser uniquement dans ce bloc.  Dans l'exemple suivant, la portée de la variable de type entier `cube` est le bloc compris entre `If` et `End If`, et vous ne pouvez plus faire référence à `cube` lorsque l'exécution passe en dehors du bloc.  
  
```  
If n < 1291 Then  
    Dim cube As Integer  
    cube = n ^ 3  
End If  
```  
  
> [!NOTE]
>  Même si la portée d'une variable est limitée à un bloc, sa durée de vie correspond néanmoins à celle de toute la procédure.  Si vous entrez dans le bloc plusieurs fois au cours de la procédure, chaque variable de bloc conserve sa valeur précédente.  Dans un tel cas, vous pouvez éviter la présence de résultats inattendus en initialisant les variables de bloc au début de chaque bloc.  
  
### Portée de procédure  
 Un élément déclaré dans une procédure n'est pas disponible en dehors de celle\-ci.  Seule la procédure qui contient la déclaration peut l'utiliser.  Les variables à ce niveau sont également appelées des *variables locales*.  Vous les déclarez à l'aide de [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md), avec ou sans le mot clé [Static](../../../../visual-basic/language-reference/modifiers/static.md).  
  
 Les portées de bloc et de procédure sont étroitement liées.  Si vous déclarez une variable à l'intérieur d'une procédure, mais en dehors de tout bloc de cette procédure, la variable peut être considérée comme ayant une portée de bloc, le bloc représentant toute la procédure.  
  
> [!NOTE]
>  Tous les éléments locaux, même s'il s'agit de variables `Static`, sont privés dans la procédure dans laquelle ils apparaissent.  Vous ne pouvez pas déclarer d'élément à l'aide du mot clé [Public](../../../../visual-basic/language-reference/modifiers/public.md) dans une procédure.  
  
### Portée de module  
 Pour des raisons pratiques, le terme *niveau de module* est appliqué indifféremment aux modules, aux classes et aux structures.  Vous pouvez déclarer des éléments à ce niveau en plaçant l'instruction de déclaration à l'extérieur de toute procédure ou tout bloc figurant dans un module, une classe ou une structure.  
  
 Lorsque vous faites une déclaration au niveau du module, le niveau d'accès que vous choisissez détermine la portée.  L'espace de noms qui contient le module, la classe ou la structure affecte également la portée.  
  
 Les éléments que vous déclarez avec un niveau d'accès [Private](../../../../visual-basic/language-reference/modifiers/private.md) sont disponibles pour chaque procédure de ce module, mais pas pour le code d'un autre module.  L'instruction `Dim` au niveau du module a la valeur `Private` par défaut si vous n'utilisez aucun mot clé de niveau d'accès.  Toutefois, vous pouvez faire en sorte que la portée et le niveau d'accès soient plus évidents en utilisant le mot clé `Private` dans l'instruction `Dim`.  
  
 Dans l'exemple précédent, toutes les procédures définies dans le module peuvent faire référence à la variable chaîne `strMsg`.  Lors de l'appel de la seconde procédure, celle\-ci affiche le contenu de la variable chaîne `strMsg` dans une boîte de dialogue.  
  
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
  
### Portée d'espace de noms  
 Si vous déclarez un élément au niveau du module à l'aide du mot clé [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) ou [Public](../../../../visual-basic/language-reference/modifiers/public.md), il est accessible à toutes les procédures dans tout l'espace de noms dans lequel l'élément est déclaré.  Avec la modification suivante apportée à l'exemple ci\-dessus, la variable chaîne `strMsg` peut faire l'objet d'une référence par le code n'importe où dans l'espace de noms de sa déclaration :  
  
```  
' Include this declaration at module level (not inside any procedure).  
Public strMsg As String  
```  
  
 La portée d'espace de noms inclut des espaces de noms imbriqués.  Un élément disponible dans un espace de noms l'est également dans tout espace de noms imbriqué dans le précédent.  
  
 Si votre projet ne contient aucune [Namespace Statement](../../../../visual-basic/language-reference/statements/namespace-statement.md), l'ensemble des éléments du projet se trouve dans le même espace de noms.  Dans ce cas, la portée d'espace de noms peut être représentée comme la portée du projet.  Les éléments `Public` d'un module, d'une classe ou d'une structure sont également accessibles à tout projet qui fait référence à leur projet.  
  
## Choix de portée  
 Lorsque vous déclarez une variable, tenez compte des points suivants lors du choix de sa portée.  
  
### Avantages offerts par les variables locales  
 Les variables locales sont un bon choix pour tous les types de calculs temporaires, pour les raisons suivantes :  
  
-   **Capacité à éviter les conflits de noms.** Les noms de variables locales ne risquent pas d'entrer en conflit.  Par exemple, vous pouvez créer plusieurs procédures différentes qui contiennent une variable appelée `intTemp`.  Tant que chaque variable `intTemp` est déclarée comme variable locale, chaque procédure ne reconnaît que sa propre version de la variable `intTemp`.  N'importe quelle procédure peut modifier la valeur de sa variable locale `intTemp` sans affecter les variables `intTemp` contenues dans les autres procédures.  
  
-   **Consommation de mémoire.** Les variables locales consomment de la mémoire que lorsque leur procédure s'exécute.  Leur mémoire est diffusée lorsque la procédure retourne au code appelant.  Par contraste, les variables [Shared](../../../../visual-basic/language-reference/modifiers/shared.md) et [Static](../../../../visual-basic/language-reference/modifiers/static.md) consomment des ressources mémoire tant que votre application est en cours d'exécution, aussi utilisez\-les uniquement lorsque cela est nécessaire.  Les *variables d'instance* consomment de la mémoire au cours de la durée de vie de leur instance, ce qui les rend moins efficaces que des variables locales, mais potentiellement plus efficaces que les variables `Shared` ou `Static`.  
  
### Réduire la portée  
 En règle générale, lorsque vous déclarez une variable ou une constante, il est conseillé de définir une portée aussi restreinte que possible \(la portée de bloc est la plus petite\).  Cela permet de conserver de la mémoire et de réduire les risques que votre code fasse référence à la mauvaise variable.  De même, ne déclarez une variable de type [Static](../../../../visual-basic/language-reference/modifiers/static.md) que lorsque sa valeur doit être conservée entre les appels de procédure.  
  
## Voir aussi  
 [Declared Element Characteristics](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)   
 [How to: Control the Scope of a Variable](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-control-the-scope-of-a-variable.md)   
 [Lifetime in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)   
 [Access Levels in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)   
 [References to Declared Elements](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)   
 [Déclaration de variable](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)