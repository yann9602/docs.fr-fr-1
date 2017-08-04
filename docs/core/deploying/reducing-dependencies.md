---
title: "Réduction des dépendances de package avec project.json"
description: "Réduisez les dépendances de package dans le cadre de la création de bibliothèques project.json."
keywords: .NET, .NET Core
author: cartermp
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 916251e3-87f9-4eee-81ec-94076215e6fa
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 23d83f0402e35bc4bed31ef59a6fff0e28e01d35
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---

# <a name="reducing-package-dependencies-with-projectjson"></a>Réduction des dépendances de package avec project.json

Cet article décrit ce que vous devez savoir sur la réduction de vos dépendances de package lors de la création de bibliothèques `project.json`. À la fin de cet article, vous saurez comment composer votre bibliothèque de sorte qu’elle utilise seulement les dépendances dont elle a besoin. 

## <a name="why-its-important"></a>Pourquoi c’est important

.NET Core est un produit composé de packages NuGet.  Parmi les packages essentiels figure le [métapackage .NETStandard.Library](https://www.nuget.org/packages/NETStandard.Library), un package NuGet composé d’autres packages.  Il vous fournit l’ensemble des packages dont le fonctionnement est garanti sur plusieurs implémentations de .NET, comme le .NET Framework, .NET Core et Xamarin/Mono.

Cependant, il est probable que votre bibliothèque n’utilise pas chaque package individuel qu’il contient.  Lors de la création d’une bibliothèque et de sa distribution sur NuGet, il est conseillé de « réduire » vos dépendances aux seuls packages que vous utilisez.  Ceci aboutit à un encombrement global inférieur pour les packages NuGet.

## <a name="how-to-do-it"></a>Comment faire

Il n’existe actuellement aucune commande `dotnet` officielle qui réduit les références de package.  Vous devez donc le faire manuellement.  Le processus général se présente comme suit :

1. Faites référence à `NETStandard.Library` version `1.6.0` dans une section `dependencies` de votre fichier `project.json`.
2. Restaurer les packages avec `dotnet restore` à partir de la ligne de commande.
3. Parcourez le fichier `project.lock.json` et recherchez la section `NETSTandard.Library`.  Elle est au début du fichier.
4. Copiez tous les packages répertoriés sous `dependencies`.
5. Supprimez la référence à `.NETStandard.Library` et remplacez-la par les packages copiés.
6. Supprimez les références aux packages dont vous n’avez pas besoin.

Vous pouvez déterminer les packages dont vous n’avez pas besoin de l’une des façons suivantes :

1. Essai et erreur.  Ceci implique de supprimer un package, de le restaurer, de déterminer si votre bibliothèque se compile encore et de répéter ce processus.
2. L’utilisation d’un outil comme [ILSpy](http://ilspy.net) ou [.NET Reflector](http://www.red-gate.com/products/dotnet-development/reflector) permet d’examiner les références pour voir ce que votre code utilise réellement.  Vous pouvez ensuite supprimer les packages qui ne correspondent pas aux types que vous utilisez.

## <a name="example"></a>Exemple 

Imaginez que vous avez écrit une bibliothèque qui fournit des fonctionnalités supplémentaires pour les types de collections génériques.  Ce type de bibliothèque doit dépendre de packages comme `System.Collections`, mais peut ne pas du tout dépendre de packages comme `System.Net.Http`.  Par conséquent, il serait judicieux de réduire les dépendances des packages aux seuls packages dont cette bibliothèque a besoin !

Pour réduire cette bibliothèque, vous commencez par le fichier `project.json` et vous ajoutez une référence à `NETStandard.Library` version `1.6.0`.

```json
{
    "version":"1.0.0",
    "dependencies":{
        "NETStandard.Library":"1.6.0"
    },
    "frameworks": {
        "netstandard1.0": {}
     }
}
```

Ensuite, vous restaurez les packages avec `dotnet restore`, vous examinez le fichier `project.lock.json` et vous recherchez tous les packages restaurés pour `NETSTandard.Library`.

Voici à quoi ressemble la section appropriée du fichier `project.lock.json` quand vous ciblez `netstandard1.0` :

```json
"NETStandard.Library/1.6.0":{
    "type": "package",
    "dependencies": {
        "Microsoft.NETCore.Platforms": "1.0.1",
        "Microsoft.NETCore.Runtime": "1.0.2",
        "System.Collections": "4.0.11",
        "System.Diagnostics.Debug": "4.0.11",
        "System.Diagnostics.Tools": "4.0.1",
        "System.Globalization": "4.0.11",
        "System.IO": "4.1.0",
        "System.Linq": "4.1.0",
        "System.Net.Primitives": "4.0.11",
        "System.ObjectModel": "4.0.12",
        "System.Reflection": "4.1.0",
        "System.Reflection.Extensions": "4.0.1",
        "System.Reflection.Primitives": "4.0.1",
        "System.Resources.ResourceManager": "4.0.1",
        "System.Runtime": "4.1.0",
        "System.Runtime.Extensions": "4.1.0",
        "System.Text.Encoding": "4.0.11",
        "System.Text.Encoding.Extensions": "4.0.11",
        "System.Text.RegularExpressions": "4.1.0",
        "System.Threading": "4.0.11",
        "System.Threading.Tasks": "4.0.11",
        "System.Xml.ReaderWriter": "4.0.11",
        "System.Xml.XDocument": "4.0.11"
    }
}
```

Ensuite, copiez les références de package dans la section `dependencies` du fichier `project.json` de la bibliothèque, en remplaçant la référence `NETStandard.Library` :

```json
{
    "version":"1.0.0",
    "dependencies":{
        "Microsoft.NETCore.Platforms": "1.0.1",
        "Microsoft.NETCore.Runtime": "1.0.2",
        "System.Collections": "4.0.11",
        "System.Diagnostics.Debug": "4.0.11",
        "System.Diagnostics.Tools": "4.0.1",
        "System.Globalization": "4.0.11",
        "System.IO": "4.1.0",
        "System.Linq": "4.1.0",
        "System.Net.Primitives": "4.0.11",
        "System.ObjectModel": "4.0.12",
        "System.Reflection": "4.1.0",
        "System.Reflection.Extensions": "4.0.1",
        "System.Reflection.Primitives": "4.0.1",
        "System.Resources.ResourceManager": "4.0.1",
        "System.Runtime": "4.1.0",
        "System.Runtime.Extensions": "4.1.0",
        "System.Text.Encoding": "4.0.11",
        "System.Text.Encoding.Extensions": "4.0.11",
        "System.Text.RegularExpressions": "4.1.0",
        "System.Threading": "4.0.11",
        "System.Threading.Tasks": "4.0.11",
        "System.Xml.ReaderWriter": "4.0.11",
        "System.Xml.XDocument": "4.0.11"
    },
    "frameworks":{
        "netstandard1.0": {}
    }
}
```

Ceci représente beaucoup de packages, dont un grand nombre ne sont certainement pas nécessaires pour étendre les types de collections.  Vous pouvez supprimer manuellement les packages ou utiliser un outil comme [ILSpy](http://ilspy.net) ou [.NET Reflector](http://www.red-gate.com/products/dotnet-development/reflector) pour identifier les packages utilisés par votre code.

Voici ce à quoi un package réduit peut ressembler :

```json
{
    "dependencies":{
        "Microsoft.NETCore.Platforms": "1.0.1",
        "Microsoft.NETCore.Runtime": "1.0.2",
        "System.Collections": "4.0.11",
        "System.Linq": "4.1.0",
        "System.Runtime": "4.1.0",
        "System.Runtime.Extensions": "4.1.0",
        "System.Runtime.Handles": "4.0.1",
        "System.Runtime.InteropServices": "4.1.0",
        "System.Runtime.InteropServices.RuntimeInformation": "4.0.0",
        "System.Threading.Tasks": "4.0.11"
    },
    "frameworks":{
        "netstandard1.0": {}
     }
}
```

Il a maintenant un encombrement moindre que s’il dépendait du métapackage `NETStandard.Library`.

