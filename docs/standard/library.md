---
title: "Bibliothèque .NET Standard"
description: "Bibliothèque .NET Standard"
keywords: .NET, .NET Core
author: richlander
manager: wpickett
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: c044882c-af15-45f2-96d1-534557a5ee9b
translationtype: Human Translation
ms.sourcegitcommit: f9ffbb2e300df2080276096095a7269736260ba1
ms.openlocfilehash: ff61319f15fea4c838517ed209e8095b37186c2e

---

# <a name="net-standard-library"></a>Bibliothèque .NET Standard

La bibliothèque .NET Standard est une spécification formelle des API .NET qui sont destinées à être disponibles sur tous les runtimes .NET. La motivation derrière la bibliothèque standard consiste à établir une meilleure uniformité dans l’écosystème .NET. [ECMA 335](https://github.com/dotnet/coreclr/blob/master/Documentation/project-docs/dotnet-standards.md) continue d’établir l’uniformité du comportement du runtime .NET, mais il n’existe aucune spécification similaire pour les bibliothèques de classes de base .NET en ce qui concerne les implémentations de bibliothèque .NET. 

La bibliothèque .NET Standard permet les scénarios clés suivants : 

- Définit un ensemble uniforme d’API de bibliothèque de classes de base pour toutes les plateformes .NET à implémenter, indépendamment de la charge de travail.
- Permet aux développeurs de générer des bibliothèques portables utilisables sur tous les runtimes .NET, à l’aide de ce même ensemble d’API.
- Réduit et éventuellement élimine une compilation conditionnelle de source partagée résultant des API .NET, uniquement pour les API de système d’exploitation.

Les différents runtimes .NET implémentent des versions spécifiques de la bibliothèque .NET Standard. Chaque version du runtime .NET publie la version la plus récente de .NET Standard qu’elle prend en charge, une instruction qui signifie qu’elle prend également en charge les versions précédentes. Par exemple, le .NET Framework 4.6 implémente la bibliothèque .NET Standard 1.3, ce qui signifie qu’il expose toutes les API définies dans les versions 1.0 à 1.3 de la bibliothèque .NET Standard. De même, le .NET Framework 4.6.2 implémente la bibliothèque .NET Standard 1.5, tandis que .NET Core 1.0 implémente la bibliothèque .NET Standard 1.6.

## <a name="net-platforms-support"></a>Prise en charge des plateformes .NET

Vous pouvez voir l’ensemble des runtimes .NET qui prennent en charge la bibliothèque .NET Standard.

| Nom de la plateforme | Alias |  |  |  |  |  | | | |
| :---------- | :--------- |:--------- |:--------- |:--------- |:--------- |:--------- |:--------- |:--------- |:--------- |
|.NET Standard | netstandard | 1.0 | 1.1 | 1.2 | 1.3 | 1.4 | 1,5 | 1.6 | 2.0 |
|.NET Core|netcoreapp|&rarr;|&rarr;|&rarr;|&rarr;|&rarr;|&rarr;|1.0|vNext|
|.NET Framework|net|&rarr;|4.5|4.5.1|4.6|4.6.1|4.6.2|vNext|4.6.1|
|Plateformes Mono/Xamarin||&rarr;|&rarr;|&rarr;|&rarr;|&rarr;|&rarr;|&rarr;|vNext|
|Plateforme Windows universelle|uap|&rarr;|&rarr;|&rarr;|&rarr;|10.0|&rarr;|&rarr;|vNext|
|Windows|win|&rarr;|8.0|8.1||||||
|Windows Phone|wpa|&rarr;|&rarr;|8.1||||||
|Windows Phone Silverlight|wp|8.0||||||||

## <a name="comparison-to-portable-class-libraries"></a>Comparaison avec les bibliothèques de classes portables

La bibliothèque .NET Standard peut être imaginée comme la nouvelle génération de [bibliothèques de classes portables](https://msdn.microsoft.com/library/gg597391.aspx). La bibliothèque .NET Standard améliore l’expérience de création des bibliothèques portables en organisant une bibliothèque de classes de base et, par conséquent, en établissant une meilleure uniformité entre les runtimes .NET. Une bibliothèque qui cible la bibliothèque .NET Standard est une bibliothèque de classes portable ou une « bibliothèque de classes portable .NET Standard ». Les bibliothèques de classes portables existantes sont basées sur un profil.

La bibliothèque .NET Standard et les profils de bibliothèque de classes portable ont été créés pour des raisons similaires, mais diffèrent de manière significative.

Points communs :

- Définit les API qui peuvent être utilisées pour le partage de code binaire.

Différences :

- La bibliothèque .NET Standard est un ensemble organisé d’API, tandis que les profils de bibliothèque de classes portable sont définis par des intersections de plateformes existantes.
- La bibliothèque .NET Standard a des versions linéaires, contrairement aux profils de bibliothèque de classes portable.
- Les profils de bibliothèque de classes portable représentent les plateformes Microsoft alors que la bibliothèque .NET Standard est indépendante de la plateforme.

## <a name="specification"></a>Spécification

La spécification de la bibliothèque .NET Standard est un ensemble d’API normalisé. La spécification est gérée par les implémentations du runtime .NET, en particulier Microsoft (inclut le .NET Framework, .NET Core et Mono) et Unity. Un processus de commentaires publics est utilisé dans le cadre de l’établissement des nouvelles versions de la bibliothèque .NET Standard.

### <a name="official-artifacts"></a>Artefacts officiels

La spécification officielle est un ensemble de fichiers .cs qui définissent les API qui font partie de la norme. Le [répertoire ref](https://github.com/dotnet/corefx/tree/master/src/System.Runtime/ref) de chaque [composant](https://github.com/dotnet/corefx/tree/master/src) définit les API de la bibliothèque .NET Standard. Bien que les artefacts ref résident dans le [dépôt CoreFX](https://github.com/dotnet/corefx), ils ne sont pas spécifiques de .NET Core.

Le métapackage [NETStandard.Library](https://www.nuget.org/packages/NETStandard.Library) ([source](https://github.com/dotnet/corefx/blob/master/pkg/NETStandard.Library/NETStandard.Library.packages.targets)) décrit l’ensemble des bibliothèques qui définissent (en partie) une ou plusieurs versions de la bibliothèque .NET Standard.

Un composant donné, comme System.Runtime, décrit ce qui suit :

- Une partie de la bibliothèque .NET Standard (seulement sa portée).
- Plusieurs versions de la bibliothèque .NET Standard, pour cette portée.

Des artefacts dérivés sont fournis pour une lecture plus pratique et pour activer certains scénarios de développement (par exemple, utilisation d’un compilateur).

- Liste des API au format markdown (TBD)
- Assemblys de référence, distribués comme [packages NuGet](../core/packages.md) et référencés par le métapackage [NETStandard.Library](https://www.nuget.org/packages/NETStandard.Library/).

### <a name="package-representation"></a>Représentation de package

Le véhicule de distribution principal des assemblys de référence de la bibliothèque .NET Standard sont les [packages NuGet](../core/packages.md). Les implémentations sont fournies de façons différentes en fonction du runtime .NET.

Les packages NuGet ciblent un ou plusieurs [frameworks](frameworks.md). Les packages de la bibliothèque .NET Standard ciblent le framework «.NET Standard ». Vous pouvez cibler le .NET Framework Standard à l’aide du [Moniker de Framework cible compact](frameworks.md) `netstandard` (par exemple, `netstandard1.4`). Les bibliothèques destinées à s’exécuter sur plusieurs runtimes doivent cibler ce framework. 

Le métapackage `NETStandard.Library` référence l’ensemble complet des packages NuGet qui définissent la bibliothèque .NET Standard.  La méthode la plus courante pour cibler `netstandard` consiste à référencer ce métapackage. Il décrit la quarantaine de bibliothèques .NET et les API associées qui définissent la bibliothèque .NET Standard et y donne accès. Vous pouvez référencer d’autres packages qui ciblent `netstandard` pour avoir accès à d’autres API. 

### <a name="versioning"></a>Versioning

La spécification n’est pas singulière, mais représente un ensemble d’API dont la croissance est incrémentielle et les versions linéaires. La première version de la norme établit un ensemble d’API de référence. Les versions ultérieures ajoutent des API et héritent des API définies par les versions précédentes. Il n’existe aucune disposition établie pour supprimer des API de la norme.

La bibliothèque .NET Standard n’est pas spécifique d’un runtime .NET et ne correspond pas au schéma de version de ces runtimes.

Les API ajoutées à un runtime (par exemple, .NET Framework, .NET Core et Mono) peuvent être considérées comme des candidats à ajouter à la spécification, en particulier si elles sont jugées fondamentales. Des [versions de la bibliothèque .NET Standard](https://github.com/dotnet/corefx/blob/master/Documentation/architecture/net-platform-standard.md#list-of-net-corefx-apis-and-their-associated-net-platform-standard-version) sont créées en fonction des versions des runtimes .NET, ce qui vous permet de cibler les nouvelles API à partir d’une bibliothèque de classes portable .NET Standard. Les mécanismes du contrôle de version sont décrits plus en détail dans [Gestion de version .NET Core](../core/versions/index.md).

Le contrôle de version de la bibliothèque .NET Standard est important pour l’utilisation. Pour une version donnée de la bibliothèque .NET Standard, vous pouvez utiliser des bibliothèques qui ciblent cette même version ou une version antérieure. L’approche suivante décrit le flux de travail de l’utilisation des bibliothèques de classes portables .NET Standard, propre au ciblage de la bibliothèque .NET Standard.

- Sélectionnez une version de la bibliothèque .NET Standard à utiliser pour votre bibliothèque de classes portable.
- Utilisez des bibliothèques qui dépendent de la même version de la bibliothèque .NET Standard ou d’une version antérieure.
- Si vous trouvez une bibliothèque qui dépend d’une version ultérieure de la bibliothèque .NET Standard, vous devez adopter cette même version ou décider de ne pas utiliser cette bibliothèque.

### <a name="pcl-compatibility"></a>Compatibilité des bibliothèques de classes portables

La bibliothèque .NET Standard est compatible avec un sous-ensemble de profils de bibliothèque de classes portable. Les versions 1.0, 1.1 et 1.2 de la bibliothèque .NET Standard se chevauchent chacune avec un ensemble de profils de bibliothèque de classes portable. Ce chevauchement a été créé pour deux raisons :

- Permettre aux bibliothèques de classes portables .NET Standard de référencer les bibliothèques de classes portables basées sur un profil.
- Permettre aux bibliothèques de classes portables basées sur un profil d’être packagées comme des bibliothèques de classes portables .NET Standard.

La compatibilité des bibliothèques de classes portables est fournie par le package NuGet [Microsoft.NETCore.Portable.Compatibility](https://www.nuget.org/packages/Microsoft.NETCore.Portable.Compatibility). Cette dépendance est nécessaire quand vous référencez des packages NuGet qui contiennent des bibliothèques de classes portables basées sur un profil.

Les bibliothèques de classes portables basées sur un profil packagées en `netstandard` sont plus faciles à utiliser que les bibliothèques de classes portables basées sur un profil généralement packagées en project.json. Les packages `netstandard` sont compatibles avec les utilisateurs existants.

Voici l’ensemble des profils de bibliothèques de classes portables qui sont compatibles avec .NET Standard : 

| Profil | Version Standard de la plateforme .NET |
| ---------| --------------- |
| Profil7 - Sous-ensemble portable .NET (.NET Framework 4.5, Windows 8) | 1.1 |
| Profil31 - Sous-ensemble portable .NET (Windows 8.1, Windows Phone Silverlight 8.1)| 1.0 |
| Profil32 - Sous-ensemble portable .NET (Windows 8.1, Windows Phone 8.1) | 1.2 |
| Profil44 - Sous-ensemble portable .NET (.NET Framework 4.5.1, Windows 8.1) | 1.2 |
| Profil49 - Sous-ensemble portable .NET (.NET Framework 4.5, Windows Phone Silverlight 8) | 1.0 |
| Profil78 - Sous-ensemble portable .NET (.NET Framework 4.5, Windows 8, Windows Phone Silverlight 8) | 1.0 |
| Profil84 - Sous-ensemble portable .NET (Windows Phone 8.1, Windows Phone Silverlight 8.1) | 1.0 |
| Profil111 - Sous-ensemble portable .NET (.NET Framework 4.5, Windows 8, Windows Phone Silverlight 8.1) | 1.1 |
| Profil151 - Sous-ensemble portable .NET (.NET Framework 4.5.1, Windows 8.1, Windows Phone 8.1) | 1.2 |
| Profil157 - Sous-ensemble portable .NET (Windows 8.1, Windows Phone 8.1, Windows Phone Silverlight 8.1) | 1.0 |
| Profil259 - Sous-ensemble portable .NET (.NET Framework 4.5, Windows 8, Windows Phone 8.1, Windows Phone Silverlight 8) | 1.0 |

## <a name="targeting-net-standard-library"></a>Ciblage de la bibliothèque .NET Standard

Vous pouvez [créer des bibliothèques .NET Standard](../core/tutorials/libraries.md) en combinant le framework `netstandard` et le métapackage NETStandard.Library. Vous pouvez voir des exemples de [ciblage de la bibliothèque .NET Standard avec les outils .NET Core](../core/packages.md).



<!--HONumber=Nov16_HO1-->


