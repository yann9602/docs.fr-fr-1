---
title: "Développement de bibliothèques avec des outils multiplateformes"
description: "Développement de bibliothèques avec des outils multiplateformes"
keywords: .NET, .NET Core
author: cartermp
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 9f6e8679-bd7e-4317-b3f9-7255a260d9cf
translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: 7f419e1fc2c9f442b08e19ede4e84f9cf6843a94
ms.lasthandoff: 03/02/2017

---

# <a name="developing-libraries-with-cross-platform-tools"></a>Développement de bibliothèques avec des outils multiplateformes

**Certains détails sont susceptibles de changer à mesure que la chaîne d’outils évolue.**

Cet article explique comment écrire des bibliothèques pour .NET à l’aide des outils CLI multiplateformes.  L’interface CLI fournit une expérience efficace et de bas niveau qui fonctionne sur tous les systèmes d’exploitation pris en charge.  Vous pouvez toujours créer des bibliothèques avec Visual Studio, et si c’est ce que vous préférez, [consultez le guide Visual Studio](libraries-with-vs.md).

## <a name="prerequisites"></a>Prérequis

[Le SDK .NET Core et l’interface CLI](https://www.microsoft.com/net/core) doivent être installés sur votre ordinateur.

Pour accéder aux sections de ce document concernant les versions du .NET Framework ou les bibliothèques de classes portables (PCL), vous devez installer le [.NET Framework](http://getdotnet.azurewebsites.net/) sur un ordinateur Windows.  

De plus, si vous voulez prendre en charge des cibles .NET Framework antérieures, vous devez installer les packs de ciblage/développeur des versions antérieures du Framework à partir de la [page de plateformes cibles .NET](http://getdotnet.azurewebsites.net/target-dotnet-platforms.html).  Reportez-vous au tableau suivant :

| Version du .NET Framework | À télécharger |
| ---------------------- | ----------------- |
| 4.6.1 | Pack de ciblage .NET Framework 4.6.1 |
| 4.6 | Pack de ciblage .NET Framework 4.6 |
| 4.5.2 | Pack du développeur .NET Framework 4.5.2 |
| 4.5.1 | Pack du développeur .NET Framework 4.5.1 |
| 4.5 | SDK Windows pour Windows 8 |
| 4.0 | SDK pour Windows 7 et .NET Framework 4 |
| 2.0, 3.0 et 3.5 | Runtime .NET Framework 3.5 SP1 (ou version Windows 8+) |

## <a name="how-to-target-the-net-standard"></a>Comment cibler .NET Standard

Si vous n’êtes pas très familiarisé avec .NET Standard, reportez-vous à [la bibliothèque .NET Standard](../../standard/library.md) pour en savoir plus.

Voici un tableau qui associe les versions .NET Standard à diverses implémentations :

| Nom de la plateforme | Alias |  |  |  |  |  | | |
| :---------- | :--------- |:--------- |:--------- |:--------- |:--------- |:--------- |:--------- |:--------- |
|.NET Standard | netstandard | 1.0 | 1.1 | 1.2 | 1.3 | 1.4 | 1,5 | 1.6 |
|.NET Core|netcoreapp|&rarr;|&rarr;|&rarr;|&rarr;|&rarr;|&rarr;|1.0|
|.NET Framework|net|&rarr;|4.5|4.5.1|4.6|4.6.1|4.6.2|4.6.3|
|Plateformes Mono/Xamarin||&rarr;|&rarr;|&rarr;|&rarr;|&rarr;|&rarr;|*|
|Plateforme Windows universelle|uap|&rarr;|&rarr;|&rarr;|&rarr;|10.0|||
|Windows|win|&rarr;|8.0|8.1|||||
|Windows Phone|wpa|&rarr;|&rarr;|8.1|||||
|Windows Phone Silverlight|wp|8.0|||||||

Voici ce que signifie ce tableau dans le processus de création d’une bibliothèque :

La version de .NET Platform Standard que vous choisissez est un compromis entre l’accès aux API les plus récentes et la possibilité de cibler plus de plateformes .NET et de versions du Framework.  Vous contrôlez la plage de versions et de plateformes pouvant être ciblées en sélectionnant une version de `netstandardX.X` (où `X.X` est un numéro de version), puis en l’ajoutant à votre fichier `project.json`.

De plus, le [package NuGet correspondant duquel dépendre](https://www.nuget.org/packages/NETStandard.Library/) est `NETStandard.Library` version `1.6.0`.  Même si rien ne vous empêche de dépendre de `Microsoft.NETCore.App` comme avec les applications console, cela n’est généralement pas recommandé.  Si vous avez besoin d’API d’un package non spécifié dans `NETStandard.Library`, vous pouvez toujours spécifier ce package en plus de `NETStandard.Library` dans la section `dependencies` de votre fichier `project.json`.

Vous disposez de trois options principales quand vous ciblez .NET Standard, en fonction de vos besoins.

1. Vous pouvez utiliser la dernière version de .NET Standard (`netstandard1.6`) qui permet d’accéder à la plupart des API si bénéficier de moins d’implémentations ne vous importe pas.
2. Vous pouvez utiliser une version antérieure de .NET Standard pour cibler des implémentations antérieures du .NET. Le prix à payer est alors l’impossibilité d’accéder aux API les plus récentes.
    
    Par exemple, si vous voulez garantir la compatibilité avec .NET Framework 4.6 et les versions ultérieures, vous devez sélectionner `netstandard1.3` :

    ```json
    {
        "dependencies":{
            "NETStandard.Library":"1.6.0"
        },
        "frameworks":{
            "netstandard1.3":{}
        }
    }
    ```
    
    Les versions .NET standard sont à compatibilité descendante. Cela signifie que les bibliothèques `netstandard1.0` s’exécutent sur les plateformes `netstandard1.1` et versions ultérieures.  Toutefois, il n’existe pas de compatibilité ascendante : les plateformes .NET Standard antérieures ne peuvent pas référencer les plateformes ultérieures.  Cela signifie que les bibliothèques `netstandard1.0` ne peuvent pas cibler des bibliothèques de référence ciblant `netstandard1.1` ou une version ultérieure.  Sélectionnez la version Standard qui offre une bonne combinaison entre les API et la prise en charge de plateformes pour vos besoins.
    
3. Si vous voulez cibler les versions .NET Framework 4.0 ou antérieures, ou que vous voulez utiliser une API disponible dans le .NET Framework, mais pas dans .NET Standard (par exemple, `System.Drawing`), lisez les sections suivantes et découvrez comment réaliser un multiciblage.

## <a name="how-to-target-the-net-framework"></a>Comment cibler le .NET Framework

> [!NOTE]
> Les instructions suivantes supposent que le .NET Framework est installé sur votre ordinateur.  Reportez-vous aux [Prérequis](#prerequisites) pour installer les dépendances.

N’oubliez pas que certaines des versions du .NET Framework utilisées ici ne sont plus prises en charge.  Reportez-vous au [Forum aux questions sur la politique de support de Microsoft .NET Framework](https://support.microsoft.com/gp/framework_faq/en-us) concernant les versions non prises en charge.

Si vous voulez atteindre le nombre maximal de développeurs et de projets, utilisez .NET Framework 4 comme cible de référence. Pour cibler le .NET Framework, vous devez commencer par utiliser le Moniker du Framework cible approprié qui correspond à la version du .NET Framework que vous voulez prendre en charge.

```
.NET Framework 2.0   --> net20
.NET Framework 3.0   --> net30
.NET Framework 3.5   --> net35
.NET Framework 4.0   --> net40
.NET Framework 4.5   --> net45
.NET Framework 4.5.1 --> net451
.NET Framework 4.5.2 --> net452
.NET Framework 4.6   --> net46
.NET Framework 4.6.1 --> net461
.NET Framework 4.6.2 --> net462
.NET Framework 4.6.3 --> net463
```

Par exemple, voici comment écrire une bibliothèque qui cible .NET Framework 4 :

```json
{
    "frameworks":{
        "net40":{}
    }
}
```

Et voilà !  Bien que ce code se compilait uniquement pour .NET Framework 4, vous pouvez utiliser la bibliothèque sur des versions plus récentes du .NET Framework.

## <a name="how-to-target-a-portable-class-library-pcl"></a>Comment cibler une bibliothèque de classes portables (PCL)

> [!NOTE]
> Les instructions suivantes supposent que le .NET Framework est installé sur votre ordinateur.  Reportez-vous aux [Prérequis](#prerequisites) pour installer les dépendances.

Le ciblage d’un profil PCL est un peu plus complexe que le ciblage de .NET Standard ou de .NET Framework.  Pour commencer, [référencez cette liste de profils PCL](http://embed.plnkr.co/03ck2dCtnJogBKHJ9EjY/preview) pour rechercher la cible NuGet qui correspond au profil PCL que vous ciblez.

Vous devez ensuite effectuer les opérations suivantes :

1. Créez une entrée sous `frameworks` dans votre `project.json`, nommée `.NETPortable,Version=v{version},Profile=Profile{profile}`, où `{version}` et `{profile}` correspondent à un numéro de version PCL et à un numéro de profil, respectivement.
2. Dans cette nouvelle entrée, répertoriez chaque assembly utilisé pour cette cible sous une entrée `frameworkAssemblies`.  Cela inclut `mscorlib`, `System` et `System.Core`.
3. Si vous effectuez un multiciblage (voir la section suivante), vous devez répertorier explicitement les dépendances pour chaque cible sous leurs entrées cibles.  Vous ne pouvez plus utiliser d’entrée `dependencies` globale.

Voici un exemple ciblant le profil PCL 328. Le profil 328 prend en charge : .NET Standard 1.4, .NET Framework 4, Windows 8, Windows Phone 8.1, Windows Phone Silverlight 8.1 et Silverlight 5.

```json
{
    "frameworks":{
        ".NETPortable,Version=v4.0,Profile=Profile328":{
            "frameworkAssemblies":{
                "mscorlib":"",
                "System":"",
                "System.Core":""
            }
        }
    }
}
```

Quand vous générez un projet qui inclut le profil PCL 328 comme framework dans le fichier *project.json*, celui-ci comprend le sous-dossier suivant dans le dossier */bin/debug* :

```
portable-net40+sl50+netcore45+wpa81+wp8/
```

Ce dossier contient les fichiers `.dll` nécessaires à l’exécution de votre bibliothèque.

## <a name="how-to-multitarget"></a>Comment multicibler

> [!NOTE]
> Les instructions suivantes supposent que le .NET Framework est installé sur votre ordinateur.  Reportez-vous à la section [Prérequis](#prerequisites) pour savoir quelles dépendances doivent être installées et à partir d’où les télécharger.

Vous devrez peut-être cibler des versions antérieures du .NET Framework si votre projet prend en charge à la fois .NET Framework et .NET Core. Dans ce scénario, si vous voulez utiliser des API et des constructions de langage plus récentes pour des cibles plus récentes, utilisez des directives `#if` dans votre code. Vous pouvez aussi avoir besoin d’ajouter différents packages et différentes dépendances dans votre `project.json file` pour chaque plateforme que vous ciblez afin d’inclure les différentes API nécessaires à chaque cas.

Supposons, par exemple, que vous avez une bibliothèque qui effectue des opérations réseau sur HTTP. Pour .NET Standard et les versions .NET Framework 4.5 ou ultérieures, vous pouvez utiliser la classe `HttpClient` à partir de l’espace de noms `System.Net.Http`. Toutefois, les versions antérieures du .NET Framework ne disposent pas de la classe `HttpClient`. Vous pourriez donc utiliser la classe `WebClient` à partir de l’espace de noms `System.Net` à la place.

Voici à quoi pourrait ressembler le fichier `project.json` :

```json
{
    "frameworks":{
        "net40":{
            "frameworkAssemblies": {
                "System.Net":"",
                "System.Text.RegularExpressions":""
            }
        },
        "net452":{
            "frameworkAssemblies":{
                "System.Net":"",
                "System.Net.Http":"",
                "System.Text.RegularExpressions":"",
                "System.Threading.Tasks":""
            }
        },
        "netstandard1.6":{
            "dependencies": {
                "NETStandard.Library":"1.6.0",
            }
        }
    }
}
```

Notez que les assemblys .NET Framework doivent être référencés explicitement dans la cible `net40` et `net452`. Les références NuGet sont également répertoriées explicitement dans la cible `netstandard1.6`.  C’est obligatoire dans les scénarios de multiciblage.

Ensuite, les instructions `using` dans votre fichier source peuvent être ajustées comme suit :

```csharp
#if NET40
// This only compiles for the .NET Framework 4 targets
using System.Net;
#else
// This compiles for all other targets
using System.Net.Http;
using System.Threading.Tasks;
#endif
```

Le système de build est informé des symboles de préprocesseur suivants utilisés dans les directives `#if`:

```
.NET Framework 2.0   --> NET20
.NET Framework 3.5   --> NET35
.NET Framework 4.0   --> NET40
.NET Framework 4.5   --> NET45
.NET Framework 4.5.1 --> NET451
.NET Framework 4.5.2 --> NET452
.NET Framework 4.6   --> NET46
.NET Framework 4.6.1 --> NET461
.NET Framework 4.6.2 --> NET462
.NET Standard 1.0    --> NETSTANDARD1_0
.NET Standard 1.1    --> NETSTANDARD1_1
.NET Standard 1.2    --> NETSTANDARD1_2
.NET Standard 1.3    --> NETSTANDARD1_3
.NET Standard 1.4    --> NETSTANDARD1_4
.NET Standard 1.5    --> NETSTANDARD1_5
.NET Standard 1.6    --> NETSTANDARD1_6
```

Et au milieu de la source, vous pouvez utiliser les directives `#if` pour utiliser ces bibliothèques de manière conditionnelle. Exemple :

```csharp
    public class Library
    {
#if NET40
        private readonly WebClient _client = new WebClient();
        private readonly object _locker = new object();
#else
        private readonly HttpClient _client = new HttpClient();
#endif

#if NET40
        // .NET Framework 4.0 does not have async/await
        public string GetDotNetCount()
        {
            string url = "http://www.dotnetfoundation.org/";
          
            var uri = new Uri(url);
            
            string result = "";
            
            // Lock here to provide thread-safety.
            lock(_locker)
            {
                result = _client.DownloadString(uri);
            }
            
            int dotNetCount = Regex.Matches(result, ".NET").Count;
            
            return $"Dotnet Foundation mentions .NET {dotNetCount} times!";
        }
#else
        // .NET 4.5+ can use async/await!
        public async Task<string> GetDotNetCountAsync()
        {
            string url = "http://www.dotnetfoundation.org/";
            
            // HttpClient is thread-safe, so no need to explicitly lock here
            var result = await _client.GetStringAsync(url);
            
            int dotNetCount = Regex.Matches(result, ".NET").Count;
            
            return $"dotnetfoundation.orgmentions .NET {dotNetCount} times in its HTML!";
        }
#endif
    }
```

Quand vous générez un projet qui inclut `net40`, `net45` et `netstandard1.6` comme frameworks dans le fichier *project.json*, celui-ci comprend les sous-dossiers suivants dans le dossier */bin/debug* :

```
net40/
net45/
netstandard1.6/
```

### <a name="but-what-about-multitargeting-with-portable-class-libraries"></a>Mais qu’en est-il du multiciblage avec les bibliothèques de classes portables ?

Si vous voulez effectuer une compilation croisée avec une cible PCL, vous devez ajouter une définition de build dans votre fichier `project.json` sous `buildOptions` dans votre cible PCL.  Vous pouvez ensuite utiliser, dans la source, des directives `#if` qui utilisent la définition de build comme symbole de préprocesseur.

Par exemple, si vous voulez cibler le [profil PCL 328](http://embed.plnkr.co/03ck2dCtnJogBKHJ9EjY/preview) (.NET Framework 4, Windows 8, Silverlight Windows Phone 8, Windows Phone 8.1, Silverlight 5), vous pouvez le référer comme « PORTABLE328 » lors de la compilation croisée.  Ajoutez-le simplement au fichier `project.json` comme attribut `buildOptions` :

```json
{
    "frameworks":{
        "netstandard1.6":{
           "dependencies":{
                "NETStandard.Library":"1.6.0",
            }
        },
        ".NETPortable,Version=v4.0,Profile=Profile328":{
            "buildOptions": {
                "define": [ "PORTABLE328" ]
            },
            "frameworkAssemblies":{
                "mscorlib":"",
                "System":"",
                "System.Core":"",
                "System.Net"
            }
        }
    }
}

```

Vous pouvez maintenant effectuer une compilation conditionnelle sur cette cible :

```csharp
#if !PORTABLE328
using System.Net.Http;
using System.Threading.Tasks;
// Potentially other namespaces which aren't compatible with Profile 328
#endif
```

Étant donné que `PORTABLE328` est maintenant reconnu par le compilateur, la bibliothèque du profil PCL 328 générée par un compilateur n’inclut ni `System.Net.Http` ni `System.Threading.Tasks`.

Quand vous générez un projet qui inclut le profil PCL 328 et `netstandard1.6` comme frameworks dans le fichier *project.json*, celui-ci comprend les sous-dossiers suivants dans le dossier */bin/debug* :

```
portable-net40+sl50+netcore45+wpa81+wp8/
netstandard1.6/
```

## <a name="how-to-use-native-dependencies"></a>Comment utiliser des dépendances natives

Vous souhaiterez peut-être écrire une bibliothèque qui dépend d’un fichier `.dll` natif.  Si vous écrivez une telle bibliothèque, vous avez deux options :

1. Référencez le fichier `.dll` natif directement dans votre `project.json`.
2. Créez un package du fichier `.dll` dans son propre package NuGet ainsi qu’une dépendance à ce package.

Pour la première option, vous devez inclure les éléments suivants dans votre fichier `project.json` :

1. Définition de `allowUnsafe` avec la valeur `true` dans une section `buildOptions`.
2. Spécification d’un [identificateur de runtime (RID)](../rid-catalog.md) dans une section `runtimes`.
3. Spécification du chemin vers le ou les fichiers `.dll` natifs que vous référencez.

Voici un exemple de `project.json` pour un fichier `.dll` natif dans le répertoire racine du projet qui s’exécute sur Windows :

```json
{
    "buildOptions":{
        "allowUnsafe":true
    },
    "runtimes":{
        "win10-x64":{}
    },
    "packOptions":{
        "files":{
            "mappings":{
                "runtimes/win10-x64/native":{
                    "includeFiles":[ "native-lib.dll"]
                }
            }            
        }
    }
}
```

Si vous distribuez votre bibliothèque en tant que package, il est recommandé de placer le fichier `.dll` à la racine de votre projet.

Pour la deuxième option, vous devez générer un package NuGet à partir de votre ou vos fichiers `.dll`, hébergez-le sur un flux NuGet ou MyGet, puis créez une dépendance directe dessus.  Vous devez toujours définir `allowUnsafe` avec la valeur `true` dans la section `buildOptions` de votre `project.json`.  Voici un exemple (en supposant que `MyNativeLib` est un package Nuget dont la version est `1.2.0`) :

```json
{
    "buildOptions":{
        "allowUnsafe":true
    },
    "dependencies":{
        "MyNativeLib":"1.2.0"
    }
}
```

Pour voir un exemple de package de binaires natifs multiplateformes, consultez [ASP.NET Libuv Package](https://github.com/aspnet/libuv-package) et la [référence correspondante dans KestrelHttpServer](https://github.com/aspnet/KestrelHttpServer/blob/1.0.0/src/Microsoft.AspNetCore.Server.Kestrel/project.json#L19).

## <a name="how-to-test-libraries-on-net-core"></a>Comment tester les bibliothèques sur .NET Core

Il est important de pouvoir effectuer des tests sur plusieurs plateformes.  Le plus facile est d’utiliser [xUnit](http://xunit.github.io/), qui est également l’outil de test utilisé par les projets .NET Core.  La façon dont vous configurez votre solution avec des projets de test dépend de la [structure de votre solution](#structuring-a-solution).  L’exemple suivant suppose que tous les projets sources se trouvent sous un dossier `/src` de niveau supérieur et que tous les projets de test se trouvent sous un dossier `/test` de niveau supérieur.

1. Assurez-vous d’avoir un fichier `global.json` au niveau de la solution qui comprend où se trouvent les projets de test :
    
    ```json
    {
        "projects":[ "src", "test"]
    }
    ```
    
    Votre structure de dossier de solution doit alors ressembler à ceci :
    
    ```
    /SolutionWithSrcAndTest
    |__global.json
    |__/src
    |__/test
    ```
    
2. Créez un projet de test en créant un dossier de projet sous votre dossier `/test` et un fichier `project.json` dans le nouveau dossier de projet.  Pour créer le fichier `project.json`, vous pouvez exécuter la commande `dotnet new` et modifier ensuite le fichier `project.json`.  Le fichier doit comporter les éléments suivants :

   * `netcoreapp1.0` répertorié comme entrée unique sous `frameworks`.
   * Une référence à `Microsoft.NETCore.App` version `1.0.0`.
   * Une référence à xUnit version `2.2.0-beta2-build3300`.
   * Une référence à la version `2.2.0-preview2-build1029` de `dotnet-test-xunit`
   * Une référence de projet à la bibliothèque en cours de test.
   * L’entrée `"testRunner":"xunit"`.
   
   Voici un exemple (`LibraryUnderTest` version `1.0.0` est la bibliothèque en cours de test) :
   
   ```json
   {
        "testRunner":"xunit",
        "dependencies":{
            "LibraryUnderTest":{
                "version":"1.0.0",
                "target":"project"
            },
            "Microsoft.NETCore.App":{
                "version":"1.0.0",
                "type":"platform"
            },
            "xunit":"2.2.0-beta2-build3300",
            "dotnet-test-xunit":"2.2.0-preview2-build1029",
        },
        "frameworks":{
            "netcoreapp1.0":{}
        }
   }
   ```
3. Restaurez les packages en exécutant `dotnet restore`.  Vous devez effectuer cette opération au niveau de la solution si vous n’avez pas encore restauré de packages.

4. Accédez à votre projet de test et exécutez les tests avec `dotnet test` :

    ```
    $ cd path-to-your-test-project
    $ dotnet test
    ```

Et voilà !  Vous pouvez maintenant tester votre bibliothèque sur toutes les plateformes à l’aide des outils en ligne de commande.  Maintenant que vous avez tout configuré, le test de votre bibliothèque est très simple :

1. Apportez des modifications à votre bibliothèque.
2. Exécutez les tests à partir de la ligne de commande, dans votre répertoire de test, avec la commande `dotnet test`.

Votre code est automatiquement régénéré quand vous appelez la commande `dotnet test`.

N’oubliez pas d’exécuter `dotnet restore` à partir de la ligne de commande chaque fois que vous ajoutez une nouvelle dépendance, après quoi vous aurez fini !

## <a name="how-to-use-multiple-projects"></a>Comment utiliser plusieurs projets

Les bibliothèques plus volumineuses ont souvent besoin de placer des fonctionnalités dans différents projets.

Imaginez que vous vouliez créer une bibliothèque pouvant être utilisée en langage C# et F#.  Cela signifierait que les consommateurs de votre bibliothèque les utilisent dans des formes qui sont naturelles en C# ou F#.  Par exemple, en C#, vous pouvez utiliser la bibliothèque de la façon suivante :

```csharp
var convertResult = await AwesomeLibrary.ConvertAsync(data);
var result = AwesomeLibrary.Process(convertResult);
```  

En F#, le code peut se présenter comme suit :

```fsharp
let result =
    data
    |> AwesomeLibrary.convertAsync 
    |> Async.RunSynchronously 
    |> AwesomeLibrary.process
```

Les scénarios de consommation tels que celui-ci signifient que les API auxquelles vous accédez ont une structure différente en C# et F#.  Pour réaliser ceci, il est courant de factoriser toute la logique d’une bibliothèque dans un projet principal et d’avoir des projets C# et F# définissant les couches API qui effectuent des appels à ce projet principal.  Le reste de la section utilise les noms suivants :

* **AwesomeLibrary.Core** : projet principal qui contient toute la logique de la bibliothèque
* **AwesomeLibrary.CSharp** : projet avec des API publiques destinées à être consommées en C#
* **AwesomeLibrary.CSharp** : projet avec des API publiques destinées à être consommées en C#

### <a name="project-to-project-referencing"></a>Références entre projets

La meilleure façon de référencer un projet consiste à effectuer les opérations suivantes :

1. Vérifiez que le projet que vous voulez référencer a un nom de dossier conteneur approprié sur le disque.  Ce sera le nom utilisé pour référencer votre projet.
2. Référencez le nom de (1) dans le fichier `project.json` du projet de consommation en spécifiant `"target":"project"`.

Les fichiers `project.json` pour à la fois **AwesomeLibrary.CSharp** et **AwesomeLibrary.FSharp** doivent maintenant référencer **AwesomeLibrary.Core** comme cible `project`.  Si vous n’effectuez pas de multiciblage, vous pouvez utiliser l’entrée `dependencies` globale :

```json
{
    "dependencies":{
        "AwesomeLibrary.Core":{
            "target":"project"
        }
    }
}
```

Si vous effectuez un multiciblage, vous ne pourrez peut-être pas utiliser une entrée `dependencies` globale et vous devrez alors référencer **AwesomeLibrary.Core** dans une entrée `dependencies` au niveau de la cible.  Par exemple, si votre cible était `netstandard1.6`, vous pouvez effectuer cette opération ainsi :

```json
{
    "frameworks":{
        "netstandard1.6":{
            "dependencies":{
                "AwesomeLibrary.Core":{
                    "target":"project"
                }
            }
        }
    }
}
```

### <a name="structuring-a-solution"></a>Structuration d’une solution

Un autre aspect important des solutions à projets multiples est la mise en place d’une bonne structure de projet globale. Pour structurer une bibliothèque à projets multiples, vous devez utiliser les dossiers `/src` et `/test` de niveau supérieur :

```
/AwesomeLibrary
|__global.json
|__/src
   |__/AwesomeLibrary.Core
      |__Source Files
      |__project.json
   |__/AwesomeLibrary.CSharp
      |__Source Files
      |__project.json
   |__/AwesomeLibrary.FSharp
      |__Source Files
      |__project.json
|__/test
   |__/AwesomeLibrary.Core.Tests
      |__Test Files
      |__project.json
   |__/AwesomeLibrary.CSharp.Tests
      |__Test Files
      |__project.json
   |__/AwesomeLibrary.FSharp.Tests
      |__Test Files
      |__project.json
```

Le fichier `global.json` de cette solution ressemble à ceci :

```json
{
    "projects":["src", "test"]
}
```

Cette approche suit le même modèle que celui établi par les modèles de projet dans la commande `dotnet new`, où tous les projets sont placés sous un répertoire `/src` et où tous les tests sont placés sous un répertoire `/test`.

Voici comment vous pouvez restaurer des packages, ainsi que générer et tester l’ensemble de votre projet :

```
$ dotnet restore
$ cd src/AwesomeLibrary.FSharp
$ dotnet build
$ cd ../AwesomeLibrary.CSharp
$ dotnet build
$ cd ../../test/AwesomeLibrary.Core.Tests
$ dotnet test
$ cd ../AwesomeLibrary.CSharp.Tests
$ dotnet test
$ cd ../AwesomeLibrary.FSharp.Tests
$ dotnet test
```

Et voilà !

