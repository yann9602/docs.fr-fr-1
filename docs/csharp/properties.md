---
title: "Propriétés"
description: "En savoir plus sur les propriétés C#, notamment les fonctionnalités liées à la validation, les valeurs calculées, l’évaluation différée et les notifications de modification de propriété."
keywords: .NET, .NET Core
author: BillWagner
ms.author: wiwagn
ms.date: 04/03/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 6950d25a-bba1-4744-b7c7-a3cc90438c55
ms.openlocfilehash: 1ffacd52df89a955ebfa72dc58836211c7a58640
ms.sourcegitcommit: 5fb6646b5ee3769ffb214e672041833ea4ceeb26
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/08/2017
---
# <a name="properties"></a>Propriétés

Les propriétés sont des éléments de première classe dans C#. Le langage définit la syntaxe que les développeurs utilisent pour écrire du code qui exprime leur intention de conception avec précision.

Les propriétés auxquelles le code accède se comportent comme des champs.
Toutefois, contrairement aux champs, les propriétés sont implémentées avec des accesseurs qui définissent quelles instructions sont exécutées au moment de l’accès à une propriété ou de son assignation.

## <a name="property-syntax"></a>Syntaxe des propriétés

La syntaxe des propriétés est une extension naturelle des champs. Un champ définit un emplacement de stockage :

```csharp
public class Person
{
    public string FirstName;
    // remaining implementation removed from listing
}
```

Une définition de propriété contient les déclarations de l’accesseur `get`, qui récupère la valeur de cette propriété, et de l’accesseur `set`, qui assigne cette valeur :

```csharp
public class Person
{
    public string FirstName { get; set; }

    // remaining implementation removed from listing
}
```

La syntaxe illustrée ci-dessus est la syntaxe *auto property*. Le compilateur génère l’emplacement de stockage pour le champ qui enregistre la propriété. Le compilateur implémente également le corps des accesseurs `get` et `set`.

Parfois, vous devez initialiser une propriété sur une valeur autre que la valeur par défaut pour son type.  C# permet cette opération en définissant une valeur après l’accolade fermante de la propriété. Vous pouvez choisir comme valeur initiale pour la propriété `FirstName` une chaîne vide au lieu de `null`. Vous pouvez le spécifier comme indiqué ci-dessous :

```csharp
public class Person
{
    public string FirstName { get; set; } = string.Empty;

    // remaining implementation removed from listing
}
```

Cela est très utile pour les propriétés en lecture seule, comme vous le verrez plus loin dans cette rubrique.

Vous pouvez aussi définir le stockage vous-même, de la manière suivante :

```csharp
public class Person
{
    public string FirstName
    {
        get { return firstName; }
        set { firstName = value; }
    }
    private string firstName;
    // remaining implementation removed from listing
}
```

Quand une implémentation de propriété est une expression unique, vous pouvez utiliser des *membres expression-bodied* pour l’accesseur Get ou Set :

```csharp
public class Person
{
    public string FirstName
    {
        get => firstName;
        set => firstName = value;
    }
    private string firstName;
    // remaining implementation removed from listing
}
```

Cette syntaxe simplifiée est utilisée partout où elle est applicable dans cette rubrique.

La définition de propriété présentée ci-dessus est une propriété en lecture-écriture. Notez la présence du mot clé `value` dans l’accesseur set. L’accesseur `set` a toujours un seul paramètre nommé `value`. L’accesseur `get` doit retourner une valeur convertible dans le type de la propriété (`string`, dans cet exemple).
 
Nous venons de voir les éléments de base de la syntaxe. Il existe beaucoup de variantes de cette syntaxe, qui sont adaptées aux différents idiomes de conception. Nous allons explorer ces variantes et découvrir les options syntaxiques de chacune.

## <a name="scenarios"></a>Scénarios

Les exemples ci-dessus ont montré un des cas les plus simples de définition de propriété, à savoir une propriété en lecture-écriture sans validation. En écrivant le code souhaité dans les accesseurs `get` et `set`, vous pouvez créer de nombreux scénarios différents.

### <a name="validation"></a>Validation

Vous pouvez écrire du code dans l’accesseur `set` pour garantir que les valeurs représentées par une propriété sont toujours valides. Par exemple, définissez une règle pour la classe `Person` qui spécifie que le nom ne peut pas être vide, ni contenir d’espace blanc. Le code à écrire est le suivant :

