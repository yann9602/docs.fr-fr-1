---
title: Utilisation de LINQ
description: "Ce didacticiel vous apprend à générer des séquences avec LINQ, à écrire des méthodes pour les requêtes LINQ et à faire la distinction entre l’évaluation stricte et l’évaluation paresseuse."
keywords: .NET, .NET Core
author: BillWagner
ms.author: wiwagn
ms.date: 03/28/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 0db12548-82cb-4903-ac88-13103d70aa77
ms.openlocfilehash: ec86c558b9aa9c6269fcf9890978f61a934c081f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="working-with-linq"></a>Utilisation de LINQ

## <a name="introduction"></a>Introduction

Ce didacticiel vous présente un certain nombre de fonctionnalités de .NET Core et du langage C#. Vous apprendrez à :

*   générer des séquences avec LINQ ;
*   écrire des méthodes utilisables dans des requêtes LINQ ;
*   faire la distinction entre l’évaluation stricte et l’évaluation paresseuse.

Vous apprendrez ces techniques en créant une application qui illustre l’une des compétences de base de tout magicien : le [mélange faro](https://en.wikipedia.org/wiki/Faro_shuffle). En quelques mots, le mélange faro est une technique qui consiste à diviser un paquet de cartes en deux moitiés exactes, puis à intercaler une carte sur deux de chacune des deux moitiés de façon à reconstruire le jeu d’origine.

Les magiciens utilisent cette technique parce que chaque carte se trouve à un emplacement connu après chaque mélange, suivant un motif répétitif. 

Dans notre cas, c’est une façon plaisante d’envisager la manipulation de séquences de données. L’application que vous allez créer construira un jeu de cartes, puis effectuera une suite de mélanges, en affichant la séquence à chaque fois. Vous comparerez également le nouvel ordre à l’ordre d’origine.

Ce didacticiel comporte plusieurs étapes. Après chaque étape, vous pourrez exécuter l’application et voir la progression. Vous pouvez également voir l’[exemple terminé](https://github.com/dotnet/docs/blob/master/samples/csharp/getting-started/console-linq) dans le dépôt GitHub dotnet/doc. Pour obtenir des instructions de téléchargement, consultez [Exemples et didacticiels](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

## <a name="prerequisites"></a>Prérequis

Vous devez configurer votre ordinateur pour exécuter .NET Core. Vous trouverez les instructions d’installation sur la page [.NET Core](https://www.microsoft.com/net/core). Vous pouvez exécuter cette application sous Windows, Ubuntu Linux, OS X ou dans un conteneur Docker. Vous devez installer l’éditeur de code de votre choix. Les descriptions ci-dessous utilisent [Visual Studio Code](https://code.visualstudio.com/), un éditeur open source et multiplateforme. Cependant, vous pouvez utiliser les outils avec lesquels vous êtes le plus à l’aise.

## <a name="create-the-application"></a>Création de l’application

La première étape consiste à créer une nouvelle application. Ouvrez une invite de commandes et créez un nouveau répertoire pour votre application. Réglez-le comme répertoire actuel. Saisissez la commande `dotnet new console` à l’invite. Elle crée les fichiers de démarrage d’une application « Hello World » de base.

Si vous n’avez jamais utilisé C#, [ce didacticiel](console-teleprompter.md) explique la structure d’un programme C#. Vous pouvez le lire, puis revenir ici pour en savoir plus sur LINQ. 

## <a name="creating-the-data-set"></a>Création du jeu de données

Commençons par créer un jeu de cartes. Vous allez pour cela utiliser une requête LINQ qui a deux sources (l’une pour les quatre couleurs, l’autre pour les treize valeurs). Vous combinerez ces sources de façon à produire un jeu de 52 cartes. Une instruction `Console.WriteLine` à l’intérieur d’une boucle `foreach` affiche les cartes.

Voici la requête :

```csharp
var startingDeck = from s in Suits()
                   from r in Ranks()
                   select new { Suit = s, Rank = r };

foreach (var c in startingDeck)
{
    Console.WriteLine(c);
}
```

Les clauses `from` multiples produisent un `SelectMany`, qui crée une séquence unique en combinant chaque élément de la première séquence avec chaque élément de la deuxième séquence. L’ordre est important ici. Le premier élément de la première séquence source (couleurs) est associé à chacun des éléments de la deuxième séquence (valeurs). Cette opération génère les treize cartes de la première couleur. Ce processus est reproduit pour chaque élément de la première séquence (couleurs). Le résultat final est un jeu de cartes classé par couleurs, puis par valeurs.

Vous devrez ensuite créer les méthodes Suits() et Ranks(). Commençons par un ensemble très simple de *méthodes d’itération* qui génèrent la séquence sous la forme d’une collection énumérable de chaînes :

```csharp
static IEnumerable<string> Suits()
{
    yield return "clubs";
    yield return "diamonds";
    yield return "hearts";
    yield return "spades";
}

static IEnumerable<string> Ranks()
{
    yield return "two";
    yield return "three";
    yield return "four";
    yield return "five";
    yield return "six";
    yield return "seven";
    yield return "eight";
    yield return "nine";
    yield return "ten";
    yield return "jack";
    yield return "queen";
    yield return "king";
    yield return "ace";
}
```

Les deux méthodes utilisent la syntaxe `yield return` pour produire une séquence lors de leur exécution. Le compilateur génère un objet qui implémente `IEnumerable<T>` et génère la séquence de chaînes au fur et à mesure.

Ensuite, exécutez l’exemple que vous avez commencé à élaborer. Il affiche les 52 cartes du jeu. Il peut être très utile d’exécuter cet exemple avec un débogueur pour observer la façon dont les méthodes `Suits()` et `Values()` s’exécutent. Vous pouvez clairement voir que chaque chaîne de chaque séquence est générée uniquement au moment requis.

![Fenêtre console montrant l’application produisant les 52 cartes](./media/working-with-linq/console.png)

## <a name="manipulating-the-order"></a>Manipulation de l’ordre

Ensuite, nous allons créer une méthode utilitaire pour effectuer le mélange. La première étape consiste à couper le jeu en deux. Les méthodes `Take()` et `Skip()`, qui font partie de l’API LINQ, nous fournissent cette fonctionnalité :

```csharp
var top = startingDeck.Take(26);
var bottom = startingDeck.Skip(26);
```

La méthode de mélange n’existe pas dans la bibliothèque standard ; vous devez donc écrire la vôtre. Cette nouvelle méthode illustre plusieurs techniques que vous allez utiliser avec des programmes LINQ. Nous allons expliquer les différentes parties de la méthode au fil des étapes.

La signature de la méthode crée une *méthode d’extension* :

```csharp
public static IEnumerable<T> InterleaveSequenceWith<T>
    (this IEnumerable<T> first, IEnumerable<T> second)
```

Une méthode d’extension est une *méthode statique* qui répond à un objectif spécifique. On peut voir l’ajout du modificateur `this` au premier argument de la méthode. Cela signifie que vous appelez la méthode comme s’il s’agissait d’une méthode membre du type du premier argument.

Les méthodes d’extension ne peuvent être déclarées qu’à l’intérieur de classes `static` : nous allons donc créer une nouvelle classe statique appelée `extensions` pour cette fonctionnalité. Vous ajouterez d’autres méthodes d’extension au fur et à mesure de ce didacticiel, et toutes seront placées dans la même classe.

Cette déclaration de méthode suit également un idiome standard selon lequel les types d’entrée et de sortie sont `IEnumerable<T>`. Cette pratique permet d’enchaîner les méthodes LINQ afin d’exécuter des requêtes plus complexes.

```csharp
using System.Collections.Generic;

namespace LinqFaroShuffle
{
    public static class Extensions
    {
        public static IEnumerable<T> InterleaveSequenceWith<T>
            (this IEnumerable<T> first, IEnumerable<T> second)
        {
            // implementation coming.
        }
    }
}
```

Vous allez énumérer les deux séquences à la fois, en intercalant les éléments et en créant un seul objet.  Pour écrire une méthode LINQ qui fonctionne avec deux séquences, vous devez comprendre comment `IEnumerable` fonctionne.

L’interface `IEnumerable` possède une seule méthode : `GetEnumerator()`. L’objet retourné par `GetEnumerator()` a une méthode permettant d’atteindre l’élément suivant et une propriété qui récupère l’élément actif dans la séquence. Vous allez utiliser ces deux membres pour énumérer la collection et retourner les éléments. Cette méthode Interleave sera une méthode d’itération ; par conséquent, au lieu de créer une collection et de la retourner, vous allez utiliser la syntaxe `yield return` présentée ci-dessus. 

Voici l’implémentation de cette méthode :

[!CODE-csharp[InterleaveSequenceWith](../../../samples/csharp/getting-started/console-linq/extensions.cs?name=snippet1)]

Maintenant que vous avez écrit cette méthode, revenez à la méthode `Main` et mélangez le jeu une fois :

```csharp
public static void Main(string[] args)
{
    var startingDeck = from s in Suits()
                       from r in Ranks()
                       select new { Suit = s, Rank = r };

    foreach (var c in startingDeck)
    {
        Console.WriteLine(c);
    }
        
    var top = startingDeck.Take(26);
    var bottom = startingDeck.Skip(26);
    var shuffle = top.InterleaveSequenceWith(bottom);

    foreach (var c in shuffle)
    {
        Console.WriteLine(c);
    }
}
```

## <a name="comparisons"></a>Comparaisons

Nous allons voir combien de mélanges sont nécessaires pour remettre le jeu dans l’ordre d’origine. Vous devrez écrire une méthode qui détermine si deux séquences sont égales. Ensuite, il vous faudra placer le code qui mélange le jeu dans une boucle et vérifier si le jeu est de nouveau dans l’ordre.

Vous ne devriez pas avoir de problèmes à écrire une méthode qui détermine si deux séquences sont égales. La structure est similaire à celle de la méthode que vous avez écrite pour mélanger le jeu. Seulement, cette fois, au lieu de retourner chaque élément, vous allez comparer les éléments correspondants de chaque séquence. Une fois que la séquence aura été énumérée en entier, si tous les éléments correspondent, les séquences sont les mêmes :

[!CODE-csharp[SequenceEquals](../../../samples/csharp/getting-started/console-linq/extensions.cs?name=snippet2)]

Cet exemple montre un autre idiome Linq : les méthodes terminales. Elles prennent une séquence en entrée (ou, dans ce cas, deux séquences) et retournent une valeur scalaire unique. Ces méthodes, lorsqu’elles sont utilisées, sont toujours les dernières méthodes d’une requête. (D’où leur nom.) 

Vous pourrez les voir en action lorsque vous les utiliserez pour déterminer si le jeu est dans l’ordre d’origine. Placez le code de mélange à l’intérieur d’une boucle, et arrêtez-la lorsque la séquence est à nouveau dans l’ordre d’origine en appliquant la méthode `SequenceEquals()`. Vous pouvez voir qu’il s’agit toujours de la dernière méthode d’une requête, parce qu’elle retourne une valeur unique plutôt qu’une séquence :

```csharp
var times = 0;
var shuffle = startingDeck;

do
{
    shuffle = shuffle.Take(26).InterleaveSequenceWith(shuffle.Skip(26));

    foreach (var c in shuffle)
    {
        Console.WriteLine(c);
    }

    Console.WriteLine();
    times++;
} while (!startingDeck.SequenceEquals(shuffle));

Console.WriteLine(times);
```

Exécutez l’exemple, et regardez comment le jeu se réorganise à chaque mélange, jusqu’à ce qu’il revienne à sa configuration d’origine après huit itérations.

## <a name="optimizations"></a>Optimisations

L’exemple que vous avez produit jusque-là exécute un *mélange intérieur*, où les cartes du haut et du bas restent les mêmes à chaque exécution. Faisons une modification, et exécutons un *mélange extérieur*, où les 52 cartes changent toutes de position. Dans le cas d’un mélange extérieur, on intercale les deux moitiés du jeu de sorte que la première carte de la moitié du dessous devienne la première carte du jeu. Cela signifie que la dernière carte de la moitié du dessus devient la carte du bas. Il n’y a qu’une ligne à modifier. Mettez à jour l’appel à la fonction de mélange pour modifier l’ordre des moitiés du dessus et du dessous du jeu :

```csharp
shuffle = shuffle.Skip(26).InterleaveSequenceWith(shuffle.Take(26));
```

Réexécutez le programme : vous verrez qu’il faut 52 itérations pour que le jeu se réorganise. Vous commencerez également à remarquer de sérieuses dégradations des performances lors de l’exécution du programme.

Il y a plusieurs raisons à cela. Attaquons-nous à l’une des causes principales : l’utilisation inefficace de *l’évaluation paresseuse*.

Les requêtes LINQ sont évaluées de façon retardée. Les séquences sont générées uniquement au moment où les éléments sont demandés. En règle générale, c’est un avantage majeur de LINQ. Toutefois, dans une utilisation du type de ce programme, cela entraîne une croissance exponentielle de la durée d’exécution.

Le jeu d’origine a été généré à l’aide d’une requête LINQ. Chaque mélange est généré en effectuant trois requêtes LINQ sur le jeu précédent. Toutes ces opérations sont effectuées de façon retardée. Cela signifie également qu’elles sont effectuées à chaque fois que la séquence est demandée. À la 52e itération, vous aurez régénéré le jeu d’origine de nombreuses fois. Nous allons écrire dans un journal pour illustrer ce comportement. Ensuite, vous résoudrez le problème.

Voici une méthode de journalisation qui peut être ajoutée aux requêtes pour marquer la requête exécutée.

[!CODE-csharp[LogQuery](../../../samples/csharp/getting-started/console-linq/extensions.cs?name=snippet3)]

Instrumentez ensuite la définition de chaque requête avec un message de journalisation :

```csharp
public static void Main(string[] args)
{
    var startingDeck = (from s in Suits().LogQuery("Suit Generation")
                        from r in Ranks().LogQuery("Rank Generation")
                        select new { Suit = s, Rank = r }).LogQuery("Starting Deck");

    foreach (var c in startingDeck)
    {
        Console.WriteLine(c);
    }
        
    Console.WriteLine();
    var times = 0;
    var shuffle = startingDeck;

    do
    {
        /*
        shuffle = shuffle.Take(26)
            .LogQuery("Top Half")
            .InterleaveSequenceWith(shuffle.Skip(26)
            .LogQuery("Bottom Half"))
            .LogQuery("Shuffle");
        */

        shuffle = shuffle.Skip(26)
            .LogQuery("Bottom Half")
            .InterleaveSequenceWith(shuffle.Take(26).LogQuery("Top Half"))
            .LogQuery("Shuffle");

        foreach (var c in shuffle)
        {
            Console.WriteLine(c);
        }

        times++;
        Console.WriteLine(times);
    } while (!startingDeck.SequenceEquals(shuffle));

    Console.WriteLine(times);
}
```

Remarquez que vous n’écrivez pas dans le journal à chaque fois que vous accédez à une requête, mais seulement lors de la création de la requête d’origine. Le programme met toujours longtemps à s’exécuter, mais vous pouvez maintenant voir pourquoi. Si vous perdez patience au cours de l’exécution du mélange extérieur avec journalisation, revenez au mélange intérieur. Vous verrez quand même les effets de l’évaluation paresseuse. Sur une itération, elle exécute 2 592 requêtes, génération de toutes les valeurs et couleurs comprise.

Il y a un moyen simple de mettre à jour ce programme afin d’éviter toutes ces exécutions. Les méthodes LINQ `ToArray()` et `ToList()` provoquent l’exécution de la requête et stockent les résultats respectivement dans un tableau ou dans une liste. On utilise ces méthodes pour mettre en cache les données résultant d’une requête plutôt que de réexécuter la requête source.  Ajoutez les requêtes qui génèrent les jeux de cartes avec un appel à `ToArray()` et réexécutez la requête :

[!CODE-csharp[Main](../../../samples/csharp/getting-started/console-linq/Program.cs?name=snippet1)]

Réexécutez-la : le mélange intérieur est descendu à 30 requêtes. Si vous repassez au mélange extérieur, vous constaterez des améliorations similaires. (Il exécute à présent 162 requêtes.)

Ne déduisez pas de cet exemple que toutes les requêtes devraient s’exécuter de façon stricte. Cet exemple est conçu pour mettre en évidence les cas d’usage où l’évaluation paresseuse peut causer des problèmes de performances. La raison en est que chaque nouvelle disposition du jeu de cartes est construite à partir de la configuration précédente. Avec l’évaluation paresseuse, chaque nouvelle configuration du jeu est générée à partir du jeu d’origine, y compris l’exécution du code qui a construit `startingDeck`, ce qui entraîne une grande quantité de travail supplémentaire. 

Dans la pratique, certains algorithmes fonctionnent beaucoup mieux avec l’évaluation stricte, d’autres avec l’évaluation paresseuse. (En général, l’évaluation paresseuse est un bien meilleur choix lorsque la source de données est un processus distinct, comme un moteur de base de données. Dans ce cas, l’évaluation paresseuse permet d’exécuter des requêtes plus complexes avec un seul aller-retour vers le processus de base de données.) LINQ permet à la fois l’évaluation paresseuse et l’évaluation stricte. Évaluez et choisissez la meilleure des deux.

## <a name="preparing-for-new-features"></a>Préparation des nouvelles fonctionnalités

Le code que vous avez écrit pour cet exemple est un prototype simple qui remplit sa fonction. C’est un excellent moyen d’explorer un problème d’espace ; pour de nombreuses fonctionnalités, il s’agit peut-être de la meilleure solution permanente. Vous avez tiré profit des *types anonymes* pour les cartes, et chaque carte est représentée par des chaînes.

Les *types anonymes* présentent de nombreux avantages du point de vue de la productivité. Vous n’avez pas besoin de définir vous-même une classe pour représenter le stockage. Le compilateur génère le type à votre place. Le type généré par le compilateur utilise plusieurs des bonnes pratiques pour les objets de données simples. Il est *non modifiable*, ce qui signifie qu’aucune de ses propriétés ne peut être modifiée une fois qu’il a été construit. Les types anonymes sont internes à un assembly ; ainsi, ils ne sont pas visibles dans le cadre de l’API publique de cet assembly. Les types anonymes contiennent également une substitution de la méthode `ToString()` qui retourne une chaîne mise en forme avec chacune des valeurs.

Les types anonymes présentent également des inconvénients. Ils n’ont pas de nom accessible ; vous ne pouvez donc pas les utiliser comme valeurs renvoyées ou comme arguments. Vous remarquerez que toutes les méthodes ci-dessus qui ont utilisé ces types anonymes sont des méthodes génériques. La substitution de `ToString()` peut ne pas être idéale lorsque l’application gagne en fonctionnalités. 

L’exemple utilise également des chaînes pour la couleur et le rang de chaque carte. C’est un système très ouvert. Le système de type C# peut nous permettre d’améliorer le code, en tirant profit des types `enum` pour ces valeurs.

Commencez par les couleurs. C’est le moment idéal pour utiliser `enum` :

[!CODE-csharp[Suit enum](../../../samples/csharp/getting-started/console-linq/Program.cs?name=snippet2)]

La méthode `Suits()` modifie également le type et l’implémentation :

[!CODE-csharp[Suit IEnumerable](../../../samples/csharp/getting-started/console-linq/Program.cs?name=snippet4)]

Ensuite, effectuez la même modification avec le rang des cartes :

[!CODE-csharp[Rank enum](../../../samples/csharp/getting-started/console-linq/Program.cs?name=snippet3)]

Et la méthode qui les génère :

[!CODE-csharp[Rank IEnumerable](../../../samples/csharp/getting-started/console-linq/Program.cs?name=snippet5)]

En guise de nettoyage final, créons un type pour représenter la carte, au lieu d’utiliser un type anonyme. Les types anonymes sont parfaits comme types légers et locaux ; mais, dans cet exemple, la carte à jouer représente l’un des principaux concepts. Elle doit avoir un type concret.

[!CODE-csharp[PlayingCard](../../../samples/csharp/getting-started/console-linq/playingcard.cs?name=snippet1)]

Ce type utilise des *propriétés en lecture seule implémentées automatiquement* qui sont définies dans le constructeur et ne sont pas modifiées. Il utilise également la nouvelle fonctionnalité *d’interpolation de chaîne*, qui facilite le formatage des chaînes de sortie.

Mettez à jour la requête qui génère le jeu de départ pour qu’elle utilise le nouveau type :

```csharp
var startingDeck = (from s in Suits().LogQuery("Suit Generation")
                    from r in Ranks().LogQuery("Value Generation")
                    select new PlayingCard(s, r))
                    .LogQuery("Starting Deck")
                    .ToArray();
```

Compilez, puis réexécutez-la. La sortie est un peu plus propre, et le code est un peu plus clair et peut être étendu plus facilement.

## <a name="conclusion"></a>Conclusion

Cet exemple vous a montré quelques-unes des méthodes utilisées dans LINQ, comment créer vos propres méthodes, faciles à utiliser avec du code compatible LINQ. Il vous a également montré les différences entre l’évaluation paresseuse et l’évaluation stricte, ainsi que l’impact de cette décision sur les performances.

Vous avez appris une technique de magicien. Les magiciens utilisent le mélange faro pour pouvoir contrôler le déplacement de chaque carte dans le jeu. Dans certains tours, le magicien invite un spectateur à placer une carte au-dessus du jeu et le mélange plusieurs fois, tout en sachant l’emplacement de la carte. D’autres illusions nécessitent que le jeu soit préparé d’une certaine manière. Le magicien prépare le jeu avant de réaliser le tour. Ensuite, il effectue cinq mélanges intérieurs. Sur scène, il peut montrer que le jeu paraît mélangé, le mélanger trois fois de plus et se retrouver avec le jeu organisé de la façon souhaitée.
