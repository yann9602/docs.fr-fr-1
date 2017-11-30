---
title: "Quelles sont les nouveautés en c# 6 - Guide c#"
description: "Découvrez les nouvelles fonctionnalités de C# version 6"
keywords: .NET, .NET Core
author: BillWagner
ms.date: 09/22/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 4d879f69-f889-4d3f-a781-75194e143400
ms.openlocfilehash: f3e7a515b1dde52461ab6abf8a9adbe84d27b7c1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="whats-new-in-c-6"></a>Nouveautés de C# 6

La version Release 6.0 de C# comprenait de nombreuses fonctionnalités qui améliorent la productivité des développeurs. Cette version inclut les fonctionnalités suivantes :

* [Auto-properties en lecture seule](#read-only-auto-properties) :
    - Vous pouvez créer des auto-properties en lecture seule qui ne peuvent être définies que dans des constructeurs.
* [Initialiseurs d’auto-properties](#auto-property-initializers) :
    - Vous pouvez écrire des expressions d’initialisation pour définir la valeur initiale d’une auto-property.
* [Membres de fonction expression-bodied](#expression-bodied-function-members) :
    - Vous pouvez créer des méthodes d’une ligne à l’aide d’expressions lambda.
* [using static](#using-static) :
    - Vous pouvez importer toutes les méthodes d’une classe unique dans l’espace de noms actuel.
* [Null - Opérateurs conditionnels](#null-conditional-operators) :
    - Vous pouvez accéder avec concision et en toute sécurité aux membres d’un objet tout en recherchant les valeurs null avec l’opérateur conditionnel null.
* [Interpolation de chaîne](#string-interpolation) :
    - Vous pouvez écrire des expressions de mise en forme de chaînes à l’aide d’expressions inline plutôt que d’arguments de position.
* [Filtres d’exception](#exception-filters) :
    - Vous pouvez intercepter des expressions en fonction de propriétés de l’exception ou de l’état d’un autre programme. 
* [Expressions nameof](#nameof-expressions) :
    - Vous pouvez laisser le compilateur générer des représentations de symboles sous forme de chaîne.
* [await dans des blocs catch et finally](#await-in-catch-and-finally-blocks) :
    - Vous pouvez utiliser des expressions `await` dans des emplacements qui ne les autorisaient pas auparavant.
* [Initialiseurs d’index](#index-initializers) :
    - Vous pouvez créer des expressions d’initialisation pour les conteneurs associatifs, ainsi que des conteneurs de séquence.
* [Méthodes d’extension pour les initialiseurs de collections](#extension-add-methods-in-collection-initializers) :
    - Les initialiseurs de collections peuvent s’appuyer sur des méthodes d’extension accessibles, en plus des méthodes membres.
* [Résolution de surcharge améliorée](#improved-overload-resolution) :
    - Certaines constructions qui généraient auparavant des appels de méthode ambigus sont désormais résolues correctement.

Globalement, ces fonctionnalités vous permettent d’écrire du code plus concis et également plus lisible. La syntaxe est moins formelle concernant de nombreuses pratiques courantes. Moins de formalisme permet de voir plus facilement l’intention de conception. En maîtrisant ces fonctionnalités, vous serez plus productif, vous écrirez du code plus lisible et vous vous concentrerez davantage sur vos fonctionnalités principales que sur les constructions du langage.

Le reste de cette rubrique fournit des détails sur chacune de ces fonctionnalités.

## <a name="auto-property-enhancements"></a>Améliorations des auto-properties 

La syntaxe des propriétés implémentées automatiquement (généralement appelées "auto-properties") permettait de créer très facilement des propriétés qui avaient des accesseurs get et set simples :

[!code-csharp[ClassicAutoProperty](../../../samples/snippets/csharp/new-in-6/oldcode.cs#ClassicAutoProperty)]

Toutefois, cette syntaxe simple limitait les types de conceptions que vous pouviez prendre en charge à l’aide d’auto-properties. C# 6 améliore les fonctionnalités des auto-properties afin de vous permettre de les exécuter dans un plus grand nombre de scénarios. Vous n’aurez pas besoin de fréquemment revenir manuellement sur la syntaxe plus détaillée de la déclaration et de la manipulation du champ de stockage.

La nouvelle syntaxe répond à des scénarios pour les propriétés en lecture seule et pour l’initialisation de la variable stockage derrière une propriété automatique.

### <a name="read-only-auto-properties"></a>Auto-properties en lecture seule

Les *auto-properties en lecture seule* offrent une syntaxe plus concise pour créer des types immuables. Dans les versions antérieures de C#, déclarer les méthodes Set privées permettait de vous rapprocher le plus de types immuables :

[!code-csharp[ClassicReadOnlyAutoProperty](../../../samples/snippets/csharp/new-in-6/oldcode.cs#ClassicReadOnlyAutoProperty)]
 
En utilisant cette syntaxe, le compilateur ne garantit pas que le type soit vraiment immuable. Il garantit seulement que les propriétés `FirstName` et `LastName` ne sont pas modifiées à partir de code en dehors de la classe.

Les auto-properties en lecture seule permettent un véritable comportement en lecture seule. Vous déclarez l’auto-property avec uniquement un accesseur get :

[!code-csharp[ReadOnlyAutoProperty](../../../samples/snippets/csharp/new-in-6/newcode.cs#ReadOnlyAutoProperty)]

Les propriétés `FirstName` et `LastName` peuvent être définies uniquement dans le corps d’un constructeur :

[!code-csharp[ReadOnlyAutoPropertyConstructor](../../../samples/snippets/csharp/new-in-6/newcode.cs#ReadOnlyAutoPropertyConstructor)]

Tenter de définir `LastName` dans une autre méthode génère une erreur de compilation `CS0200` :

```csharp
public class Student
{
    public string LastName { get;  }

    public void ChangeName(string newLastName)
    {
        // Generates CS0200: Property or indexer cannot be assigned to -- it is read only
        LastName = newLastName;
    }
}
```

Cette fonctionnalité permet une véritable prise en charge du langage pour la création de types immuables et l’utilisation de la syntaxe d’auto-property plus concise et plus pratique.

### <a name="auto-property-initializers"></a>Initialiseurs d’auto-properties

Les *initialiseurs d’auto-properties* vous permettent de déclarer la valeur initiale d’une auto-property dans le cadre de la déclaration de la propriété.  Dans les versions antérieures, ces propriétés devaient avoir des méthodes setter que vous deviez utiliser pour initialiser le stockage de données utilisé par le champ de stockage. Étudions la classe suivante pour un étudiant. Elle contient le nom et la liste des diplômes de ce dernier :

[!code-csharp[Construction](../../../samples/snippets/csharp/new-in-6/oldcode.cs#Construction)]
 
À mesure que cette classe augmente, vous pouvez inclure d’autres constructeurs. Chaque constructeur doit initialiser ce champ, sans quoi vous introduirez des erreurs.

C# 6 vous permet d’assigner une valeur initiale pour le stockage utilisé par une auto-property dans la déclaration de l’auto-property :

[!code-csharp[Initialization](../../../samples/snippets/csharp/new-in-6/newcode.cs#Initialization)]

Le membre `Grades` est initialisé à l’emplacement où il est déclaré. Il est ainsi plus facile d’effectuer l’initialisation une seule fois. L’initialisation fait partie de la déclaration de propriété, facilitant ainsi la mise en correspondance de l’allocation de stockage et de l’interface publique pour les objets `Student`.

Initialiseurs de propriété peuvent être utilisés avec les propriétés en lecture/écriture, ainsi que les propriétés en lecture seule, comme indiqué ici.

[!code-csharp[ReadWriteInitialization](../../../samples/snippets/csharp/new-in-6/newcode.cs#ReadWriteInitialization)]

## <a name="expression-bodied-function-members"></a>Membres de fonction expression-bodied

Le corps de beaucoup de membres que nous écrivons se compose d’une seule instruction qui peut être représentée sous la forme d’une expression. Vous pouvez réduire cette syntaxe en écrivant un membre expression-bodied à la place. Il fonctionne pour les méthodes et propriétés en lecture seule. Par exemple, une substitution de `ToString()` est souvent un excellent candidat :

[!code-csharp[ToStringExpressionMember](../../../samples/snippets/csharp/new-in-6/newcode.cs#ToStringExpressionMember)]

Vous pouvez également utiliser des membres de l’expression-pulvérisés dans les propriétés en lecture seule :

[!code-csharp[FullNameExpressionMember](../../../samples/snippets/csharp/new-in-6/newcode.cs#FullNameExpressionMember)]

## <a name="using-static"></a>using static

L’amélioration de *using static* vous permet d’importer les méthodes statiques d’une classe unique. Auparavant, l’instruction `using` importait tous les types d’un espace de noms. 

Souvent, nous utilisons les méthodes statiques d’une classe dans notre code. Saisir de manière répétée le nom de classe peut nuire à la visibilité de la signification de votre code. C’est souvent le cas quand vous écrivez des classes qui effectuent de nombreux calculs numériques.
Votre code sera encombré de <xref:System.Math.Sin%2A>, de <xref:System.Math.Sqrt%2A> et d’autres appels à différentes méthodes de la classe <xref:System.Math>. La nouvelle syntaxe `using static` clarifie considérablement la lecture de ces classes. Vous spécifiez la classe que vous utilisez :

[!code-csharp[UsingStaticMath](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStaticMath)]

Vous pouvez maintenant utiliser n’importe quelle méthode statique de la classe <xref:System.Math> sans qualifier la classe <xref:System.Math>. La classe <xref:System.Math> est un excellent cas d’usage de cette fonctionnalité, car elle ne contient aucune méthode d’instance. Vous pouvez également utiliser `using static` pour importer les méthodes statiques d’une classe pour une classe qui comprend à la fois des méthodes statiques et des méthodes d’instance. Un des exemples plus utiles est <xref:System.String>:

[!code-csharp[UsingStatic](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStatic)]

> [!NOTE]
> Vous devez utiliser le nom de classe complet, `System.String`, dans une instruction static using. Vous ne pouvez pas utiliser le mot clé `string` à la place. 

Vous pouvez maintenant appeler des méthodes statiques définies dans la classe <xref:System.String> sans qualifier ces méthodes comme membres de cette classe :

[!code-csharp[UsingStaticString](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStaticString)]

La fonctionnalité `static using` et les méthodes d’extension interagissent de façons intéressantes, et la conception du langage comprenait des règles qui traitent spécifiquement ces interactions. L’objectif est de réduire les risques de changements importants dans des codes base existants, dont les vôtres.

Les méthodes d’extension sont dans la portée uniquement quand elles sont appelées à l’aide de la syntaxe d’invocation de méthode d’extension, et pas quand elles sont appelées en tant que méthode statique.
Ce sera souvent le cas dans les requêtes LINQ. Vous pouvez importer le modèle LINQ en important <xref:System.Linq.Enumerable>.

[!code-csharp[UsingStaticLinq](../../../samples/snippets/csharp/new-in-6/newcode.cs#usingStaticLinq)]

Cette opération importe toutes les méthodes de la classe <xref:System.Linq.Enumerable>.
Toutefois, les méthodes d’extension sont dans la portée uniquement quand elles sont appelées en tant que méthodes d’extension. Elles ne sont pas dans la portée si elles sont appelées à l’aide de la syntaxe de méthode statique :

[!code-csharp[UsingStaticLinqMethod](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStaticLinkMethod)]

Cette décision est justifiée par le fait que les méthodes d’extension sont généralement appelées à l’aide d’expressions d’invocation de méthode d’extension. Il existe de rares cas où elles sont appelées à l’aide de la syntaxe d’appel de méthode statique, dans le but de résoudre une ambiguïté.
Il semble judicieux d’exiger le nom de la classe dans le cadre de l’invocation.

`static using` comprend une dernière fonctionnalité. La directive `static using` importe également n’importe quel type imbriqué. Cela vous permet de référencer tout type imbriqué sans qualification.

## <a name="null-conditional-operators"></a>Null - Opérateurs conditionnel

Les valeurs null compliquent le code. Vous devez vérifier chaque accès de variables afin de garantir que vous ne déréférencez pas `null`. L’*opérateur conditionnel null* rend ces contrôles beaucoup plus faciles et plus fluides.

Remplacez simplement l’accès aux membres `.` par `?.` :

[!code-csharp[NullConditional](../../../samples/snippets/csharp/new-in-6/program.cs#NullConditional)]

Dans l’exemple précédent, la valeur `null` est assignée à la variable `first` si l’objet person a la valeur `null`. Sinon, la valeur de la propriété `FirstName` lui est assignée. Plus important encore, le `?.` signifie que cette ligne de code ne génère pas de `NullReferenceException` quand la variable `person` a la valeur `null`. Au lieu de cela, elle court-circuite et produit `null`.

Notez également que cette expression retourne un `string`, quelle que soit la valeur de `person`.
Dans le cas d’un court-circuit, la valeur `null` retournée est typée pour correspondre à l’expression complète.

Vous pouvez souvent utiliser cette construction avec l’opérateur de *fusion null*  pour assigner des valeurs par défaut quand l’une des propriétés a la valeur `null` :

[!code-csharp[NullCoalescing](../../../samples/snippets/csharp/new-in-6/program.cs#NullCoalescing)]

L’opérande de droite de l’opérateur `?.` n’est pas limité aux propriétés ou aux champs.
Vous pouvez également l’utiliser pour appeler des méthodes de manière conditionnelle. L’utilisation la plus courante de fonctions membres avec l’opérateur conditionnel null consiste à appeler en toute sécurité des délégués (ou des gestionnaires d’événements) qui peuvent avoir la valeur `null`.  Pour ce faire, appelez la méthode `Invoke` du délégué à l’aide de l’opérateur `?.` pour accéder au membre. Vous trouverez un exemple dans la rubrique relative aux  
[modèles de délégués](../delegates-patterns.md#handling-null-delegates).

Les règles de l’opérateur `?.` garantissent que la partie gauche de l’opérateur n’est évalué qu’une seule fois. Cela est important et permet de nombreux idiomes, notamment l’exemple utilisant des gestionnaires d’événements. Commençons par l’utilisation de gestionnaires d’événements. Dans les précédentes versions de C#, vous étiez encouragé à écrire du code semblable à ceci :

```csharp
var handler = this.SomethingHappened;
if (handler != null)
    handler(this, eventArgs);
```

Cela était préférable à une syntaxe plus simple :

```csharp
// Not recommended
if (this.SomethingHappened != null)
    this.SomethingHappened(this, eventArgs);
```

> [!IMPORTANT]
> L’exemple précédent introduit une concurrence critique. L’événement `SomethingHappened` peut avoir des abonnés au moment où il est vérifié pour voir s’il a la valeur `null`, et ces abonnés peuvent avoir été supprimés avant le déclenchement de l’événement. Cela entraînerait la levée d’un <xref:System.NullReferenceException>.

Dans cette deuxième version, le gestionnaire d’événements `SomethingHappened` peut être non null au moment du test, mais si un autre code supprime un gestionnaire, il peut être encore null quand le gestionnaire d’événements a été appelé.

Le compilateur génère du code pour l’opérateur `?.` qui garantit que la partie gauche (`this.SomethingHappened`) de l’expression `?.` n’est évaluée qu’une seule fois, et le résultat est mis en cache :

```csharp
// preferred in C# 6:
this.SomethingHappened?.Invoke(this, eventArgs);
```

Le fait de garantir que la partie gauche n’est évaluée qu’une seule fois vous permet également d’utiliser n’importe quelle expression, notamment des appels de méthode, dans la partie gauche de l’expression `?.`. Même si ces expressions ont des effets secondaires, elles ne sont évaluées qu’une seule fois ; les effets secondaires ne se produisent donc qu’une seule fois. Vous trouverez un exemple dans notre contenu relatif aux [événements](../events-overview.md#language-support-for-events).

## <a name="string-interpolation"></a>Interpolation de chaîne

C# 6 contient une nouvelle syntaxe pour la composition de chaînes à partir d’une chaîne de format et des expressions qui peuvent être évaluées pour produire d’autres valeurs de chaîne.

Habituellement, vous deviez utiliser des paramètres de position dans une méthode telle que `string.Format` :

[!code-csharp[stringFormat](../../../samples/snippets/csharp/new-in-6/oldcode.cs#stringFormat)]

Avec C# 6, la nouvelle fonctionnalité d’interpolation de chaîne vous permet d’incorporer des expressions dans la chaîne de format. Faites simplement précéder la chaîne de `$` :

[!code-csharp[stringInterpolation](../../../samples/snippets/csharp/new-in-6/newcode.cs#FullNameExpressionMember)]

Cet exemple initial utilisait des expressions variables pour les expressions substituées. Vous pouvez étendre cette syntaxe pour utiliser n’importe quelle expression. Par exemple, vous pourrez calculer la moyenne pondérée cumulative d’un étudiant dans le cadre de l’interpolation :

[!code-csharp[stringInterpolationExpression](../../../samples/snippets/csharp/new-in-6/newcode.cs#stringInterpolationExpression)]

En exécutant l’exemple précédent, vous pouvez voir que la sortie de `Grades.Average()` peut avoir plus de décimales que vous ne le souhaitez. La syntaxe d’interpolation de chaîne prend en charge toutes les chaînes de format disponibles en utilisant des méthodes de mise en forme précédentes. Vous ajoutez les chaînes de format entre les accolades. Ajoutez un `:` après l’expression à mettre en forme :

[!code-csharp[stringInterpolationFormat](../../../samples/snippets/csharp/new-in-6/newcode.cs#stringInterpolationFormat)]

La ligne de code précédente mettra en forme la valeur de `Grades.Average()` sous la forme d’un nombre à virgule flottante à deux décimales.

Le `:` est toujours interprété comme le séparateur entre l’expression mise en forme et la chaîne de format. Cela peut entraîner des problèmes quand votre expression utilise un `:` d’une autre manière, par exemple comme opérateur conditionnel :

```csharp
public string GetGradePointPercentages() =>
    $"Name: {LastName}, {FirstName}. G.P.A: {Grades.Any() ? Grades.Average() : double.NaN:F2}";
```

Dans l’exemple précédent, le `:` est analysé comme début de la chaîne de format, et non comme partie de l’opérateur conditionnel. Dans tous les cas où cela se produit, vous pouvez mettre l’expression entre parenthèses pour forcer le compilateur à interpréter l’expression comme vous le souhaitez :

[!code-csharp[stringInterpolationConditional](../../../samples/snippets/csharp/new-in-6/newcode.cs#stringInterpolationConditional)]

Aucune limite ne s’applique aux expressions que vous pouvez placer entre accolades. Vous pouvez exécuter une requête LINQ complexe à l’intérieur d’une chaîne interpolée pour effectuer des calculs et afficher le résultat :

[!code-csharp[stringInterpolationLinq](../../../samples/snippets/csharp/new-in-6/newcode.cs#stringInterpolationLinq)]

Dans cet exemple, vous pouvez voir qu’il est même possible d’imbriquer une expression d’interpolation de chaîne à l’intérieur d’une autre expression d’interpolation de chaîne. Cet exemple est très probablement plus complexe que vous ne le souhaiteriez dans le code de production.
En fait, il illustre l’étendue de la fonctionnalité. Toute expression C# peut être placée entre les accolades d’une chaîne interpolée.

### <a name="string-interpolation-and-specific-cultures"></a>Interpolation de chaîne et cultures spécifiques

Tous les exemples présentés dans la section précédente mettront en forme les chaînes à l’aide de la culture et de la langue actuelles sur l’ordinateur sur lequel le code s’exécute. Souvent, vous devrez mettre en forme la chaîne produite à l’aide d’une culture spécifique.
L’objet créé à partir d’une interpolation de chaîne est un type qui a une conversion implicite en <xref:System.String> ou en <xref:System.FormattableString>.

Le type <xref:System.FormattableString> contient la chaîne de format et les résultats de l’évaluation des arguments avant leur conversion en chaînes. Vous pouvez utiliser des méthodes publiques de <xref:System.FormattableString> pour spécifier la culture lors de la mise en forme d’une chaîne. Par exemple, le code suivant produira une chaîne utilisant l’allemand comme langue et culture. (Il utilisera le caractère ',' comme séparateur décimal et le caractère '.' comme séparateur des milliers.)

```csharp
FormattableString str = $"Average grade is {s.Grades.Average()}";
var gradeStr = string.Format(null, 
    System.Globalization.CultureInfo.CreateSpecificCulture("de-de"),
    str.GetFormat(), str.GetArguments());
```

> [!NOTE]
> L’exemple précédent n’est pas pris en charge dans .NET Core version 1.0.1. Il est pris en charge uniquement dans le .NET Framework.

En général, les expressions d’interpolation de chaîne produisent des chaînes comme sortie. Toutefois, si vous souhaitez mieux contrôler la culture utilisée pour mettre en forme la chaîne, vous pouvez spécifier une sortie spécifique.  S’il s’agit d’une fonctionnalité dont vous avez souvent besoin, vous pouvez créer des méthodes pratiques, comme des méthodes d’extension, pour faciliter la mise en forme simple avec des cultures spécifiques.

## <a name="exception-filters"></a>Filtres d’exception

Les *filtres d’exception* constituent une autre nouvelle fonctionnalité en C# 6. Les filtres d’exception sont des clauses qui déterminent quand une clause catch donnée doit être appliquée.
Si l’expression utilisée pour un filtre d’exception prend la valeur `true`, la clause catch effectue son traitement normal sur une exception. Si l’expression prend la valeur `false`, la clause `catch` est ignorée.

Une de leurs utilisations consiste à examiner les informations concernant une exception pour déterminer si une clause `catch` peut la traiter :

[!code-csharp[ExceptionFilter](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#ExceptionFilter)]

Le code généré par les filtres d’exception fournit de meilleures informations concernant une exception qui est levée et non traitée. Avant que des filtres d’exception soient ajoutés au langage, vous deviez créer du code semblable au code suivant :

[!code-csharp[ExceptionFilterOld](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#ExceptionFilterOld)]

Le point où l’exception est levée change entre ces deux exemples.
Dans le code précédent, où une clause `throw` est utilisée, toute analyse de trace de pile ou tout examen de vidages sur incident montrera que l’exception a été levée à partir de l’instruction `throw` dans votre clause catch. L’objet exception réel contiendra la pile des appels d’origine, mais toutes les autres informations relatives aux variables de la pile des appels entre ce point de levée et l’emplacement du point de levée d’origine ont été perdues. 

Comparez cela à la façon dont le code qui utilise un filtre d’exception est traité : l’expression de filtre d’exception prend la valeur `false`. Par conséquent, l’exécution n’entre jamais dans la clause `catch`. Étant donné que la clause `catch` ne s’exécute pas, aucun déroulement de pile n’a lieu. Cela signifie que l’emplacement de levée d’origine est conservé pour toutes les activités de débogage qui se produiront ultérieurement.

Chaque fois que vous avez besoin d’évaluer des champs ou des propriétés d’une exception, au lieu de vous appuyer uniquement sur le type d’exception, utilisez un filtre d’exception pour conserver davantage d’informations de débogage.

Une autre pratique recommandée avec des filtres d’exception consiste à les utiliser pour les routines de journalisation. Cette utilisation profite également de la manière dont le point de levée de l’exception est conservé quand un filtre d’exception prend la valeur `false`.

Une méthode de journalisation est une méthode dont l’argument est l’exception qui retourne `false` sans condition :

[!code-csharp[ExceptionFilterLogging](../../../samples/snippets/csharp/new-in-6/ExceptionFilterHelpers.cs#ExceptionFilterLogging)]

Chaque fois que vous voulez journaliser une exception, vous pouvez ajouter une clause catch et utiliser cette méthode comme filtre d’exception :

[!code-csharp[LogException](../../../samples/snippets/csharp/new-in-6/program.cs#LogException)]

Les exceptions ne sont jamais interceptées, car la méthode `LogException` retourne toujours `false`. Ce filtre d’exception qui a toujours la valeur false signifie que vous pouvez placer ce gestionnaire de journalisation avant tous les autres gestionnaires d’exceptions :

[!code-csharp[LogExceptionRecovery](../../../samples/snippets/csharp/new-in-6/program.cs#LogExceptionRecovery)]

L’exemple précédent met en évidence une facette très importante des filtres d’exception.
Ces derniers autorisent les scénarios où une clause catch d’exception plus générale peut apparaître avant une clause plus spécifique. Il est également possible que le même type d’exception apparaisse dans plusieurs clauses catch :

[!code-csharp[HandleNotChanged](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#HandleNotChanged)]

Une autre pratique recommandée empêche que les clauses catch traitent les exceptions quand un débogueur est attaché. Cette technique vous permet d’exécuter une application avec le débogueur, et d’arrêter son exécution quand une exception est levée.

Dans votre code, ajoutez un filtre d’exception afin que tout code de récupération s’exécute uniquement quand un débogueur n’est pas attaché :

[!code-csharp[LogExceptionDebugger](../../../samples/snippets/csharp/new-in-6/program.cs#LogExceptionDebugger)]

Après avoir ajouté cela au code, vous configurez votre débogueur pour qu’il s’arrête sur toutes les exceptions non prises en charge. Exécutez le programme sous le débogueur. Ce dernier s’arrête chaque fois que `PerformFailingOperation()` lève un `RecoverableException`.
Le débogueur arrête votre programme, car la clause catch ne sera pas exécutée en raison du filtre d’exception qui retourne false.

## <a name="nameof-expressions"></a>Expressions `nameof`

L’expression `nameof` prend comme valeur le nom d’un symbole. C’est un très bon moyen d’obtenir les outils fonctionnant chaque fois que vous avez besoin du nom d’une variable, d’une propriété ou d’un champ de membre.

L’une des utilisations les plus courantes de `nameof` est la fourniture du nom d’un symbole qui a provoqué une exception :

[!code-csharp[nameof](../../../samples/snippets/csharp/new-in-6/NewCode.cs#UsingStaticString)]

Une autre utilisation concerne les applications XAML qui implémentent l’interface `INotifyPropertyChanged` :

[!code-csharp[nameofNotify](../../../samples/snippets/csharp/new-in-6/viewmodel.cs#nameofNotify)]

L’avantage d’utiliser l’opérateur `nameof` sur une chaîne constante est que les outils peuvent comprendre le symbole. Si vous utilisez des outils de refactorisation pour renommer le symbole, il sera renommé dans l’expression `nameof`. Les chaînes constantes ne présentent pas cet avantage. Faites vous-même l’essai dans votre éditeur préféré : renommez une variable ; toutes les expressions `nameof` se mettront également à jour.

L’expression `nameof` produit le nom non qualifié de son argument (`LastName` dans les exemples précédents), même si vous utilisez le nom complet de l’argument :

[!code-csharp[QualifiedNameofNotify](../../../samples/snippets/csharp/new-in-6/viewmodel.cs#QualifiedNameofNotify)]

Cette expression `nameof` produit `FirstName`, et non pas `UXComponents.ViewModel.FirstName`.

## <a name="await-in-catch-and-finally-blocks"></a>await dans des blocs catch et finally

C# 5 présentait plusieurs restrictions concernant les emplacements où vous pouviez placer des expressions `await`.
L’une de ces restrictions a été supprimée dans C# 6. Vous pouvez maintenant utiliser `await` dans des expressions `catch` ou `finally`. 

L’ajout d’expressions await dans des blocs catch et finally peut sembler compliquer la façon dont elles sont traitées. Ajoutons un exemple pour étudier comment cela se présente. Dans n’importe quelle méthode asynchrone, vous pouvez utiliser une expression await dans une clause finally.

Avec C# 6, vous pouvez également utiliser await dans des expressions catch. C’est le plus souvent le cas avec les scénarios de journalisation :

[!code-csharp[AwaitFinally](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#AwaitFinally)]

Les informations d’implémentation détaillées de l’ajout de la prise en charge d’`await` dans des clauses `catch` et `finally` garantissent que le comportement est cohérent avec le comportement du code synchrone. Quand le code exécuté dans une clause `catch` ou `finally` est déclenché, l’exécution recherche une clause `catch` appropriée dans le bloc voisin suivant. S’il existait une exception actuelle, elle est perdue. Il en va de même pour les expressions await dans les clauses `catch` et `finally` : une clause `catch` appropriée est recherchée, et l’exception actuelle, le cas échéant, est perdue.  

> [!NOTE]
> De ce fait, il est recommandé d’écrire les clauses `catch` et `finally` avec précaution, afin d’éviter d’introduire de nouvelles exceptions.

## <a name="index-initializers"></a>Initialiseurs d’index.

Les *initialiseurs d’index* constituent l’une des deux fonctionnalités qui améliorent la cohérence des initialiseurs. Dans les versions Release précédentes de C#, vous ne pouviez utiliser des *initialiseurs de collection* qu’avec des collections de styles de séquence :

[!code-csharp[ListInitializer](../../../samples/snippets/csharp/new-in-6/initializers.cs#ListInitializer)]

À présent, vous pouvez également les utiliser avec des collections <xref:System.Collections.Generic.Dictionary%602> et des types similaires :

[!code-csharp[DictionaryInitializer](../../../samples/snippets/csharp/new-in-6/initializers.cs#DictionaryInitializer)]

Cette fonctionnalité signifie que les conteneurs associatifs peuvent être initialisés à l’aide d’une syntaxe similaire à ce qui a été mis en place pour les conteneurs de séquence depuis plusieurs versions.

### <a name="extension-add-methods-in-collection-initializers"></a>Méthodes `Add` d’extension dans des initialiseurs de collections

La possibilité d’utiliser une *méthode d’extension* pour la méthode `Add` constitue une autre fonctionnalité qui simplifie l’initialisation des collections. Elle a été ajoutée à des fins de parité avec Visual Basic. 

Cette fonctionnalité est particulièrement utile pour ajouter sémantiquement de nouveaux éléments quand vous avez une classe de collection personnalisée dont une méthode porte un nom différent.

Prenons, par exemple, une collection d’étudiants telle que la suivante :

[!code-csharp[Enrollment](../../../samples/snippets/csharp/new-in-6/enrollment.cs#Enrollment)]

La méthode `Enroll` ajoute un étudiant. Mais elle ne suit pas le modèle `Add`.
Dans les versions antérieures de C#, vous ne pouviez pas utiliser d’initialiseurs de collections avec un objet `Enrollment` :

[!code-csharp[InitializeEnrollment](../../../samples/snippets/csharp/new-in-6/classList.cs#InitializeEnrollment)]

C’est maintenant possible, mais uniquement si vous créez une méthode d’extension qui mappe `Add` à `Enroll` :

[!code-csharp[ExtensionAdd](../../../samples/snippets/csharp/new-in-6/classList.cs#ExtensionAdd)]

En utilisant cette fonctionnalité, vous mappez toute méthode ajoutant des éléments à une collection à une méthode nommée `Add` en créant une méthode d’extension : 

[!code-csharp[Enrollment](../../../samples/snippets/csharp/new-in-6/enrollment.cs#Enrollment)]
[!code-csharp[ExtensionAddSample](../../../samples/snippets/csharp/new-in-6/classList.cs#ExtensionAddSample)]

## <a name="improved-overload-resolution"></a>Résolution de surcharge améliorée

Il est probable que vous ne remarquerez pas cette dernière fonctionnalité. La précédente version du compilateur C# pouvait trouver, dans certaines constructions, des appels de méthode impliquant des expressions lambda ambigües. Prenons la méthode suivante :

[!code-csharp[AsyncMethod](../../../samples/snippets/csharp/new-in-6/overloads.cs#AsyncMethod)]

Dans les versions antérieures de C#, l’appel de cette méthode à l’aide de la syntaxe de groupe de méthodes échouait :

[!code-csharp[MethodGroup](../../../samples/snippets/csharp/new-in-6/overloads.cs#MethodGroup)]
 
Le précédent compilateur ne pouvait pas faire correctement la distinction entre `Task.Run(Action)` et `Task.Run(Func<Task>())`. Dans les versions précédentes, vous deviez utiliser une expression lambda comme argument :

[!code-csharp[Lambda](../../../samples/snippets/csharp/new-in-6/overloads.cs#Lambda)]

Le compilateur C# 6 détermine correctement que `Task.Run(Func<Task>())` constitue un meilleur choix.