```csharp
public class Person
{
    public string FirstName
    {
        get => firstName;
        set
        {
            if (string.IsNullOrWhiteSpace(value))
                throw new ArgumentException("First name must not be blank");
            firstName = value;
        }
    }
    private string firstName;
    // remaining implementation removed from listing
}
```

L’exemple ci-dessus applique la règle selon laquelle le nom ne doit pas être vide, ni contenir d’espace blanc. Supposons qu’un développeur écrive cette ligne de code :

```csharp
hero.FirstName = "";
```

Cette assignation lève une exception `ArgumentException`. Étant donné qu’un accesseur set de propriété doit avoir un type de retour void, vous signalez les erreurs dans l’accesseur set en levant une exception.

Ceci est un cas simple de validation. Vous pouvez employer cette même syntaxe pour valider d’autres éléments dans votre scénario. Vous pouvez notamment vérifier les relations entre plusieurs propriétés ou effectuer une validation par rapport à des conditions externes. Toute instruction C# valide peut être utilisée dans un accesseur de propriété.

### <a name="read-only"></a>Propriétés en lecture seule

Jusqu’ici, nous avons vu uniquement des définitions de propriétés qui sont en lecture-écriture dans des accesseurs publics. Ce n’est pas la seule accessibilité valide pour les propriétés.
Vous pouvez créer des propriétés en lecture seule, ou assigner une accessibilité différente aux accesseurs set et get. Supposons que votre classe `Person` doit uniquement autoriser la modification de la valeur de la propriété `FirstName` à partir des autres méthodes de cette classe. Vous pouvez alors assigner l’accessibilité `private` au lieu de `public` à l’accesseur set :

```csharp
public class Person
{
    public string FirstName { get; private set; }

    // remaining implementation removed from listing
}
```

À présent, la propriété `FirstName` est accessible à partir de n’importe quel code, mais elle peut uniquement être assignée à partir de code dans la classe `Person`.

Vous pouvez ajouter n’importe quel modificateur d’accès restrictif à l’accesseur set ou get. Le modificateur d’accès que vous ajoutez à un accesseur doit être plus restrictif que le modificateur d’accès spécifié dans la définition de propriété. Le code ci-dessus est autorisé, car la propriété `FirstName` est `public`, mais l’accesseur set est `private`. En revanche, vous ne pouvez pas déclarer une propriété `private` avec un accesseur `public`. Déclarations de propriétés peuvent également être déclarées `protected`, `internal`, `protected internal`, `private protected` ou même `private`.   

Placer le modificateur le plus restrictif sur l’accesseur `get` est également autorisé. Par exemple, vous pouvez avoir une propriété `public`, mais restreindre l’accesseur `get` à `private`. Ce scénario s’observe rarement dans la pratique.

Vous pouvez également limiter les modifications apportées à une propriété pour qu’elle puisse uniquement être définie dans un constructeur ou un initialiseur de propriété. Vous pouvez modifier la classe `Person`, comme suit :

```csharp
public class Person
{
    public Person(string firstName)
    {
        this.FirstName = firstName;
    }

    public string FirstName { get; }

    // remaining implementation removed from listing
}
```

Cette fonctionnalité est généralement utilisée pour initialiser des collections qui sont exposées sous forme de propriétés en lecture seule :

```csharp
public class Measurements
{
    public ICollection<DataPoint> points { get; } = new List<DataPoint>();
}
```

### <a name="computed-properties"></a>Propriétés calculées

Une propriété peut faire plus que simplement retourner la valeur d’un champ de membre. Vous pouvez créer des propriétés qui retournent une valeur calculée. L’objet `Person` est étendu pour retourner le nom complet, calculé en concaténant le nom et le prénom :

```csharp
public class Person
{
    public string FirstName { get; set; }

    public string LastName { get; set; }

    public string FullName { get { return $"{FirstName} {LastName}"; } }
}
```

L’exemple ci-dessus utilise la syntaxe d’*interpolation de chaîne* pour créer la chaîne mise en forme du nom complet.

Vous pouvez également utiliser des *membres expression-bodied*, qui constituent un moyen plus succinct de créer la propriété `FullName` calculée :

```csharp
public class Person
{
    public string FirstName { get; set; }

    public string LastName { get; set; }

    public string FullName =>  $"{FirstName} {LastName}";
}
```
 
Les *membres expression-bodied* utilisent la syntaxe des *expressions lambda* pour définir une méthode qui contient une expression unique. Ici, cette expression retourne le nom complet de l’objet person.

