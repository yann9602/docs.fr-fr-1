---
title: "Packages, métapackages et frameworks"
description: "Packages, métapackages et frameworks"
keywords: .NET, .NET Core
author: richlander
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 609b0845-49e7-4864-957b-21ffe1b93bf2
translationtype: Human Translation
ms.sourcegitcommit: 3845ec46cbd1f65abd9b78f7b81487efed9de2f2
ms.openlocfilehash: 9cb957973e68129194c998c88e398351b48819ec
ms.lasthandoff: 03/13/2017

---

# <a name="packages-metapackages-and-frameworks"></a>Packages, métapackages et frameworks

.NET Core est une plateforme constituée de packages NuGet. Certains produits bénéficient d’une définition de packages très précise, d’autres d’une définition plus grossière. Pour prendre en compte cette dualité, le produit est distribué sous forme d’un ensemble précis de packages, puis décrit en blocs plus grossiers avec un type de package familièrement appelé « métapackage ».

Chaque package .NET Core peut être exécuté sur plusieurs runtimes .NET, représentées par des frameworks. Certains d’entre eux sont des frameworks classiques, comme `net46`, représentant le .NET Framework. D’autres sont de nouveaux frameworks qui peuvent s’envisager comme des « frameworks basés sur des packages », qui établissent un nouveau modèle de définition de frameworks. Ces frameworks basés sur des packages sont entièrement formés et définis comme packages, formant ainsi une relation forte entre les packages et les frameworks.

## <a name="packages"></a>Packages

