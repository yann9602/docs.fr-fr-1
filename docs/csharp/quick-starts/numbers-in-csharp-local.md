---
title: "Guide de démarrage rapide - numéros dans c# : c#"
description: "Découvrir c# en explorant les méthodes, leurs propriétés et les types numériques."
author: billwagner
ms.author: wiwagn
ms.date: 10/31/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.custom: mvc
ms.openlocfilehash: 821cca4ea6d6148410e9b179f05d5b74c4844628
ms.sourcegitcommit: 43c656811dd38a66a6672084c65d10c0cbbf2015
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2017
---
# <a name="numbers-in-c-quick-start"></a>Nombres dans démarrage rapide de c# #

Ce démarrage rapide traite des types de nombres en C# interactivement. Vous allez écrire de petites quantités de code, puis vous allez compiler et exécuter ce code. Le démarrage rapide contient une série de leçons qui explorent des nombres et des opérations mathématiques en c#. Ces leçons présentent les concepts de base du langage C#.

Ce démarrage rapide attend que vous disposiez d’un ordinateur, que vous pouvez utiliser pour le développement. La rubrique .NET [prise en main de 10 minutes](https://www.microsoft.com/net/core) a des instructions pour configurer votre environnement de développement local sur le Mac, PC ou Linux.

## <a name="explore-integer-math"></a>Explorer les mathématiques avec des entiers

Créez un répertoire nommé **numéros-démarrage rapide**. Faites-en le répertoire actuel et exécutez `dotnet new console -n NumbersInCSharp -o .`.

Ouvrez **Program.cs** dans votre éditeur favori, puis remplacez la ligne `Console.Writeline("Hello World!");` par le code suivant :

```csharp
int a = 18;
int b = 6;
int c = a + b;
Console.WriteLine(c);
```

Exécutez ce code en tapant `dotnet run` dans votre fenêtre de commande. 

Vous venez d’observer l’une des opérations mathématiques de base avec des entiers. Le type `int` représente un **entier**, qui peut être positif ou négatif. Vous utilisez le symbole `+` pour effectuer une addition. Les autres opérations mathématiques courantes avec des entiers sont les suivantes :

- `-` pour la soustraction
- `*` pour la multiplication
- `/` pour la division

Commencez par explorer ces différentes opérations. Ajoutez ces lignes après la ligne qui écrit la valeur de `c`:

```csharp
c = a - b;
Console.WriteLine(c);
c = a * b;
Console.WriteLine(c);
c = a / b;
Console.WriteLine(c);
```

Exécutez ce code en tapant `dotnet run` dans votre fenêtre de commande. 
    
Vous pouvez également, si vous le souhaitez, effectuer des essais en réalisant plusieurs opérations mathématiques dans la même ligne. Essayez `c = a + b - 12 * 17;` par exemple. Combinaison de variables et les numéros de constante est autorisée.

> [!TIP]
> Durant votre exploration de C# (ou de tout autre langage de programmation), vous commettrez des erreurs d’écriture du code. Le **compilateur** détectera ces erreurs et vous les signalera. Lorsque la sortie contient des messages d’erreur, examinez attentivement l’exemple de code et le code dans la fenêtre pour afficher les éléments à corriger.
> Cet exercice vous aidera à mieux comprendre la structure du code C#.     

Vous avez terminé la première étape. Avant de passer à la section suivante, déplaçons le code actuel dans une méthode distincte. Cela nous permettra de travailler plus facilement avec un nouvel exemple. Renommez votre méthode `Main` `WorkingWithIntegers` et écrivez une nouvelle méthode `Main` qui appelle `WorkingWithIntegers`. Une fois terminé, votre code doit ressembler au code suivant :

```csharp
using System;

namespace NumbersInCSharp
{
    class Program
    {
        static void WorkingWithIntegers()
        {
            int a = 18;
            int b = 6;
            int c = a + b;
            Console.WriteLine(c);
            c = a - b;
            Console.WriteLine(c);
            c = a * b;
            Console.WriteLine(c);
            c = a / b;
            Console.WriteLine(c);
        }

        static void Main(string[] args)
        {
            WorkingWithIntegers();
        }
    }
}
```

## <a name="explore-order-of-operations"></a>Explorer l’ordre des opérations

Commentez l’appel à `WorkingWithIntegers()`. Il effectue la sortie que moins encombrée lorsque vous travaillez dans cette section :

```csharp
//WorkingWithIntegers();
```

Le `//` démarre un **commentaire** en c#. Les commentaires sont n’importe quel texte que vous souhaitez conserver dans votre code source, mais pas s’exécuter en tant que code. Le compilateur ne génère pas de code exécutable à partir de commentaires.

Le langage C# définit la priorité des différentes opérations mathématiques avec à l’aide de règles cohérentes avec les règles mathématiques que vous avez apprises.
La multiplication et la division ont priorité sur l’addition et la soustraction.
Explorer qui, en ajoutant le code suivant à votre `Main` (méthode) et execuing `dotnet run`:

```csharp
int a = 5;
int b = 4;
int c = 2;
int d = a + b * c;
Console.WriteLine(d);
 ```

La sortie montre que la multiplication est effectuée avant l’addition.

Vous pouvez forcer un ordre différent de l’opération en ajoutant des parenthèses autour de l’opération ou les opérations exécutées en premier. Ajoutez les lignes suivantes et exécutez à nouveau :

```csharp
d = (a  + b) * c;
Console.WriteLine(d);
```

Pratiquez en combinant plusieurs opérations différentes. Ajouter quelque chose comme les lignes suivantes au bas de votre `Main` (méthode). Essayez `dotnet run` à nouveau.

```csharp
d = (a + b) - 6 * c + (12 * 4) / 3 + 12;
Console.WriteLine(d);
```

Vous avez peut-être observé un comportement intéressant des entiers. Division d’entier toujours produit un résultat entier, même lorsque le résultat à inclure une partie décimale ou fractionnaire souhaitées.

Si vous n’avez pas lu ce problème, essayez le code suivant à la fin de votre `Main` méthode :

```csharp
int e = 7;
int f = 4;
int g = 3;
int h = (e  + f) / g;
Console.WriteLine(h);
```

Type `dotnet run` pour voir les résultats.

Avant de continuer, nous allons prendre tout code que vous avez écrite dans cette section et le placer dans une nouvelle méthode. Appelez cette méthode nouvelle `OrderPrecedence`.
Vous devez obtenir quelque chose comme suit :

```csharp
using System;

namespace NumbersInCSharp
{
    class Program
    {
        static void WorkingWithIntegers()
        {
            int a = 18;
            int b = 6;
            int c = a + b;
            Console.WriteLine(c);
            c = a - b;
            Console.WriteLine(c);
            c = a * b;
            Console.WriteLine(c);
            c = a / b;
            Console.WriteLine(c);
        }

        static void OrderPrecedence()
        {   
            int a = 5;
            int b = 4;
            int c = 2;
            int d = a + b * c;
            Console.WriteLine(d);

            d = (a  + b) * c;
            Console.WriteLine(d);

            d = (a + b) - 6 * c + (12 * 4) / 3 + 12;
            Console.WriteLine(d);

            int e = 7;
            int f = 4;
            int g = 3;
            int h = (e  + f) / g;
            Console.WriteLine(h);
        }

        static void Main(string[] args)
        {
            WorkingWithIntegers();

            OrderPrecedence();

        }
    }
}
```

## <a name="explore-integer-precision-and-limits"></a>Explorer la précision et les limites des entiers
Ce dernier exemple a montré que la division d’entiers tronque le résultat.
Vous pouvez obtenir le **reste** à l’aide de la **modulo** (opérateur), le `%` caractère. Essayez le code suivant dans votre `Main` méthode :

```csharp
int a = 7;
int b = 4;
int c = 3;
int d = (a  + b) / c;
int e = (a + b) % c;
Console.WriteLine($"quotient: {d}");
Console.WriteLine($"remainder: {e}");
```

Le type d’entier C# diffère des entiers mathématiques d’une autre manière : le type `int` a des limites minimale et maximale. Ajoutez ce code à votre `Main` méthode pour afficher ces limites :
    
```csharp
int max = int.MaxValue;
int min = int.MinValue;
Console.WriteLine($"The range of integers is {min} to {max}");
```

Si un calcul produit une valeur qui dépasse ces limites, vous obtenez une condition de **dépassement négatif** ou **dépassement positif**. La réponse affichée indique la plage (d’une limite à l’autre). Ajoutez ces deux lignes à votre `Main` méthode pour voir un exemple :

```csharp
int what = max + 3;
Console.WriteLine($"An example of overflow: {what}");
```
    
Notez que la réponse est très proche de l’entier minimal (négatif). Il en est de même pour `min + 2`. L’addition a produit un **dépassement négatif** des valeurs autorisées pour les entiers.
La réponse est un très grand nombre négatif, car un dépassement négatif « inclut » de la plus grande valeur d’entier possible à la plus petite.

Il existe d’autres types numériques avec une précision et des limites différentes que vous pouvez utiliser quand le type `int` ne répond pas à vos besoins. Nous les explorerons à l’étape suivante.

Une fois encore, passons maintenant le code que vous avez écrit dans cette section dans une méthode distincte. Nommez-le `TestLimits`. 

## <a name="work-with-the-double-type"></a>Utiliser le type double

Le type numérique `double` représente un nombre à virgule flottante double précision. Ces termes vous sont peut-être inconnus. A **à virgule flottante** nombre est utile pour représenter des nombres non intégral qui peuvent être très grande ou petite dans l’ordre de grandeur. La **double précision** signifie que ces nombres sont stockés avec une précision supérieure à la **simple précision**. Sur les ordinateurs modernes, les nombres double précision sont généralement plus utilisés que les nombres simple précision.
Explorons ce type double. Ajoutez le code suivant et voir le résultat obtenu :

```csharp
double a = 5;
double b = 4;
double c = 2;
double d = (a  + b) / c;
Console.WriteLine(d);
```

Notez que la réponse inclut la partie décimale du quotient. Essayez avec une expression légèrement plus complexe utilisant des doubles :

```csharp
double e = 19;
double f = 23;
double g = 8;
double h = (e  + f) / g;
Console.WriteLine(h);
```

La plage d’une valeur double est nettement supérieure à celle de valeurs entières. Essayez le code suivant sous ce que vous avez écrits jusqu'à présent :

```csharp
double max = double.MaxValue;
double min = double.MinValue;
Console.WriteLine($"The range of double is {min} to {max}");
```

Ces valeurs sont imprimés dans la notation scientifique. Le nombre à gauche de la `E` est la mantisse. Le nombre à droite est l’exposant, en puissance de 10. 

Tout comme les nombres décimaux en mathématiques, les doubles en C# peuvent présenter des erreurs d’arrondi. Exécutez le code suivant :

```csharp
double third = 1.0 / 3.0;
Console.WriteLine(third);
```

Vous savez que la valeur extensible `0.3` ne correspond pas exactement à `1/3`.

***Test***

Effectuez d’autres calculs avec des grands nombres, des petits nombres, des multiplications et des divisions à l’aide du type `double`.  Effectuez des calculs plus complexes.

Une fois que vous avez passé un certain temps avec la demande, prenez le code que vous avez écrit et les placez dans une nouvelle méthode. Nommez cette nouvelle méthode `WorkWithDoubles`.

## <a name="work-with-fixed-point-types"></a>Utiliser des types de virgule fixe

Vous avez vu les types numériques de base en C#, à savoir les entiers et les doubles.  Il existe un autre type à découvrir : le type `decimal`. Le `decimal` type a une plage plus petite, mais une précision supérieure que `double`. Le terme **virgule fixe** signifie que la virgule décimale (ou virgule binaire) ne se déplace pas. Étudions cela d’un peu plus près :

```csharp
decimal min = decimal.MinValue;
decimal max = decimal.MaxValue;
Console.WriteLine($"The range of the decimal type is {min} to {max}");
```

Notez que la plage est plus petite que celle du type `double`. Vous pouvez observer la plus haute précision du type décimal en exécutant le code suivant :

```csharp
double a = 1.0;
double b = 3.0;
Console.WriteLine(a / b);

decimal c = 1.0M;
decimal d = 3.0M;
Console.WriteLine(c / d);
```

Le suffixe `M` des nombres permet d’indiquer comment une constante doit utiliser le type `decimal`.

Notez que le calcul utilisant le type décimal a plus de chiffres à droite de la virgule décimale. 

***Test***

Maintenant que vous avez vu les différents types numériques, écrivez un code qui calcule la surface d’un cercle avec un rayon de 2,5 pouces. Rappelez-vous que la surface d’un cercle est le rayon au carré multiplié par PI. Un seul indicateur : c# contient une constante de PI, <xref:System.Math.PI?displayProperty=nameWithType> que vous pouvez utiliser pour cette valeur. 

Vous pouvez vérifier votre réponse par [en examinant le code exemple terminé sur GitHub](https://github.com/dotnet/docs/tree/master/samples/csharp/numbers-quickstart/Program.cs#L104-L106)

Essayez de certaines autres formules que vous souhaitez. 

Vous avez terminé le démarrage rapide de « numéros dans c# ». Vous pouvez poursuivre la [Branches et des boucles](branches-and-loops-local.md) démarrage rapide dans votre propre environnement de développement.

Pour en savoir plus sur les nombres en C#, consultez les rubriques suivantes :

[Tableau des types intégraux](../language-reference/keywords/integral-types-table.md)   
[Tableau des types virgule flottante](../language-reference/keywords/floating-point-types-table.md)   
[Tableau des types intégrés](../language-reference/keywords/built-in-types-table.md)   
[Tableau des conversions numériques implicites](../language-reference/keywords/implicit-numeric-conversions-table.md)   
[Tableau des conversions numériques explicites](../language-reference/keywords/explicit-numeric-conversions-table.md)