### <a name="lazy-evaluated-properties"></a>Propriétés à évaluation différée

Vous pouvez combiner le concept d’une propriété calculée avec le stockage pour créer une *propriété à évaluation différée*.  Par exemple, vous pouvez mettre à jour la propriété `FullName` pour que la chaîne soit mise en forme uniquement lors du premier accès à cette propriété :

```csharp
public class Person
{
    public string FirstName { get; set; }

    public string LastName { get; set; }

    private string fullName;
    public string FullName
    {
        get
        {
            if (fullName == null)
                fullName = $"{FirstName} {LastName}";
            return fullName;
        }
    }
}
```

Le code ci-dessus contient toutefois un bogue. Si le code met à jour la valeur de la propriété `FirstName` ou `LastName`, le champ `fullName` qui a été précédemment évalué n’est plus valide. Vous devez donc mettre à jour les accesseurs `set` des propriétés `FirstName` et `LastName` pour que le champ `fullName` soit recalculé :

```csharp
public class Person
{
    private string firstName;
    public string FirstName
    {
        get => firstName;
        set
        {
            firstName = value;
            fullName = null;
        }
    }

    private string lastName;
    public string LastName
    {
        get => lastName;
        set
        {
            lastName = value;
            fullName = null;
        }
    }

    private string fullName;
    public string FullName
    {
        get
        {
            if (fullName == null)
                fullName = $"{FirstName} {LastName}";
            return fullName;
        }
    }
}
```

Dans cette version finale du code, la propriété `FullName` est évaluée uniquement si cela est nécessaire.
Si la version précédemment calculée est valide, elle est utilisée. Si elle n’est plus valide en raison d’un changement d’état, la version est recalculée. Les développeurs peuvent utiliser cette classe sans connaître les détails de l’implémentation. Ces modifications internes n’ont pas d’impact sur l’utilisation de l’objet Person. C’est l’un des principaux avantages d’utiliser des propriétés pour exposer les membres de données d’un objet.
 
### <a name="inotifypropertychanged"></a>Interface INotifyPropertyChanged

Il existe un dernier scénario où vous devrez écrire du code dans un accesseur de propriété : pour prendre en charge l’interface `INotifyPropertyChanged`, qui notifie les changements de valeurs aux clients de liaison de données. Quand la valeur d’une propriété change, l’objet déclenche l’événement `PropertyChanged` pour signaler le changement. Les bibliothèques de liaison de données mettent ensuite à jour les éléments d’affichage en fonction de cette modification. Le code ci-dessous montre comment implémenter `INotifyPropertyChanged` pour la propriété `FirstName` de la classe Person.

```csharp
public class Person : INotifyPropertyChanged
{
    public string FirstName
    {
        get => firstName;
        set
        {
            if (string.IsNullOrWhiteSpace(value))
                throw new ArgumentException("First name must not be blank");
            if (value != firstName)
            {
                PropertyChanged?.Invoke(this, 
                    new PropertyChangedEventArgs(nameof(FirstName)));
            }
            firstName = value;
        }
    }
    private string firstName;

    public event PropertyChangedEventHandler PropertyChanged;
    // remaining implementation removed from listing
}
```

L’opérateur `?.` est appelé *opérateur conditionnel Null*. Il recherche une référence null avant d’évaluer le côté droit de l’opérateur. Au final, s’il n’y a pas d’abonné à l’événement `PropertyChanged`, le code devant déclencher l’événement n’est pas exécuté. Dans ce cas précis, il lèverait une exception `NullReferenceException` sans cette vérification. Pour plus d’informations, consultez la page [`events`](delegates-events.md). Cet exemple utilise également le nouvel opérateur `nameof` pour convertir le symbole de nom de propriété en sa représentation textuelle.
L’utilisation de `nameof` peut vous éviter des erreurs dues à la saisie incorrecte du nom de propriété.

Là encore, il s’agit d’un exemple de cas où vous pouvez écrire du code dans vos accesseurs pour prendre en charge les scénarios souhaités.

## <a name="summing-up"></a>Récapitulatif

Les propriétés sont une forme de champs intelligents dans une classe ou un objet. De l’extérieur de l’objet, elles apparaissent sous la forme de champs dans l’objet. Toutefois, les propriétés peuvent être implémentées avec toutes les fonctionnalités C#.
Vous pouvez écrire du code qui remplit les exigences de validation, d’accessibilité, d’évaluation différée ou toute autre exigence requise dans vos scénarios.
