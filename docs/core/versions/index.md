---
title: Gestion de version .NET Core
description: Gestion de version .NET Core
keywords: .NET, .NET Core
author: richlander
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: f6f684b1-1d2c-4105-8376-7c1959e23803
translationtype: Human Translation
ms.sourcegitcommit: 3845ec46cbd1f65abd9b78f7b81487efed9de2f2
ms.openlocfilehash: 7be49f3ac7a7806e631eacf5004343919654881e
ms.lasthandoff: 04/05/2017

---

# <a name="net-core-versioning"></a>Gestion de version .NET Core

.NET Core est une plateforme constituée de [packages NuGet](../packages.md) et de frameworks, et qui est distribuée comme un ensemble. Chacune de ces couches de plate-forme peut être créée séparément pour une meilleure agilité du produit et pour décrire précisément les modifications apportées au produit. Même si la gestion de version est très flexible, il est souhaitable d’attribuer une version à l’ensemble de la plateforme afin de faciliter la compréhension du produit.

À certains égards, le produit est unique, car il est décrit et fourni via un gestionnaire de package (NuGet) sous forme de packages. .NET Core s’obtient généralement sous la forme d’un SDK autonome. Cependant, ce SDK n’est pas différent des packages NuGet, il est simplement plus pratique. La gestion de version s’applique donc principalement aux packages, et les autres gestions de version découlent de celle-ci.

## <a name="semantic-versioning"></a>Gestion sémantique de version

