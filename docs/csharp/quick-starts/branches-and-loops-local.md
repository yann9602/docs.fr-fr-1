---
title: "Démarrage rapide - Branches et lops - Guide c#"
description: "Dans ce guide de démarrage rapide sur les branches et des boucles, vous écrivez du code c# pour Explorer la syntaxe du langage qui prend en charge des branches conditionnelles et des boucles pour exécuter des instructions à plusieurs reprises."
author: billwagner
ms.author: wiwagn
ms.date: 10/31/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.custom: mvc
ms.openlocfilehash: 4b077a29cf42072a93b054f50a13a4580ad54304
ms.sourcegitcommit: 43c656811dd38a66a6672084c65d10c0cbbf2015
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2017
---
# <a name="branches-and-loops"></a>Branches et boucles

Ce guide de démarrage rapide vous apprend comment écrire du code qui examine les variables et modifie le chemin d’accès de l’exécution en fonction de ces variables. Écrire du code c# et de voir les résultats de la compilation et son exécution. Le démarrage rapide contient une série de leçons qui explorent la création de branche et de constructions de boucle dans c#. Ces leçons présentent les concepts de base du langage C#.

Ce démarrage rapide attend que vous disposiez d’un ordinateur, que vous pouvez utiliser pour le développement. La rubrique .NET [prise en main de 10 minutes](https://www.microsoft.com/net/core) a des instructions pour configurer votre environnement de développement local sur le Mac, PC ou Linux.

## <a name="make-decisions-using-the-if-statement"></a>Prenez les décisions relatives à l’aide de la `if` instruction

Créez un répertoire nommé **branches-démarrage rapide**. Faites-en le répertoire actuel et exécutez `dotnet new console -n BranchesAndLoops -o .`. Cette commande crée une nouvelle application de console .NET Core dans le répertoire actif. 

Ouvrez **Program.cs** dans votre éditeur favori, puis remplacez la ligne `Console.Writeline("Hello World!");` par le code suivant :

```csharp
int a = 5;
int b = 6;
if (a + b > 10)
    Console.WriteLine("The answer is greater than 10.");
```

Essayez le code suivant en tapant `dotnet run` dans la fenêtre de la console. Vous devez voir le message « la réponse est supérieure à 10 ». imprimé à votre console.

Modifiez la déclaration de `b` pour que la somme soit inférieure à 10 : 

```csharp
int b = 3;
```

Type `dotnet run` à nouveau. La réponse étant inférieure à 10, rien ne s’affiche. La **condition** que vous testez a une valeur false. Vous n’avez pas de code à exécuter, car vous avez uniquement écrit l’une des branches possibles pour une instruction `if` : la branche true.

> [!TIP]
> Durant votre exploration de C# (ou de tout autre langage de programmation), vous commettrez des erreurs d’écriture du code. Le compilateur détecte et signaler les erreurs. Examinez attentivement la sortie d’erreur et le code qui a généré l’erreur. L’erreur compler peut généralement vous aider à identifier le problème. 

Le premier exemple montre la puissance de `if` et types booléens. A *booléenne* est une variable qui peut avoir une des deux valeurs : `true` ou `false`. C# définit un type spécial, `bool` des variables booléennes. L’instruction `if` vérifie la valeur d’un `bool`. Quand la valeur est `true`, l’instruction qui suit `if` s’exécute. Dans le cas contraire, elle est ignorée. 

Ce processus de vérification des conditions et d’exécution des instructions en fonction de ces conditions est très performant.


## <a name="make-if-and-else-work-together"></a>Utiliser if et else ensemble

Pour exécuter un code différent dans les branches true et false, vous créez une branche `else` qui s’exécute quand la condition a une valeur false. Sont manquants. Ajoutez les deux dernières lignes dans le code suivant à votre `Main` (méthode) (vous devez déjà avoir les quatre premiers) :

```csharp
int a = 5;
int b = 3;
if (a + b > 10)
    Console.WriteLine("The answer is greater than 10");
else
    Console.WriteLine("The answer is not greater than 10");
```

L’instruction qui suit le mot clé `else` s’exécute uniquement quand la condition testée a une valeur `false`. Combinaison de `if` et `else` avec une valeur booléenne conditions fournit toute la puissance dont vous avez besoin pour gérer à la fois un `true` et un `false` condition.

> [!IMPORTANT]
> La mise en retrait sous les instructions `if` et `else` a simplement pour but de faciliter la lecture.
> Le langage C# ne considère pas la mise en retrait ou les espaces blancs comme des éléments significatifs. L’instruction qui suit le mot clé `if` ou `else` sera exécutée en fonction de la condition. Tous les exemples dans ce démarrage rapide suivent une pratique courante pour mettre en retrait les lignes selon le flux de contrôle d’instructions.

Étant donné que la mise en retrait n’est pas significative, vous devez utiliser `{` et `}` pour indiquer quand vous souhaitez inclure plus d’une instruction dans le bloc qui s’exécute de manière conditionnelle. Les programmeurs C# utilisent généralement les accolades pour toutes les clauses `if` et `else`. L’exemple suivant est identique à celui que vous venez de créer. Modifiez le code ci-dessus pour faire correspondre le code suivant :

```csharp
int a = 5;
int b = 3;
if (a + b > 10)
{
    Console.WriteLine("The answer is greater than 10");
}
else
{
    Console.WriteLine("The answer is not greater than 10");
}
```

> [!TIP]
> Le reste de ce guide de démarrage rapide, tous les exemples de code incluent les accolades suivant accepté pratiques.

Vous pouvez tester des conditions plus complexes. Ajoutez le code suivant dans votre `Main` méthode après le code que vous avez écrits jusqu'à présent :

```csharp
    int c = 4;
    if ((a + b + c > 10) && (a > b))
{
    Console.WriteLine("The answer is greater than 10");
    Console.WriteLine("And the first number is greater than the second");
}
else
{
    Console.WriteLine("The answer is not greater than 10");
    Console.WriteLine("Or the first number is not greater than the second");
}
```

`&&` représente « et ». Cela signifie que les deux conditions doivent être true pour que l’instruction s’exécute dans la branche true.  Ces exemples montrent également que vous pouvez avoir plusieurs instructions dans chaque branche conditionnelle, à condition de les mettre entre `{` et `}`.

Vous pouvez également utiliser `||` pour représenter « ou ». Une fois que vous avez écrits jusqu'à présent, ajoutez le code suivant :

```csharp
if ((a + b + c > 10) || (a > b))
{
    Console.WriteLine("The answer is greater than 10");
    Console.WriteLine("Or the first number is greater than the second");
}
else
{
    Console.WriteLine("The answer is not greater than 10");
    Console.WriteLine("And the first number is not greater than the second");
}
```

Vous avez terminé la première étape. Avant de passer à la section suivante, déplaçons le code actuel dans une méthode distincte. Cela nous permettra de travailler plus facilement avec un nouvel exemple. Renommez votre méthode `Main` `ExploreIf` et écrivez une nouvelle méthode `Main` qui appelle `ExploreIf`. Une fois terminé, votre code doit ressembler au code suivant :

```csharp
using System;

namespace BranchesAndLoops
{
    class Program
    {
        static void ExploreIf()
        {
            int a = 5;
            int b = 3;
            if (a + b > 10)
            {
                Console.WriteLine("The answer is greater than 10");
            }
            else
            {
                Console.WriteLine("The answer is not greater than 10");
            }

            if ((a + b + c > 10) && (a > b))
            {
                Console.WriteLine("The answer is greater than 10");
                Console.WriteLine("And the first number is greater than the second");
            }
            else
            {
                Console.WriteLine("The answer is not greater than 10");
                Console.WriteLine("Or the first number is not greater than the second");
            }

            if ((a + b + c > 10) || (a > b))
            {
                Console.WriteLine("The answer is greater than 10");
                Console.WriteLine("Or the first number is greater than the second");
            }
            else
            {
                Console.WriteLine("The answer is not greater than 10");
                Console.WriteLine("And the first number is not greater than the second");
            }            
        }

        static void Main(string[] args)
        {
            ExploreIf();
        }
    }
}
```

Commentez l’appel à `ExploreIf()`. Il effectue la sortie que moins encombrée lorsque vous travaillez dans cette section :

```csharp
//ExploreIf();
```

Le `//` démarre un **commentaire** en c#. Les commentaires sont n’importe quel texte que vous souhaitez conserver dans votre code source, mais pas s’exécuter en tant que code. Le compilateur ne génère pas de code exécutable à partir de commentaires.

## <a name="use-loops-to-repeat-operations"></a>Utiliser des boucles pour répéter des opérations

Dans cette section, vous utilisez **boucles** à répéter les instructions. Essayez le code suivant dans votre `Main` méthode :

```csharp
int counter = 0;
while (counter < 10)
{
    Console.WriteLine($"Hello World! The counter is {counter}");
    counter++;
}
```

Le `while` instruction vérifie une condition et exécute l’instruction ou le bloc d’instructions suivant le `while`. À plusieurs reprises, il vérifie la condition et l’exécution de ces instructions jusqu'à ce que la condition est false.

Cet exemple contient un nouvel opérateur. `++` après la variable `counter` est l’opérateur d’**incrémentation**. Il ajoute 1 à la valeur de `counter` et stocke cette valeur dans la `counter` variable.

> [!IMPORTANT]
> Assurez-vous que le `while` sur false, les modifications de condition de boucle lorsque vous exécutez le code. Dans le cas contraire, vous allez créer une **boucle infinie** dans laquelle votre programme ne se terminera jamais. Qui n’est pas illustrée dans cet exemple, car vous devez forcer votre programme pour cesser d’utiliser **CTRL-C** ou d’autres moyens.

La boucle `while` teste la condition avant d’exécuter le code qui suit `while`. La boucle `do` ... `while` exécute d’abord le code, puis vérifie la condition. Faire lors de la boucle est indiquée dans le code suivant :

```csharp
counter = 0;
do
{
    Console.WriteLine($"Hello World! The counter is {counter}");
    counter++;
} while (counter < 10);
```

Cela `do` boucle et la plus antérieure `while` boucle produisent le même résultat.

## <a name="work-with-the-for-loop"></a>Utiliser la boucle for

Le **pour** boucle est couramment utilisée dans c#. Essayez ce code dans votre méthode Main() :

```csharp
for(int index = 0; index < 10; index++)
{
    Console.WriteLine($"Hello World! The index is {index}");
} 
```

Cette boucle fonctionne de manière identique à la boucle `while` et la boucle `do` que vous avez déjà utilisées. L’instruction `for` comprend trois parties qui contrôlent son fonctionnement. 

La première partie est l’**initialiseur for** : `for index = 0;` déclare que `index` est la variable de boucle et définit sa valeur initiale sur `0`.

La partie centrale est la **condition for** : `index < 10` déclare que cette boucle `for` continue à s’exécuter tant que la valeur de compteur est inférieure à 10.

La dernière partie est l’**itérateur for** : `index++` indique comment modifier la variable de boucle après l’exécution du bloc qui suit l’instruction `for`. Il spécifie ici que `index` doit être incrémenté de 1 chaque fois que le bloc s’exécute.

Vérifiez-le par vous-même. Réalisez les essais suivants :

- Modifiez l’initialiseur pour définir le démarrage à une valeur différente.
- Modifiez la condition pour définir l’arrêt à une valeur différente.

Une fois terminé, vous allez vous-même écrire des codes pour mettre en pratique ce que vous avez appris.

## <a name="combine-branches-and-loops"></a>Combiner des branches et des boucles

Maintenant que vous avez vu l’instruction `if` et la création de boucles en langage C#, vérifiez si vous pouvez écrire un code C# pour obtenir la somme de tous les entiers de 1 à 20 divisibles par 3.  Voici quelques conseils :

- L’opérateur `%` vous donne le reste d’une opération de division.
- La `if` instruction vous donne la condition pour voir si un nombre doit être la partie de la somme.
- La boucle `for` peut vous aider à répéter une série d’étapes pour tous les nombres de 1 à 20.

Essayez par vous-même et vérifiez le résultat. Vous pouvez voir une réponse possible par [affichage du code terminé sur GitHub](https://github.com/dotnet/docs/tree/master/samples/csharp/branches-quickstart/Program.cs#L46-L54).

Vous avez terminé le démarrage rapide de « branches et effectue une boucle ».

Vous pouvez poursuivre la [tableaux et collections](arrays-and-collections.md) démarrage rapide dans votre propre environnement de développement.

Pour en savoir plus sur ces concepts, consultez les rubriques suivantes :

[Instruction if et else](../language-reference/keywords/if-else.md)   
[Instruction while](../language-reference/keywords/while.md)   
[Instruction do](../language-reference/keywords/do.md)   
[Instruction for](../language-reference/keywords/for.md)   
