---
title: "Nouveautés de C# 7 | Guide C#"
description: "Découvrez les nouvelles fonctionnalités disponibles dans la prochaine version 7 du langage C#."
keywords: "C#, .NET, .NET Core, dernières fonctionnalités, nouveautés"
author: BillWagner
ms.author: wiwagn
ms.date: 12/21/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: fd41596d-d0c2-4816-b94d-c4d00a5d0243
ms.openlocfilehash: 3f3598fce5abeb67b772f51ed6f93e6ada4c92d0
ms.sourcegitcommit: 401c4427a3ec0d1263543033b3084039278509dc
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/06/2017
---
# <a name="whats-new-in-c-7"></a>Nouveautés de C# 7

C# 7 ajoute un certain nombre de nouvelles fonctionnalités au langage C# :
* [Variables `out`](#out-variables)
    - Vous pouvez déclarer des valeurs `out` inline comme arguments de la méthode dans laquelle elles sont utilisées.
* [Tuples](#tuples)
    - Vous pouvez créer des types légers et sans nom qui contiennent plusieurs champs publics. Les compilateurs et les outils de l’IDE comprennent la sémantique de ces types.
* [Éléments ignorés](#discards)
    - Les éléments ignorés sont les variables temporaires en écriture seule utilisées dans les attributions quand vous ne vous souciez pas de la valeur assignée. Ils sont particulièrement utiles lors de la déconstruction de tuples et de types définis par l’utilisateur, ainsi que lors de l’appel de méthodes avec des paramètres `out`.
* [Critères spéciaux](#pattern-matching)
    - Vous pouvez créer une logique de branchement basée sur des types arbitraires et les valeurs des membres de ces types.
* [Variables locales et retours `ref`](#ref-locals-and-returns)
    - Les arguments et les variables locales de méthode peuvent être des références à un autre stockage.
* [Fonctions locales](#local-functions)
    - Vous pouvez imbriquer des fonctions dans d’autres fonctions afin de limiter leur portée et leur visibilité.
* [Autres membres expression-bodied](#more-expression-bodied-members)
    - La liste des membres pouvant être créés à l’aide d’expressions s’est allongée.
* [Expressions `throw`](#throw-expressions)
    - Vous pouvez lever des exceptions dans les constructions de code qui n’étaient pas autorisées auparavant, car `throw` était une instruction. 
* [Types de retour async généralisés](#generalized-async-return-types)
    - Les méthodes déclarées avec le modificateur `async` peuvent retourner d’autres types en plus de `Task` et de `Task<T>`.
* [Améliorations de la syntaxe littérale numérique](#numeric-literal-syntax-improvements)
    - De nouveaux jetons améliorent la lisibilité des constantes numériques.

Le reste de cette rubrique traite de chacune de ces fonctionnalités. Vous découvrirez la logique de chacune d’elles. Vous allez apprendre leur syntaxe. Grâces à des exemples de scénarios utilisant les nouvelles fonctionnalités, vous gagnerez en productivité en tant que développeur. 

## <a name="out-variables"></a>Variables `out`

La syntaxe existante qui prend en charge les paramètres `out` a été améliorée dans cette version.  

Auparavant, vous deviez séparer la déclaration de la variable out et son initialisation en deux instructions distinctes :

[!code-csharp[OutVariableOldStyle](../../../samples/snippets/csharp/new-in-7/program.cs#03_OutVariableOldStyle "classic out variable declaration")]

Vous pouvez désormais déclarer des variables `out` dans la liste d’arguments d’un appel de méthode, au lieu d’écrire une instruction de déclaration distincte :

[!code-csharp[OutVariableDeclarations](../../../samples/snippets/csharp/new-in-7/program.cs#01_OutVariableDeclarations "Out variable declarations")]

Par souci de clarté, vous voulez peut-être spécifier le type de la variable `out`, comme indiqué ci-dessus. Toutefois, le langage prend en charge l’utilisation d’une variable locale implicitement typée :

[!code-csharp[OutVarVariableDeclarations](../../../samples/snippets/csharp/new-in-7/program.cs#02_OutVarVariableDeclarations "Implicitly typed Out variable")]

* Le code est plus facile à lire. 
    - Vous déclarez la variable out à l’endroit où vous l’utilisez, et non pas sur une autre ligne au-dessus.
* Il n’est pas nécessaire d’assigner une valeur initiale.
    - En déclarant la variable `out` à l’endroit où elle est utilisée dans un appel de méthode, vous ne pouvez pas l’utiliser accidentellement avant qu’elle soit assignée.

L’utilisation la plus courante de cette fonctionnalité est le modèle `Try`. Dans ce modèle, une méthode retourne un `bool` indiquant la réussite ou l’échec, et une variable `out` qui donne le résultat en cas de réussite de la méthode.

Quand vous utilisez la déclaration de variable `out`, la variable déclarée « fuit » dans la portée externe de l’instruction if. Cela vous permet d’utiliser la variable par la suite :

```csharp
if (!int.TryParse(input, out int result))
{    
    return null;
}

return result;
```

## <a name="tuples"></a>Tuples

> [!NOTE]
> Les nouvelles fonctionnalités des tuples exigent les types <xref:System.ValueTuple>.
> Vous devez ajouter le package NuGet [`System.ValueTuple`](https://www.nuget.org/packages/System.ValueTuple/) pour pouvoir l’utiliser sur les plateformes qui n’incluent pas les types.
>
> Ces fonctionnalités sont semblables à celles d’autres langages qui reposent sur les types fournis dans le framework. `async` et `await` qui reposent sur l’interface `INotifyCompletion`, et LINQ qui repose sur `IEnumerable<T>` en sont des exemples. Toutefois, le mécanisme de remise change à mesure que le .NET dépend de moins en moins de la plateforme. Le .NET Framework n’est pas toujours émis à la même cadence que le compilateur de langage. Quand les nouvelles fonctionnalités de langage reposent sur de nouveaux types, ces types sont disponibles sous la forme de packages NuGet au moment de l’émission des fonctionnalités de langage. À mesure que ces nouveaux types sont ajoutés à l’API .NET Standard et remis dans le cadre du framework, les packages NuGet ne sont plus obligatoires.

C# fournit une syntaxe complète pour les classes et les structs, utilisée pour expliquer l’intention de votre conception. Cependant, cette syntaxe complète nécessite parfois un travail supplémentaire avec peu d’avantages. Vous pouvez souvent écrire des méthodes qui nécessitent une structure simple contenant plusieurs éléments de données. Pour prendre en charge ces scénarios, des *tuples* ont été ajoutées à C#. Les tuples sont des structures de données légères contenant plusieurs champs pour représenter les membres de données.
Les champs ne sont pas validés, et vous ne pouvez pas définir vos propres méthodes.

> [!NOTE]
> Les tuples étaient disponibles avant C# 7, mais ils n’étaient pas efficaces et n’avaient aucune prise en charge du langage.
> Cela signifiait que les éléments tuples pouvaient uniquement être référencés comme `Item1`, `Item2`, et ainsi de suite. C# 7 introduit la prise en charge du langage pour les tuples, ce qui permet d’utiliser des noms sémantiques pour les champs d’un tuple avec de nouveaux types tuple plus efficaces.

Vous pouvez créer un tuple en assignant chaque membre à une valeur :

[!code-csharp[UnnamedTuple](../../../samples/snippets/csharp/new-in-7/program.cs#04_UnnamedTuple "Unnamed tuple")]

Cette assignation crée un tuple dont les membres sont `Item1` et `Item2`, que vous pouvez utiliser de la même façon que <xref:System.Tuple>. Vous pouvez modifier la syntaxe pour créer un tuple qui fournit des noms sémantiques à chacun des membres du tuple :

[!code-csharp[NamedTuple](../../../samples/snippets/csharp/new-in-7/program.cs#05_NamedTuple "Named tuple")]

Le tuple `namedLetters` contient des champs appelés `Alpha` et `Beta`. Ces noms n’existent qu’au moment de la compilation et ne sont pas conservés par exemple lors de l’inspection du tuple à l’aide de la réflexion lors de l’exécution.

Dans une assignation de tuple, vous pouvez également spécifier les noms des champs dans la partie droite :

[!code-csharp[ImplicitNamedTuple](../../../samples/snippets/csharp/new-in-7/program.cs#06_ImplicitNamedTuple "Implicitly named tuple")]

Vous pouvez spécifier des noms pour les champs dans la partie gauche et dans la partie droite de l’assignation :

[!code-csharp[NamedTupleConflict](../../../samples/snippets/csharp/new-in-7/program.cs#07_NamedTupleConflict "Named tuple conflict")]

La ligne ci-dessus génère un avertissement, `CS8123`, vous indiquant que les noms dans la partie droite de l’assignation, `Alpha` et `Beta`, sont ignorés, car ils sont en conflit avec les noms dans la partie gauche, `First` et `Second`.

Les exemples ci-dessus illustrent la syntaxe de base permettant de déclarer des tuples. Ces derniers sont surtout utiles comme types de retour pour les méthodes `private` et `internal`. Ils fournissent une syntaxe simple pour permettre à ces méthodes de retourner plusieurs valeurs discrètes : vous enregistrez le travail de création d’un `class` ou d’un `struct` qui définit le type retourné. Il n’est pas nécessaire de créer un nouveau type.

Il est plus efficace et plus productif de créer un tuple.
Il s’agit d’une syntaxe légère et plus simple utilisée pour définir une structure de données qui comporte plusieurs valeurs. L’exemple de méthode ci-dessous retourne les valeurs minimale et maximale trouvées dans une séquence d’entiers :

[!code-csharp[TupleReturningMethod](../../../samples/snippets/csharp/new-in-7/program.cs#08_TupleReturningMethod "Tuple returning method")]

En utilisant les tuples de cette façon, vous bénéficiez de plusieurs avantages :

* Vous enregistrez le travail de création d’un `class` ou d’un `struct` qui définit le type retourné. 
* Vous n’avez pas besoin de créer un type.
* Les améliorations du langage suppriment la nécessité d’appeler les méthodes <xref:System.Tuple.Create``1(``0)>.

La déclaration pour la méthode fournit les noms des champs du tuple qui est retourné. Quand vous appelez la méthode, la valeur de retour est un tuple dont les champs sont `Max` et `Min` :

[!code-csharp[CallingTupleMethod](../../../samples/snippets/csharp/new-in-7/program.cs#09_CallingTupleMethod "Calling a tuple returning method")]

Dans certains cas, vous pouvez souhaiter décompresser les membres d’un tuple qui ont été retournés à partir d’une méthode.  Pour ce faire, déclarez des variables distinctes pour chacune des valeurs dans le tuple. Cette opération est appelée *déconstruction* du tuple :

[!code-csharp[CallingWithDeconstructor](../../../samples/snippets/csharp/new-in-7/program.cs#10_CallingWithDeconstructor "Deconstructing a tuple")]

<!-- Add wildcards here, if they are in C# 7
-->

Vous pouvez également fournir une déconstruction similaire pour tout type dans le .NET. Pour ce faire, écrivez une méthode `Deconstruct` comme un membre de la classe. Cette méthode `Deconstruct` fournit un ensemble d’arguments `out` pour chacune des propriétés que vous voulez extraire. Prenons la classe `Point` suivante qui fournit une méthode de déconstructeur qui extrait les coordonnées `X` et `Y` :

[!code-csharp[PointWithDeconstruction](../../../samples/snippets/csharp/new-in-7/point.cs#11_PointWithDeconstruction "Point with deconstruction method")]
 
Vous pouvez extraire des champs individuels en assignant un tuple à un `Point` :

[!code-csharp[DeconstructPoint](../../../samples/snippets/csharp/new-in-7/program.cs#12_DeconstructPoint "Deconstruct a point")]

Vous n’êtes pas lié par les noms définis dans la méthode `Deconstruct`. Vous pouvez renommer les variables d’extraction dans le cadre de l’assignation :  

[!code-csharp[DeconstructNames](../../../samples/snippets/csharp/new-in-7/program.cs#13_DeconstructNames "Deconstruct with new names")]

La [rubrique relative au tuples](../tuples.md) vous permet d’étudier les tuples plus en détail.

## <a name="discards"></a>Éléments ignorés

Souvent, lors de la déconstruction d’un tuple ou de l’appel d’une méthode avec des paramètres `out`, vous devez définir une variable dont la valeur ne vous importe pas et que vous ne prévoyez pas d’utiliser. C# ajoute la prise en charge des *éléments ignorés* pour gérer ce scénario. Un élément ignoré est une variable en écriture seule dont le nom est `_` (caractère de soulignement) ; vous pouvez assigner toutes les valeurs que vous souhaitez ignorer à la variable unique. Un élément ignoré est semblable à une variable non assignée ; en dehors de l’instruction d’assignation, l’élément ignoré ne peut pas être utilisé dans le code.

Les éléments ignorés sont pris en charge dans les scénarios suivants :

* Lors de la déconstruction de tuples ou de types définis par l’utilisateur.

* Lors d’appels à des méthodes avec des paramètres [out](../language-reference/keywords/out.md).

* Dans une opération de critères spéciaux avec les instructions [is](../language-reference/keywords/is.md) et [switch](../language-reference/keywords/switch.md).

* Comme un identificateur autonome quand vous voulez explicitement identifier la valeur d’une assignation comme un élément ignoré.

L’exemple suivant définit une méthode `QueryCityDataForYears` qui retourne un tuple à 6 composants qui contient des données pour une ville au cours de deux années différentes. L’appel de méthode dans l’exemple s’intéresse uniquement à deux valeurs de population retournées par la méthode et traite par conséquent les valeurs restantes dans le tuple comme des éléments ignorés lors de la déconstruction du tuple.

[!code-csharp[Tuple-discard](../../../samples/snippets/csharp/programming-guide/deconstructing-tuples/discard-tuple1.cs)]

Pour plus d’informations, consultez [Éléments ignorés](../discards.md).
 
## <a name="pattern-matching"></a>Critères spéciaux

Les *critères spéciaux* constituent une fonctionnalité qui vous permet d’implémenter la distribution de méthodes sur des propriétés autres que le type d’un objet. Vous êtes probablement déjà familiarisé avec la distribution de méthodes en fonction du type d’un objet. Dans la programmation orientée objet, les méthodes virtuelles et override fournissent une syntaxe du langage permettant d’implémenter la distribution de méthodes basées sur le type d’un objet. Les classes de base et dérivées offrent des implémentations différentes. Les expressions de critères spéciaux étendent ce concept de manière à vous permettre d’implémenter facilement des modèles de distribution similaires pour les types et les éléments de données qui ne sont pas liés au moyen d’une hiérarchie d’héritage. 

Les critères spéciaux prennent en charge les expressions `is` et les expressions `switch`. L’une ou l’autre permettent d’inspecter un objet et ses propriétés afin de déterminer s’il correspond au modèle recherché. Vous utilisez le mot clé `when` pour spécifier des règles supplémentaires pour le modèle.

### <a name="is-expression"></a>Expression `is`

L’expression de modèle `is` étend l’opérateur `is` classique pour interroger un objet au-delà de son type.

Commençons par un scénario simple. Nous allons ajouter à ce scénario des fonctionnalités qui illustrent la façon dont les expressions de critères spéciaux facilitent les algorithmes qui fonctionnent avec les types non apparentés. Nous allons commencer par une méthode qui calcule la somme d’un certain nombre de lancers de dés :

[!code-csharp[SumDieRolls](../../../samples/snippets/csharp/new-in-7/patternmatch.cs#14_SumDieRolls "Sum die rolls")]

Vous constaterez peut-être rapidement que vous devez calculer la somme de lancers de dés où certains des lancers sont effectués avec plusieurs dés. Une partie de la séquence d’entrée peut être constituée de plusieurs résultats au lieu d’un seul nombre :

[!code-csharp[SumDieRollsWithGroups](../../../samples/snippets/csharp/new-in-7/patternmatch.cs#15_SumDieRollsWithGroups "Sum die rolls with groups")]

L’expression de modèle `is` fonctionne très bien dans ce scénario. Dans le cadre de la vérification du type, vous écrivez une initialisation de variable. Cela crée une variable du type de runtime validé.

À mesure que vous continuerez à développer ces scénarios, vous constaterez peut-être que vous générez plus d’instructions `if` et `else if`. Quand cela deviendra peu pratique, vous voudrez probablement passer à des expressions de modèle `switch`.

### <a name="switch-statement-updates"></a>Mises à jour d’instructions `switch`

L’*expression de correspondance* a une syntaxe familière, basée sur l’instruction `switch` qui fait déjà partie du langage C#. Traduisons le code existant pour utiliser une expression de correspondance avant d’ajouter de nouveaux cas : 

[!code-csharp[SumUsingSwitch](../../../samples/snippets/csharp/new-in-7/patternmatch.cs#16_SumUsingSwitch "Sum using switch")]

Les expressions de correspondance ont une syntaxe légèrement différente des expressions `is`, dans laquelle vous déclarez le type et la variable au début de l’expression `case`.

Les expressions de correspondance prennent également en charge les constantes. Cela peut faire gagner du temps en éliminant les cas simples :

[!code-csharp[SwitchWithConstants](../../../samples/snippets/csharp/new-in-7/patternmatch.cs#17_SwitchWithConstants "Switch with constants")]

Le code ci-dessus ajoute des cas pour `0` comme un cas particulier de `int`, et `null` comme un cas particulier quand il n’y a aucune entrée. Cela illustre une nouvelle fonctionnalité importante des expressions de modèle switch : l’ordre des expressions `case` a maintenant de l’importance. Le cas `0` doit apparaître avant le cas général `int`. Sinon, le premier modèle à mettre en correspondance serait le cas `int`, même si la valeur est `0`. Si vous classez par mégarde des expressions de correspondance de sorte qu’un cas ultérieur a déjà été traité, le compilateur le signale et génère une erreur.

Ce même comportement active le cas particulier pour une séquence d’entrée vide.
Vous pouvez voir que le cas pour un élément `IEnumerable` qui contient des éléments doit apparaître avant le cas général `IEnumerable`.

Cette version a également ajouté un cas `default`. Le cas `default` est toujours évalué en dernier, quel que soit l’ordre dans lequel il apparaît dans la source. C’est pourquoi la convention est de placer le cas `default` en dernier.

Pour finir, ajoutons un dernier `case` pour un nouveau style de dé. Certains jeux utilisent des dés percentiles pour représenter des plages de nombres plus importantes. 

> [!NOTE]
> Deux dés percentiles à 10 faces peuvent représenter chaque nombre compris entre 0 et 99. Un dé a des faces marquées `00`, `10`, `20`, ... `90`. L’autre dé a des faces marquées `0`, `1`, `2`, ... `9`. Additionnez les valeurs des deux dés. Vous pouvez alors obtenir n’importe quel nombre compris entre 0 à 99.

Pour ajouter ce genre de dé à votre collection, commencez par définir un type pour représenter le dé percentile. La propriété `TensDigit` stocke les valeurs `0`, `10`, `20`, jusqu’à `90` :

[!code-csharp[18_PercentileDice](../../../samples/snippets/csharp/new-in-7/patternmatch.cs#18_PercentileDice "Percentile Die type")]

Ajoutez ensuite une expression de correspondance `case` pour le nouveau type :

[!code-csharp[SwitchWithNewTypes](../../../samples/snippets/csharp/new-in-7/patternmatch.cs#19_SwitchWithNewTypes "Include Percentile Die type")]

La nouvelle syntaxe pour les expressions de critères spéciaux facilite la création d’algorithmes de distribution basés sur le type d’un objet, ou d’autres propriétés, en utilisant une syntaxe claire et concise. Les expressions de critères spéciaux permettent ces constructions sur les types de données qui ne sont pas liés par héritage.

Pour plus d’informations sur les critères spéciaux, consultez la rubrique consacrée aux [critères spéciaux en C#](../pattern-matching.md).

## <a name="ref-locals-and-returns"></a>Variables locales et retours ref

Cette fonctionnalité active les algorithmes qui utilisent et retournent des références à des variables définies ailleurs. C’est le cas, par exemple, lors de la recherche d’un emplacement unique comportant certaines caractéristiques dans une matrice de grande taille. Une méthode retournerait les deux index pour un seul emplacement dans la matrice :

[!code-csharp[FindReturningIndices](../../../samples/snippets/csharp/new-in-7/MatrixSearch.cs#20_FindReturningIndices "Find returning indices")]

Ce code présente de nombreux problèmes. Tout d’abord, il s’agit d’une méthode publique qui retourne un tuple. Le langage prend en charge ce fait, mais les types définis par l’utilisateur (les classes ou les structs) conviennent mieux pour les API publiques.

Ensuite, cette méthode retourne les index à l’élément dans la matrice.
Cela conduit les appelants à écrire du code qui utilise ces index pour déréférencer la matrice et modifier un seul élément :

[!code-csharp[UpdateItemFromIndices](../../../samples/snippets/csharp/new-in-7/program.cs#21_UpdateItemFromIndices "Update Item From Indices")]

Il est préférable d’écrire une méthode qui retourne une *référence* à l’élément de la matrice que vous voulez changer. Pour y parvenir, la seule solution consiste à utiliser du code unsafe et à retourner un pointeur vers un `int` dans des versions précédentes.

Examinons en détail une série de changements pour illustrer la fonctionnalité de variable locale de référence et montrer comment créer une méthode qui retourne une référence à un stockage interne.
Au cours du processus, vous allez apprendre les règles de la fonctionnalité de retour ref et de variables locales ref qui vous évite de l’utiliser incorrectement par mégarde.

Commencez par modifier la déclaration de méthode `Find` pour qu’elle retourne un `ref int` au lieu d’un tuple. Ensuite, modifiez l’instruction return de sorte qu’elle retourne la valeur stockée dans la matrice plutôt que les deux index :

```csharp
// Note that this won't compile. 
// Method declaration indicates ref return,
// but return statement specifies a value return.
public static ref int Find2(int[,] matrix, Func<int, bool> predicate)
{
    for (int i = 0; i < matrix.GetLength(0); i++)
        for (int j = 0; j < matrix.GetLength(1); j++)
            if (predicate(matrix[i, j]))
                return matrix[i, j];
    throw new InvalidOperationException("Not found");
}
```

Quand vous déclarez qu’une méthode retourne une variable `ref`, vous devez également ajouter le mot clé `ref` à chaque instruction return. Cela indique un retour par référence, et permet aux développeurs qui lisent le code ultérieurement de ne pas oublier que la méthode effectue un retour par référence :

[!code-csharp[FindReturningRef](../../../samples/snippets/csharp/new-in-7/MatrixSearch.cs#22_FindReturningRef "Find returning by reference")]

Maintenant que la méthode retourne une référence à la valeur entière dans la matrice, vous devez modifier l’emplacement où elle est appelée.  La déclaration `var` signifie que `valItem` est désormais un `int` au lieu d’un tuple :

[!code-csharp[AssignRefReturnToValue](../../../samples/snippets/csharp/new-in-7/program.cs#23_AssignRefReturnToValue "Assign ref return to value")]

La deuxième instruction `WriteLine` dans l’exemple ci-dessus affiche la valeur `42`, et non la valeur `24`. La variable `valItem` est un `int`, et non un `ref int`. Le mot clé `var` permet au compilateur de spécifier le type, mais il n’ajoutera pas implicitement le modificateur `ref`. Au lieu de cela, la valeur référencée par `ref return` est *copiée* dans la variable dans la partie gauche de l’assignation. La variable n’est pas une variable `ref` locale.

Pour obtenir le résultat souhaité, vous devez ajouter le `ref` modificateur à la déclaration de variable locale pour faire de la variable une référence quand la valeur de retour est une référence :

[!code-csharp[AssignRefReturn](../../../samples/snippets/csharp/new-in-7/program.cs#24_AssignRefReturn "Assign ref return")]

À présent, la deuxième instruction `WriteLine` dans l’exemple ci-dessus affiche la valeur `24`, ce qui indique que le stockage dans la matrice a été modifié. La variable locale a été déclarée avec le modificateur `ref`, et elle prendra un retour `ref`. Vous devez initialiser une variable `ref` au moment de sa déclaration : vous ne pouvez pas séparer la déclaration et l’initialisation.

Le langage C# a trois autres règles qui vous protègent contre une mauvaise utilisation des variables locales et des retours `ref` :

* Vous ne pouvez pas affecter une valeur de retour de méthode standard à une variable locale `ref`.
    - Cela rejette les instructions telles que `ref int i = sequence.Count();`.
* Vous ne pouvez pas retourner un `ref` à une variable dont la durée de vie ne s’étend pas au-delà de l’exécution de la méthode.
    - Cela signifie que vous ne pouvez pas retourner une référence à une variable locale ni une variable avec une étendue similaire.
* Les variables locales et les retours `ref` ne peuvent pas être utilisés avec les méthodes Async.
    - Le compilateur ne peut pas savoir si la variable référencée a été définie à sa valeur finale quand la méthode Async est retournée.

L’ajout de variables locales ref et de retours ref permet d’utiliser des algorithmes qui sont plus efficaces en évitant la copie de valeurs, ou d’effectuer plusieurs fois des opérations de déréférencement. 

## <a name="local-functions"></a>Fonctions locales

De nombreuses conceptions pour les classes incluent des méthodes qui sont appelées à partir d’un seul emplacement. Ces méthodes privées supplémentaires maintiennent chaque méthode réduite et focalisée. Toutefois, elles peuvent rendre plus difficile la compréhension d’une classe quand elle est lue pour la première fois. Ces méthodes doivent être comprises en dehors du contexte de l’emplacement d’appel unique.

Pour ces conceptions, les *fonctions locales* vous permettent de déclarer des méthodes dans le contexte d’une autre méthode. Il est ainsi plus facile pour les lecteurs de la classe de voir que la méthode locale est appelée uniquement à partir du contexte dans lequel elle a été déclarée.

Il existe deux cas d’utilisation très courants pour les fonctions locales : les méthodes iterator publiques et les méthodes async publiques. Ces deux types de méthodes génèrent du code qui signale les erreurs plus tard que ce qu’attendent les programmeurs. Dans le cas des méthodes iterator, toute exception est observée uniquement lors de l’appel de code qui énumère la séquence retournée. Dans le cas des méthodes async, toute exception est observée uniquement quand le `Task` retourné est attendu.

Commençons par une méthode iterator :

[!code-csharp[IteratorMethod](../../../samples/snippets/csharp/new-in-7/Iterator.cs#25_IteratorMethod "Iterator method")]

Examinez le code ci-dessous, qui appelle la méthode iterator de manière incorrecte :

[!code-csharp[CallIteratorMethod](../../../samples/snippets/csharp/new-in-7/program.cs#26_CallIteratorMethod "Call iterator method")]

L’exception est levée quand `resultSet` est itéré, pas quand `resultSet` est créé.
Dans cet exemple contenu, la plupart des développeurs peuvent diagnostiquer rapidement le problème. Toutefois, dans les codes base de plus grande taille, il est fréquent que le code qui crée un itérateur ne soit pas aussi proche du code qui énumère le résultat. Vous pouvez refactoriser le code afin que la méthode publique valide tous les arguments, et qu’une méthode privée génère l’énumération :

[!code-csharp[IteratorMethodRefactored](../../../samples/snippets/csharp/new-in-7/Iterator.cs#27_IteratorMethodRefactored "Iterator method refactored")]

Cette version refactorisée lève immédiatement des exceptions, car la méthode publique n’est pas une méthode iterator ; seule la méthode privée utilise la syntaxe `yield return`. Toutefois, cette refactorisation pose deux problèmes potentiels. La méthode privée ne doit être appelée qu’à partir de la méthode d’interface publique, car sinon, toute validation d’argument est ignorée.
Les lecteurs de la classe doivent le découvrir en lisant l’intégralité de la classe et en recherchant toute autre référence à la méthode `alphabetSubsetImplementation`.

Vous pourrez rendre cette intention de conception plus claire en déclarant `alphabetSubsetImplementation` comme une fonction locale à l’intérieur de la méthode d’API publique :

[!code-csharp[22_IteratorMethodLocal](../../../samples/snippets/csharp/new-in-7/Iterator.cs#28_IteratorMethodLocal "Iterator method with local function")]

La version ci-dessus indique clairement que la méthode locale est référencée uniquement dans le contexte de la méthode externe. Les règles relatives aux fonctions locales peuvent également garantir qu’un développeur ne peut pas appeler accidentellement la fonction locale à partir d’un autre emplacement dans la classe et ignorer la validation d’argument.

Il est possible d’utiliser la même technique avec les méthodes `async` pour garantir que les exceptions résultant de la validation d’argument sont levées avant le début de la tâche asynchrone :

[!code-csharp[TaskExample](../../../samples/snippets/csharp/new-in-7/AsyncWork.cs#29_TaskExample "Task returning method with local function")]

> [!NOTE]
> Certaines des conceptions prises en charge par les fonctions locales peuvent également être effectuées à l’aide d’*expressions lambda*. Si cela vous intéresse, [reportez-vous aux informations supplémentaires décrivant ce qui différencie ces deux processus](../local-functions-vs-lambdas.md).

## <a name="more-expression-bodied-members"></a>Autres membres expression-bodied

C# 6 a introduit les [membres expression-bodied](csharp-6.md#expression-bodied-function-members) pour les fonctions membres, ainsi que des propriétés en lecture seule. C# 7 développe les membres autorisés pouvant être implémentés comme expressions. Dans C# 7, vous pouvez implémenter des *constructeurs*, des *finaliseurs* ainsi que des accesseurs `get` et `set` sur des *propriétés* et des *indexeurs*. Le code suivant présente des exemples de chaque élément :

[!code-csharp[ExpressionBodiedMembers](../../../samples/snippets/csharp/new-in-7/expressionmembers.cs#36_ExpressionBodiedEverything "new expression-bodied members")]

> [!NOTE]
> Cet exemple n’a pas besoin de finaliseur, mais il est présenté pour illustrer la syntaxe. Vous ne devez implémenter un finaliseur dans votre classe que si cela est nécessaire pour libérer des ressources non managées. Vous devez également envisager d’utiliser la classe <xref:System.Runtime.InteropServices.SafeHandle> au lieu de gérer directement les ressources non managées.

Ces nouveaux emplacements pour les membres expression-bodied représentent une étape importante pour le langage C# : ces fonctionnalités ont été implémentées par des membres de la communauté travaillant sur le projet open source [Roslyn](https://github.com/dotnet/Roslyn).

## <a name="throw-expressions"></a>Expressions throw

En C#, `throw` a toujours été une instruction. Étant donné que `throw` est une instruction, et non pas une expression, certaines constructions C# ne pouvaient pas l’utiliser. Il s’agit notamment des expressions conditionnelles, des expressions de fusion null, ainsi que de certaines expressions lambda. L’ajout de membres expression-bodied ajoute des emplacements supplémentaires où les expressions `throw` seraient utiles. Pour vous permettre d’écrire n’importe laquelle de ces constructions, C# 7 introduit les *expressions throw*.

La syntaxe est la même que celle que vous avez toujours utilisée pour les instructions `throw`. La seule différence est que vous pouvez maintenant les placer dans de nouveaux emplacements, comme dans une expression conditionnelle :

[!code-csharp[Throw_ExpressionExample](../../../samples/snippets/csharp/new-in-7/throwexpressions.cs#37_Throw_ExpressionExample "conditional throw expressions")]

Cette fonctionnalité permet d’utiliser des expressions throw dans des expressions d’initialisation :

[!code-csharp[ThrowInInitialization](../../../samples/snippets/csharp/new-in-7/throwexpressions.cs#38_ThrowInInitialization "conditional throw expressions")]

Auparavant, ces initialisations devaient se trouver dans un constructeur, avec les instructions throw dans le corps du constructeur :


[!code-csharp[ThrowInConstructor](../../../samples/snippets/csharp/new-in-7/throwexpressions.cs#39_ThrowInConstructor "throw statements")]

> [!NOTE]
> Les deux constructions précédentes provoquent la levée d’exceptions pendant la construction d’un objet. Celles-ci sous souvent difficilement récupérables.
> C’est pourquoi les conceptions qui lèvent des exceptions lors de la construction sont déconseillées.

## <a name="generalized-async-return-types"></a>Types de retour async généralisés

Le retour d’un objet `Task` à partir de méthodes async peut introduire des goulots d’étranglement au niveau des performances dans certains chemins. `Task` est un type référence. Si vous l’utilisez, vous allouez donc un objet. Dans les cas où une méthode déclarée avec le modificateur `async` retourne un résultat mis en cache, ou si elle s’exécute de manière synchrone, le coût en termes de temps induit par les allocations supplémentaires peut s’avérer significatif dans les sections de code critiques pour les performances. Il peut devenir très important si ces allocations se produisent dans des boucles serrées.

La nouvelle fonctionnalité du langage signifie que les méthodes async peuvent retourner d’autres types en plus de `Task`, de `Task<T>` et de `void`. Le type retourné doit toujours correspondre au modèle async, ce qui signifie qu’une méthode `GetAwaiter` doit être accessible. Pour donner un exemple concret, le type `ValueTask` a été ajouté au .NET Framework pour utiliser cette nouvelle fonctionnalité du langage : 

[!code-csharp[UsingValueTask](../../../samples/snippets/csharp/new-in-7/AsyncWork.cs#30_UsingValueTask "Using ValueTask")]

> [!NOTE]
> Vous devez ajouter le package NuGet [`System.Threading.Tasks.Extensions`](https://www.nuget.org/packages/System.Threading.Tasks.Extensions/) pour pouvoir utiliser le type <xref:System.Threading.Tasks.ValueTask%601>.

Une optimisation simple consisterait à utiliser `ValueTask` dans des emplacements où `Task` était utilisé avant. Toutefois, si vous voulez effectuer manuellement des optimisations supplémentaires, vous pouvez mettre en cache les résultats à partir du travail asynchrone et réutiliser le résultat dans les appels suivants. Le struct `ValueTask` a un constructeur avec un paramètre `Task` pour vous permettre de construire un `ValueTask` à partir de la valeur de retour de toute méthode async existante :

[!code-csharp[AsyncOptimizedValueTask](../../../samples/snippets/csharp/new-in-7/AsyncWork.cs#31_AsyncOptimizedValueTask "Return async result or cached value")]
 
Comme avec toutes les recommandations relatives aux performances, vous devez effectuer un test d’évaluation sur les deux versions avant d’apporter des changements à grande échelle à votre code.

## <a name="numeric-literal-syntax-improvements"></a>Améliorations de la syntaxe littérale numérique

La mauvaise interprétation de constantes numériques peut rendre plus difficile la compréhension du code quand il est lu pour la première fois. Cela se produit souvent quand ces nombres sont utilisés comme des masques de bits ou un autre élément symbolique plutôt que comme des valeurs numériques. C# 7 comprend deux nouvelles fonctionnalités permettant de faciliter l’écriture de nombres de la manière la plus lisible pour l’utilisation prévue : les *littéraux binaires* et les *séparateurs de chiffres*.

Dans les cas où vous créez des masques de bits chaque fois qu’une représentation binaire d’un nombre rend le code plus lisible, écrivez ce nombre au format binaire :

[!code-csharp[BinaryConstants](../../../samples/snippets/csharp/new-in-7/Program.cs#32_BinaryConstants "Binary constants")]

Le `0b` au début de la constante indique que le nombre est écrit sous la forme d’un nombre binaire.

Les nombres binaires peuvent être très longs. Il est donc souvent plus facile de voir les modèles de bits en introduisant le `_` comme séparateur de chiffres :

[!code-csharp[ThousandSeparators](../../../samples/snippets/csharp/new-in-7/Program.cs#33_ThousandSeparators "Thousands separators")]

Le séparateur de chiffres peut apparaître n’importe où dans la constante. Pour les nombres de base 10, il arrive fréquemment qu’il soit utilisé comme séparateur des milliers :

[!code-csharp[LargeIntegers](../../../samples/snippets/csharp/new-in-7/Program.cs#34_LargeIntegers "Large integer")]

Il est possible d’utiliser le séparateur de chiffres également avec les types `decimal`, `float` et `double` :

[!code-csharp[OtherConstants](../../../samples/snippets/csharp/new-in-7/Program.cs#35_OtherConstants "non-integral constants")]

Globalement, vous pouvez déclarer des constantes numériques avec beaucoup plus de lisibilité.
