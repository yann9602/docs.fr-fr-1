---
title: "Conventions de codage C# (Guide de programmation C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- coding conventions, C#
- Visual C#, coding conventions
- C# language, coding conventions
ms.assetid: f4f60de9-d49b-4fb6-bab1-20e19ea24710
caps.latest.revision: 32
author: BillWagner
ms.author: wiwagn
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
ms.translationtype: Human Translation
ms.sourcegitcommit: fe32676f0e39ed109a68f39584cf41aec5f5ce90
ms.openlocfilehash: 85e113f66998157a69be3f1d9065a5c4c1117773
ms.contentlocale: fr-fr
ms.lasthandoff: 05/10/2017

---
# <a name="c-coding-conventions-c-programming-guide"></a>Conventions de codage C# (Guide de programmation C#)
La [spécification du langage C#](http://go.microsoft.com/fwlink/?LinkId=199552) ne définit pas une norme de codage. Toutefois, les instructions de cette rubrique sont utilisées par Microsoft pour développer les exemples et la documentation.  
  
 Les conventions de codage répondent aux objectifs suivants :  
  
-   Elles confèrent une apparence cohérente au code, afin que les lecteurs puissent se concentrer sur le contenu, pas sur la disposition.  
  
-   Elles permettent aux lecteurs de comprendre le code plus rapidement en formulant des hypothèses selon leur expérience antérieure.  
  
-   Elles facilitent la copie, la modification et la gestion du code.  
  
-   Elles illustrent les bonnes pratiques en C#.  
  
## <a name="naming-conventions"></a>Conventions d'affectation de noms  
  
-   Dans les exemples courts qui ne comprennent pas de [directives](../../../csharp/language-reference/keywords/using-directive.md), utilisez les qualifications d’espace de noms. Si vous savez qu'un espace de noms est importé par défaut dans un projet, vous n'êtes pas obligé de qualifier entièrement les noms à partir de cet espace de noms. Les noms qualifiés peuvent être interrompus après un point (.) s'ils sont trop longs pour contenir sur une ligne unique, comme indiqué dans l'exemple suivant.  
  
     [!code-cs[csProgGuideCodingConventions#1](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_1.cs)]  
  
-   Vous n'avez pas à modifier les noms des objets qui ont été créés à l'aide des outils du concepteur Visual Studio pour les rendre conformes aux autres directives.  
  
## <a name="layout-conventions"></a>Conventions de disposition  
 Une bonne disposition utilise la mise en forme pour souligner la structure de votre code et en faciliter la lecture. Les exemples Microsoft et autres se conforment aux conventions suivantes :  
  
-   Utilisez les paramètres par défaut de l'éditeur de code (retrait intelligent, retrait de quatre caractères, tabulations enregistrées en tant qu'espaces). Pour plus d’informations, consultez [Options, Éditeur de texte, C#, Mise en forme](https://docs.microsoft.com/visualstudio/ide/reference/options-text-editor-csharp-formatting).  
  
-   Écrivez une seule instruction par ligne.  
  
-   Écrivez une seule déclaration par ligne.  
  
-   Si les lignes de continuation ne sont pas mises en retrait automatiquement, indentez-les à l'aide d'un taquet de tabulation (quatre espaces).  
  
-   Ajoutez au moins une ligne blanche entre les définitions des méthodes et les définitions des propriétés.  
  
-   Utilisez des parenthèses pour rendre apparentes les clauses d'une expression, comme illustré dans le code suivant.  
  
     [!code-cs[csProgGuideCodingConventions#2](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_2.cs)]  
  
## <a name="commenting-conventions"></a>Conventions de commentaires  
  
-   Placez le commentaire sur une ligne séparée, pas à la fin d'une ligne de code.  
  
-   Commencez le commentaire par une lettre majuscule.  
  
-   Terminez le texte de commentaire par un point.  
  
-   Insérez un espace entre le délimiteur de commentaire (//) et le texte du commentaire, comme illustré dans l'exemple suivant.  
  
     [!code-cs[csProgGuideCodingConventions#3](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_3.cs)]  
  
-   Ne créez pas de blocs d'astérisques mis en forme autour des commentaires.  
  
## <a name="language-guidelines"></a>Directives du langage  
 Les sections suivantes décrivent les pratiques que l'équipe C# suit pour préparer les exemples de code et autres.  
  
### <a name="string-data-type"></a>String, type de données  
  
-   Utilisez l'opérateur `+` pour concaténer les chaînes courtes, comme illustré dans le code suivant.  
  
     [!code-cs[csProgGuideCodingConventions#6](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_4.cs)]  
  
-   Pour ajouter des chaînes dans des boucles, en particulier lorsque vous travaillez avec une quantité de texte importante, utilisez un objet <xref:System.Text.StringBuilder>.  
  
     [!code-cs[csProgGuideCodingConventions#7](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_5.cs)]  
  
### <a name="implicitly-typed-local-variables"></a>Variables locales implicitement typées  
  
-   Utilisez le [typage implicite](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md) pour les variables locales quand le type de la variable est évident à droite de l’assignation ou quand le type précis n’importe pas.  
  
     [!code-cs[csProgGuideCodingConventions#8](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_6.cs)]  
  
-   N’utilisez pas [var](../../../csharp/language-reference/keywords/var.md) quand le type n’est pas apparent à droite de l’assignation.  
  
     [!code-cs[csProgGuideCodingConventions#9](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_7.cs)]  
  
-   Ne vous basez pas sur le nom de la variable pour spécifier son type. Il peut ne pas être correct.  
  
     [!code-cs[csProgGuideCodingConventions#10](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_8.cs)]  
  
-   Évitez d’utiliser `var` à la place de [dynamic](../../../csharp/language-reference/keywords/dynamic.md).  
  
-   Utilisez le typage implicite pour déterminer le type de la variable de boucle dans les boucles [for](../../../csharp/language-reference/keywords/for.md) et [foreach](../../../csharp/language-reference/keywords/foreach-in.md).  
  
     L'exemple suivant utilise un typage implicite dans une instruction `for`.  
  
     [!code-cs[csProgGuideCodingConventions#11](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_9.cs)]  
  
     L'exemple suivant utilise un typage implicite dans une instruction `foreach`.  
  
     [!code-cs[csProgGuideCodingConventions#12](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_10.cs)]  
  
### <a name="unsigned-data-type"></a>Type de données non signé  
  
-   En règle générale, utilisez `int` plutôt que les types non signés. L'utilisation de `int` est commun en C# et il est plus facile d'interagir avec d'autres bibliothèques lorsque vous utilisez `int`.  
  
### <a name="arrays"></a>Tableaux  
  
-   Utilisez la syntaxe concise lorsque vous initialisez des tableaux sur la ligne de déclaration.  
  
     [!code-cs[csProgGuideCodingConventions#13](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_11.cs)]  
  
### <a name="delegates"></a>Délégués  
  
-   Utilisez la syntaxe concise pour créer des instances d'un type délégué.  
  
     [!code-cs[csProgGuideCodingConventions#14](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_12.cs)]  
  
     [!code-cs[csProgGuideCodingConventions#15](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_13.cs)]  
  
### <a name="try-catch-and-using-statements-in-exception-handling"></a>Instructions try-catch et using dans la gestion des exceptions  
  
-   Utilisez une instruction [try-catch](../../../csharp/language-reference/keywords/try-catch.md) pour la plus grande part de la gestion des exceptions.  
  
     [!code-cs[csProgGuideCodingConventions#16](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_14.cs)]  
  
-   Simplifiez votre code à l’aide de l’instruction [using](../../../csharp/language-reference/keywords/using-statement.md) C#. Si vous avez une instruction [try-finally](../../../csharp/language-reference/keywords/try-finally.md) dans laquelle le seul code du bloc `finally` est un appel à la méthode <xref:System.IDisposable.Dispose%2A>, utilisez à la place une instruction `using`.  
  
     [!code-cs[csProgGuideCodingConventions#17](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_15.cs)]  
  
### <a name="-and-124124-operators"></a>Opérateurs && et &#124;&#124;  
  
-   Pour éviter les exceptions et accroître les performances en ignorant les comparaisons superflues, utilisez [&&](../../../csharp/language-reference/operators/conditional-and-operator.md) au lieu de [&](../../../csharp/language-reference/operators/and-operator.md) et [&#124;&#124;](../../../csharp/language-reference/operators/conditional-or-operator.md) au lieu de [&#124;](../../../csharp/language-reference/operators/or-operator.md) quand vous effectuez des comparaisons, comme indiqué dans l’exemple suivant.  
  
     [!code-cs[csProgGuideCodingConventions#18](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_16.cs)]  
  
### <a name="new-operator"></a>New, opérateur  
  
-   Utilisez la forme concise d'instanciation d'objets, avec un typage implicite, comme indiqué dans la déclaration suivante.  
  
     [!code-cs[csProgGuideCodingConventions#19](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_17.cs)]  
  
     La ligne précédente est équivalente à la déclaration suivante.  
  
     [!code-cs[csProgGuideCodingConventions#20](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_18.cs)]  
  
-   Utilisez les initialiseurs d'objets pour simplifier la création d'objet.  
  
     [!code-cs[csProgGuideCodingConventions#21](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_19.cs)]  
  
### <a name="event-handling"></a>Gestion des événements  
  
-   Si vous définissez un gestionnaire d’événements que vous n’avez pas besoin de supprimer ultérieurement, utilisez une expression lambda.  
  
     [!code-cs[csProgGuideCodingConventions#22](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_20.cs)]  
  
     [!code-cs[csProgGuideCodingConventions#23](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_21.cs)]  
  
### <a name="static-members"></a>Membres static  
  
-   Appelez les membres [static](../../../csharp/language-reference/keywords/static.md) en utilisant le nom de la classe : *Nom_classe.Membre_statique*. Cette pratique rend le code plus lisible en clarifiant l'accès aux membres static.  Ne qualifiez pas un membre static défini dans une classe de base avec le nom d'une classe dérivée.  Lorsque ce code est compilé, la lisibilité du code est trompeuse et le code peut s'interrompre à l'avenir si vous ajoutez à la classe dérivée un membre static de même nom.  
  
### <a name="linq-queries"></a>Requêtes LINQ  
  
-   Utilisez des noms explicites pour les variables de requête. L'exemple suivant utilise `seattleCustomers` pour les clients qui se trouvent à Seattle.  
  
     [!code-cs[csProgGuideCodingConventions#25](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_22.cs)]  
  
-   Utilisez des alias pour vous assurer que les noms de propriétés des types anonymes sont correctement écrits en majuscules à l'aide de la casse Pascal.  
  
     [!code-cs[csProgGuideCodingConventions#26](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_23.cs)]  
  
-   Renommez les propriétés lorsque les noms de propriétés dans le résultat sont ambigus. Par exemple, si votre requête retourne un nom de client et un ID de distributeur, au lieu de les laisser sous la forme `Name` et `ID` dans le résultat, renommez-les pour montrer clairement que `Name` est le nom d'un client et `ID` l'ID d'un distributeur.  
  
     [!code-cs[csProgGuideCodingConventions#27](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_24.cs)]  
  
-   Utilisez le typage implicite dans la déclaration des variables de requête et des variables de portée.  
  
     [!code-cs[csProgGuideCodingConventions#25](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_22.cs)]  
  
-   Alignez les clauses de requête sous la clause [from](../../../csharp/language-reference/keywords/from-clause.md), comme illustré dans les exemples précédents.  
  
-   Utilisez les clauses [where](../../../csharp/language-reference/keywords/where-clause.md) avant les autres clauses de requête pour garantir que les clauses de requête ultérieures opèrent sur l’ensemble de données réduit et filtré.  
  
     [!code-cs[csProgGuideCodingConventions#29](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_25.cs)]  
  
-   Utilisez plusieurs clauses `from` au lieu d’une clause [join](../../../csharp/language-reference/keywords/join-clause.md) pour accéder aux collections internes. Par exemple, une collection d'objets `Student` peut contenir chacune une collection de scores de test. Lorsque la requête suivante est exécutée, elle retourne chaque score supérieur à 90, avec le nom de l'étudiant correspondant.  
  
     [!code-cs[csProgGuideCodingConventions#30](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_26.cs)]  
  
## <a name="security"></a>Sécurité  
 Suivez les instructions indiquées dans [Instructions de codage sécurisé](../../../standard/security/secure-coding-guidelines.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Conventions de codage Visual Basic](../../../visual-basic/programming-guide/program-structure/coding-conventions.md)   
 [Instructions de codage sécurisé](../../../standard/security/secure-coding-guidelines.md)