.NET Core utilise la [gestion sémantique de version (SemVer)](http://semver.org/), adoptant ainsi l’utilisation de la gestion de version major.minor.patch, qui utilise différentes parties du numéro de version pour décrire le degré et le type de modification.

Le modèle de gestion de version suivant est généralement appliqué à .NET Core. Il existe des cas où ce modèle a été adapté à une gestion de version existante. Ces cas sont décrits plus loin dans ce document. Par exemple, les frameworks sont uniquement conçus pour représenter les fonctionnalités de la plateforme et des API, ce qui s’aligne sur le principe de version principale/secondaire.

### <a name="versioning-form"></a>Format de la gestion de version

MAJOR.MINOR.PATCH[-PRERELEASE-BUILDNUMBER]

### <a name="decision-tree"></a>Arbre de décision

Une version principale est nécessaire quand vous devez :
  - Arrêter la prise en charge d’une plateforme
  - Adopter une version principale plus récente d’une dépendance existante 
  - Désactiver le mode compatibilité par défaut

Une version secondaire est nécessaire quand vous devez :
  - Ajouter une surface d’API publique 
  - Ajouter un nouveau comportement
  - Adopter une version secondaire plus récente d’une dépendance existante
  - Ajouter une nouvelle dépendance 
  
Un correctif est nécessaire quand vous devez :
  - Corriger des bogues
  - Ajouter la prise en charge d’une plateforme plus récente
  - Adopter une version corrective plus récente d’une dépendance existante
  - Toute autre modification

Pour déterminer les éléments à incrémenter lorsqu’il existe plusieurs modifications, choisissez le type de modification le plus important.

## <a name="versioning-scheme"></a>Schéma de la gestion de version

.NET Core peut être défini et se voir attribuer une version de la manière suivante :

- Une implémentation du runtime et du framework, distribuée sous forme de packages. La version de chaque package est attribuée indépendamment, en particulier pour les versions correctives.
- Un ensemble de métapackages qui référence des packages de granularité fine comme un ensemble avec version. Les versions des métapackages sont gérées séparément de celles des packages.
- Un ensemble de frameworks (par exemple, `netstandard`) qui représente un ensemble API qui s’agrandit progressivement, décrit dans un ensemble d’instantanés avec version.

### <a name="packages"></a>Packages

L’évolution et l’attribution des versions des packages de bibliothèque sont réalisées indépendamment. Les packages qui se chevauchent avec le système .NET Framework.\* utilisent généralement les versions 4.x, s’alignant ainsi sur la gestion de version .NET Framework 4.x (choix historique). Les packages qui n’entraînent pas de chevauchement avec les bibliothèques .NET Framework (par exemple, [System.Reflection.Metadata](https://www.nuget.org/packages/System.Reflection.Metadata)) commencent généralement à 1.0 et s’incrémentent par la suite.

Les packages décrits par [NETStandard.Library](https://www.nuget.org/packages/NETStandard.Library) reçoivent un traitement spécial, car ils sont à la base de la plateforme.

- Les packages NETStandard.Library reçoivent généralement leur version comme un ensemble, car ils possèdent des dépendances au niveau de l’implémentation.
- Les API sont uniquement ajoutées aux packages NETStandard.Library dans le cadre d’une version principale ou secondaire de .NET Core, puisque cela implique l’ajout d’une nouvelle version `netstandard`. Cela vient s’ajouter aux conditions requises par SemVer.

### <a name="metapackages"></a>Métapackages

Pour les métapackages .NET Core, la gestion de version repose sur le framework auquel ils sont associés. Les métapackages adoptent le numéro de version le plus élevé du framework (par exemple, netstandard1.6) auquel ils sont mappés dans sa fermeture de package. 

La version corrective du métapackage est utilisée pour représenter des mises à jour du métapackage qui référencent des packages mis à jour. Les versions correctives n’incluent jamais de version de framework mise à jour. Par conséquent, les métapackages ne sont pas strictement conformes aux règles de gestion sémantique de version (SemVer), car leur schéma de version ne représente pas le degré de modification des packages sous-jacents, mais principalement le niveau de l’API. 

Il existe deux métapackages principaux pour .NET Core.

**NETStandard.Library**

- V1.6 à compter de .NET Core 1.0 (ces versions ne correspondent généralement pas).
- Est mappé au framework `netstandard`. 
- Décrit les packages qui sont considérés comme nécessaires au développement d’applications modernes et que les plateformes .NET doivent implémenter pour être considérées comme des plateformes [.NET Standard](../../standard/library.md).

**Microsoft.NETCore.App**

- V1.0 à compter de .NET Core 1.0 (ces versions correspondent).
- Est mappé au framework `netcoreapp`.
- Décrit les packages de la distribution .NET Core.

Remarque : [`Microsoft.NETCore.Portable.Compatibility`](https://www.nuget.org/packages/Microsoft.NETCore.Portable.Compatibility) est un autre métapackage .NET Core. Il n’est pas mappé à un framework particulier et reçoit donc une version comme un package.

### <a name="frameworks"></a>Frameworks

Les versions du framework sont mises à jour lorsque de nouvelles API sont ajoutées. Elles ne comprennent pas le concept de version corrective, car elles représentent la forme de l’API et non son implémentation. La gestion des versions principales et secondaires suivent les règles de gestion sémantique de version (SemVer) spécifiées précédemment.

Le framework `netcoreapp` est lié à la distribution .NET Core. Il suit les numéros de version utilisés par .NET Core. Par exemple, lorsque .NET Core 2.0 sera publié, il ciblera `netcoreapp2.0`. Le framework `netstandard` ne correspondra au schéma de version d’aucun runtime .NET, étant donné qu’il s’applique à tous les éléments.

## <a name="versioning-in-practice"></a>La gestion de version dans la pratique

Tous les jours, de nouvelles validations et demandes Pull sont ajoutées aux dépôts .NET Core sur GitHub, ce qui permet d’obtenir de nouvelles versions de nombreuses bibliothèques. Il ne serait pas pratique de créer une nouvelle version publique de .NET Core à chaque modification. Les modifications sont donc agrégées pendant une période définie (par exemple, des semaines ou des mois) avant de créer une nouvelle version publique stable de .NET Core.

Une nouvelle version de .NET Core peut signifier plusieurs choses :

- De nouvelles versions des packages et des métapackages.
- De nouvelles versions de différents frameworks, supposant l’ajout de nouvelles API.
- Une nouvelle version de la distribution .NET Core.

### <a name="shipping-a-patch-release"></a>Publication d’une version corrective

Une fois la version stable de .NET Core v1.0.0 publiée, les modifications au niveau du correctif (pas de nouvelles API) sont apportées aux bibliothèques .NET Core pour corriger les bogues et améliorer les performances et la fiabilité. Les différents métapackages sont mis à jour pour référencer les packages de bibliothèque .NET Core mis à jour. Les métapackages reçoivent une version dans le cadre d’un correctif (x.y.z). Les frameworks ne sont pas mis à jour. Une nouvelle distribution .NET Core est fournie avec un numéro de version correspondant au métapackage `Microsoft.NETCore.App`.

Vous pouvez voir ces mises à jour correctives dans les exemples project.json ci-dessous.

```
{
  "dependencies": {
    "Microsoft.NETCore.App": "1.0.1"
  },
  "frameworks": {
    "netcoreapp1.0": {}
  }
}
```

### <a name="shipping-a-minor-release"></a>Publication d’une version secondaire

Une fois la version stable de .NET Core v1.0.0 publiée, de nouvelles API sont ajoutées aux bibliothèques .NET Core pour permettre de nouveaux scénarios. Les différents métapackages sont mis à jour pour référencer les packages de bibliothèque .NET Core mis à jour. Les métapackages reçoivent une version dans le cadre d’un correctif (x.y) qui correspond à la version de framework la plus élevée. Les différents frameworks sont mis à jour pour décrire les nouvelles API. Une nouvelle distribution .NET Core est fournie avec un numéro de version correspondant au métapackage `Microsoft.NETCore.App`.

Vous pouvez voir les mises à jour secondaires illustrées dans le fichier projet suivant :

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netcoreapp1.1</TargetFramework>
  </PropertyGroup>
</Project>
```

### <a name="shipping-a-major-release"></a>Publication d’une version principale

Avec une version stable de .NET Core v1.y.z, de nouvelles API sont ajoutées aux bibliothèques .NET Core pour permettre de nouveaux scénarios de mises à jour principales. Par exemple, pour la suppression de la prise en charge d’une plateforme. Les différents métapackages sont mis à jour pour référencer les packages de bibliothèque .NET Core mis à jour. Le métapackage `Microsoft.NETCore.App` et le framework `netcore` reçoivent une version dans le cadre d’une version principale (x.). Le métapackage `NETStandard.Library` reçoit probablement une version dans le cadre d’une version secondaire (x.y), étant donné qu’il s’applique à plusieurs implémentations de .NET. Une nouvelle distribution .NET Core serait alors fournie avec un numéro de version correspondant au métapackage `Microsoft.NETCore.App`.

Vous pouvez voir les mises à jour principales illustrées dans le fichier projet suivant. (Notez que `netcoreapp2.0` n’a pas été publié.)

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netcoreapp2.0</TargetFramework>
  </PropertyGroup>
</Project>

```