.NET Core se divise en un ensemble de packages qui fournissent des primitives, des types de données généraux, des types de composition d’applications et des utilitaires communs. Chacun de ces packages représente un assembly unique de même nom. Par exemple, [System.Runtime](https://www.nuget.org/packages/System.Runtime) contient System.Runtime.dll. 

Il y a des avantages à définir les packages avec précision :

- Les packages définis avec précision peuvent être émis selon un calendrier qui leur est propre en ayant relativement peu testé d’autres packages.
- Ils peuvent offrir une prise en charge de systèmes d’exploitation et de processeurs différents.
- Ils peuvent avoir des dépendances spécifiques à une seule bibliothèque.
- Les applications sont plus petites, car les packages non référencés ne sont pas distribués avec elles.

Certains de ces avantages ne sont profitables que dans certaines circonstances. Par exemple, les packages .NET Core sont généralement émis selon le même calendrier avec la même prise en charge de plateforme. Dans le cas de la maintenance, des correctifs peuvent être distribués et installés sous forme de petites mises à jour de package uniques. En raison de la portée limitée des modifications, la validation et le délai de mise à disposition d’un correctif sont limitées au strict nécessaire pour une même bibliothèque.

Voici la liste des principaux packages NuGet pour .NET Core :

- [System.Runtime](https://www.nuget.org/packages/System.Runtime) : package .NET Core le plus fondamental, comprenant [Object](http://docs.microsoft.com/dotnet/core/api/System.Object), [String](http://docs.microsoft.com/dotnet/core/api/System.String), [Array](http://docs.microsoft.com/dotnet/core/api/System.Array), [Action](http://docs.microsoft.com/dotnet/core/api/System.Action) et [IList&lt;T&gt;](http://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.IList-1).
- [System.Collections](https://www.nuget.org/packages/System.Collections) : ensemble de collections (principalement) génériques, notamment [List&lt;T&gt;](http://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.List-1) et [Dictionary&lt;K, V&gt;](http://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.Dictionary-2).
- [System.Net.Http](https://www.nuget.org/packages/System.Net.Http) : ensemble de types pour les communications réseau HTTP, notamment [HttpClient](http://docs.microsoft.com/dotnet/core/api/System.Net.Http.HttpClient) et [HttpResponseMessage](http://docs.microsoft.com/dotnet/core/api/System.Net.Http.HttpResponseMessage).
- [System.IO.FileSystem](https://www.nuget.org/packages/System.IO.FileSystem) : ensemble de types pour la lecture et l’écriture dans un stockage sur disque local ou en réseau, dont [File](http://docs.microsoft.com/dotnet/core/api/System.IO.File) et [Directory](http://docs.microsoft.com/dotnet/core/api/System.IO.Directory).
- [System.Linq](https://www.nuget.org/packages/System.Linq) : ensemble de types pour l’interrogation d’objets, notamment Enumerable et [ILookup&lt;TKey, TElement&gt;](http://docs.microsoft.com/dotnet/core/api/System.Linq.ILookup-2).
- [System.Reflection](https://www.nuget.org/packages/System.Reflection) : ensemble de types pour le chargement, l’inspection et l’activation de types, dont [Assembly](http://docs.microsoft.com/dotnet/core/api/System.Reflection.Assembly), [TypeInfo](http://docs.microsoft.com/dotnet/core/api/System.Reflection.TypeInfo) et [MethodInfo](http://docs.microsoft.com/dotnet/core/api/System.Reflection.MethodInfo).

En général, au lieu d’inclure des packages dans vos projets un par un, il est beaucoup plus facile d’inclure un *métapackage*, qui est un ensemble de packages souvent traités conjointement. (Pour plus d'informations sur les métapackages, consultez la section suivante.) Toutefois, quand vous avez besoin d’un seul package, vous pouvez l’inclure de la même manière que dans l’exemple ci-dessous, qui référence le package [System.Runtime](https://www.nuget.org/packages/System.Runtime/). 

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netstandard1.6</TargetFramework>
  </PropertyGroup>
  <ItemGroup>
    <PackageReference Include="System.Runtime" Version="4.3.0" />
  </ItemGroup>
</Project>
```

## <a name="metapackages"></a>Métapackages

Les métapackages sont une convention de packages NuGet qui vise à décrire un ensemble de packages qu’il est logique de regrouper. Ils représentent cet ensemble de packages sous forme de dépendances. Ils peuvent éventuellement établir un cadre pour cet ensemble de packages en spécifiant un framework. 

Les versions précédentes des outils .NET Core (les outils project.json et csproj) spécifiaient par défaut un framework et un métapackage. Actuellement, toutefois, le métapackage est implicitement référencé par le framework cible, de sorte que chaque métapackage est lié à un framework cible. Par exemple, le framework `netstandard1.6` référence le métapackage NetStandard.Library version 1.6.0. De même, le framework `netcoreapp1.1` référence le métapackage Microsoft.NETCore.App version 1.1.0. Pour plus d’informations, consultez [Implicit metapackage package reference in the .NET Core SDK](https://github.com/dotnet/core/blob/master/release-notes/1.0/sdk/1.0-rc3-implicit-package-refs.md) (Référence de package métapackage implicite dans le SDK .NET Core).

En ciblant un framework et en référençant implicitement un métapackage, vous ajoutez une référence à chacun de ses packages dépendants en une seule fois. De cette façon, toutes les bibliothèques contenues dans ces packages sont disponibles pour IntelliSense (ou une expérience similaire) et pour la publication de votre application.  

L’utilisation de métapackages confère les avantages suivants :

- Fournit une expérience utilisateur pratique pour référencer un ensemble étoffé de packages définis avec précision. 
- Définit un ensemble de packages (comprenant des versions spécifiques) qui ont été testés et fonctionnent bien ensemble.

Le métapackage de la bibliothèque .NET Standard est le suivant :

- [NETStandard.Library](https://www.nuget.org/packages/NETStandard.Library) : décrit les bibliothèques qui font partie de la « bibliothèque .NET Standard ». S’applique à toutes les implémentations .NET (par exemple, .NET Framework, .NET Core et Mono) qui prennent en charge la bibliothèque .NET Standard. Établit le framework « netstandard ».

Les principaux métapackages .NET Core sont les suivants :

- [Microsoft.NETCore.App](https://www.nuget.org/packages/Microsoft.NETCore.App) : décrit les bibliothèques qui font partie de la distribution .NET Core. Établit le [`.NETCoreApp`framework](https://github.com/dotnet/core-setup/blob/master/pkg/projects/Microsoft.NETCore.App/Microsoft.NETCore.App.pkgproj). Dépend de la bibliothèque `NETStandard.Library` (plus petite).
- [Microsoft.NETCore.Portable.Compatibility](https://www.nuget.org/packages/Microsoft.NETCore.Portable.Compatibility) : ensemble de façades de compatibilité qui permettent aux bibliothèques de classes portables (PCL) basées sur mscorlib de s’exécuter sur .NET Core.

## <a name="frameworks"></a>Frameworks

Chaque package .NET Core prend en charge un ensemble de frameworks de runtime. Les frameworks décrivent un ensemble d’API disponibles (et éventuellement d’autres caractéristiques) sur lesquelles vous pouvez vous appuyer quand vous ciblez un framework donné. Leur version change à mesure que de nouvelles API sont ajoutés.

Par exemple, [System.IO.FileSystem](https://www.nuget.org/packages/System.IO.FileSystem) prend en charge les frameworks suivants :

- .NETFramework,Version=4.6
- .NETStandard,Version=1.3
- 6 plateformes Xamarin (par exemple, xamarinios10)

Il est utile de comparer les deux premiers frameworks, car ils représentent des exemples des deux manières de définir des frameworks.

Le framework `.NETFramework,Version=4.6` représente les API disponibles dans le .NET Framework 4.6. Vous pouvez produire des bibliothèques compilées avec les assemblys de référence du .NET Framework 4.6, puis distribuer ces bibliothèques dans des packages NuGet dans un dossier lib net46. Elle servira aux applications qui ciblent le .NET Framework 4.6 ou qui sont compatibles avec celui-ci. C’est ainsi que l’ensemble des frameworks fonctionne habituellement.

`.NETStandard,Version=1.3` est un framework basé sur des packages. Il s’appuie sur des packages qui ciblent le framework pour définir et exposer des interfaces API selon le framework.

## <a name="package-based-frameworks"></a>Frameworks basés sur des packages

Il existe une relation réciproque entre les frameworks et les packages. La première partie consiste à définir les API accessibles à un framework donné, par exemple `netstandard1.3`. Les packages qui ciblent `netstandard1.3` (ou des frameworks compatibles tels que `netstandard1.0`) définissent les API disponibles pour `netstandard1.3`. On pourrait croire à première vue qu’il s’agit d’une définition circulaire, mais il n’en est rien. Étant « basée sur des packages », la définition d’API pour le framework est issue de packages. Le framework lui-même ne définit pas d’API.

La deuxième partie de la relation est la sélection de ressource. Les packages peuvent contenir des ressources pour plusieurs frameworks. Le framework est nécessaire pour déterminer quelle ressource sélectionner, par exemple `net46` ou `netstandard1.3`, pour une référence donnée à un ensemble de packages et/ou de métapackages. Il est important de sélectionner la ressource adéquate. Par exemple, il est peu probable qu’une ressource `net46` soit compatible avec le .NET Framework 4.0 ou .NET Core 1.0.

![Composition d’un framework basé sur des packages](./media/packages/package-framework.png)

Cette relation est illustrée dans l’image ci-dessus. L’*API* cible et définit le *framework*. Le *framework* est utilisé pour la *sélection de ressource*. La *ressource* vous fournit l’API.

Les deux principaux frameworks basés sur des packages utilisés avec .NET Core sont les suivants :

- `netstandard`
- `netcoreapp`

### <a name="net-standard"></a>.NET Standard

Le framework .NET Standard (moniker du framework cible : `netstandard`) représente les API définies par et créées par-dessus la [bibliothèque .NET Standard](../standard/library.md). Les bibliothèques destinées à s’exécuter sur plusieurs runtimes doivent cibler ce framework. Elles sont prises en charge sur n’importe quel runtime compatible .NET Standard, tels que .NET Core, .NET Framework et Mono/Xamarin. Chacun de ces runtimes prend en charge un ensemble de versions .NET Standard, selon les API qu’ils implémentent. 

Le framework `netstandard` référence implicitement le métapackage `NETStandard.Library`. Par exemple, le fichier projet MSBuild suivant indique que le projet cible `netstandard1.6`, qui référence le métapackage de la bibliothèque .NET Standard version 1.6. 

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netstandard1.6</TargetFramework>
  </PropertyGroup>
</Project>
```

Toutefois, les références de framework et de métapackage dans le fichier projet ne doivent pas nécessairement correspondre et vous pouvez utiliser l’élément `<NetStandardImplicitPackageVersion>` dans votre fichier projet pour spécifier une version de framework inférieure à la version de métapackage. Par exemple, le fichier projet suivant est valide.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netstandard1.3</TargetFramework>
  </PropertyGroup>
  <ItemGroup>
    <NetStandardImplicitPackageVersion Include="NetStandardLibrary" Version="1.6.0" />
  </ItemGroup>
</Project>
```

Il peut sembler étrange de cibler `netstandard1.3`, mais d’utiliser la version 1.6.0 de `NETStandard.Library`. Il s’agit d’un cas d’utilisation valide, car le métapackage maintient la prise en charge pour les anciennes versions de `netstandard`. Vous pouvez avoir procédé à une uniformisation sur la version 1.6.0 du métapackage et l’utiliser pour toutes vos bibliothèques, qui ciblent diverses versions de `netstandard`. Avec cette approche, vous avez seulement besoin de restaurer `NETStandard.Library` 1.6.0 et pas les versions antérieures. 

L’inverse ne serait pas valide : le ciblage de `netstandard1.6` avec la version 1.3.0 de `NETStandard.Library`. Vous ne pouvez pas cibler un framework de version supérieure avec un métapackage de version inférieure, car ce dernier n’expose aucune ressource pour le framework de version supérieure. Le schéma de gestion de version des métapackages certifie que les métapackages correspondent à la version la plus récente du framework qu’ils décrivent. Grâce au schéma de gestion de version, la première version de `NETStandard.Library` est v1.6.0, étant donné qu’elle contient des ressources `netstandard1.6`. La version 1.3.0 est utilisée dans l’exemple ci-dessus dans un souci de symétrie par rapport à l’exemple précédent, mais elle n’existe pas dans la réalité.

### <a name="net-core-application"></a>Application .NET Core

Le framework d’application .NET Core (TFM : `netcoreapp`) représente les packages et les API associées qui accompagnent la distribution .NET Core et le modèle d’application console qu’il propose. Les applications .NET Core doivent utiliser ce framework, en raison du ciblage du modèle d’application console, tout comme les bibliothèques destinées à s’exécuter uniquement sur .NET Core. L’utilisation de ce framework contraint les applications et les bibliothèques à s’exécuter uniquement sur .NET Core. 

Le métapackage `Microsoft.NETCore.App` cible le framework `netcoreapp`. Il donne accès à une soixantaine de bibliothèques, dont une quarantaine est fournie par le package `NETStandard.Library`, à laquelle s’ajoute une vingtaine de bibliothèques supplémentaires. Vous pouvez référencer des bibliothèques supplémentaires qui ciblent `netcoreapp` ou des frameworks compatibles, telles que `netstandard`, pour avoir accès à des API supplémentaires. 

La plupart des bibliothèques supplémentaires fournies par `Microsoft.NETCore.App` ciblent aussi `netstandard`, vu que leurs dépendances sont satisfaites par d’autres bibliothèques `netstandard`. Cela signifie que les bibliothèques `netstandard` peuvent aussi référencer ces packages comme dépendances. 

