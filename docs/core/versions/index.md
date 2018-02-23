---
title: Gestion des versions de .NET Core
description: "Découvrez comment fonctionne la gestion des versions de .NET Core."
author: bleroy
ms.author: mairaw
ms.date: 02/13/2018
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: f6f684b1-1d2c-4105-8376-7c1959e23803
ms.workload:
- dotnetcore
ms.openlocfilehash: 70c7f179f3451e51d5ab383cde80959a69f959a1
ms.sourcegitcommit: 96cc82cac4650adfb65ba351506d8a8fbcd17b5c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2018
---
# <a name="net-core-versioning"></a>Gestion des versions de .NET Core

.NET Core est constitué de [packages NuGet](../packages.md), d’outils et de frameworks qui sont distribués comme un tout. Les versions de chacune de ces couches de plateforme peuvent être gérées séparément, ce qui permet une meilleure agilité. Même si la gestion des versions est très flexible de ce point de vue, il est souhaitable d’attribuer une version à l’ensemble de la plateforme afin de rendre le produit plus facile à comprendre.

Cet article vise à clarifier la façon dont les versions du SDK .NET Core et du runtime sont gérées.

Il existe un grand nombre de composants changeants dont les versions sont gérées indépendamment dans .NET Core. Cependant, à compter de .NET Core 2.0, il existe un numéro de version de plus haut niveau facile à comprendre, dont tout le monde comprend qu’il s’agit de *la* version de « .NET Core » considéré comme un tout. Le reste de ce document donne des informations détaillées sur la gestion des versions de tous ces composants. Ces informations peuvent être importantes, par exemple si vous êtes gestionnaire de packages.

> [!IMPORTANT]
> Les détails du contrôle de version indiqués dans cette rubrique ne s’appliquent pas à la version actuelle du Kit de développement logiciel (SDK) .NET Core et au runtime.
> Le schéma de version change dans les versions futures. Vous pouvez consulter la proposition actuelle dans le référentiel [dotnet/conceptions](https://github.com/dotnet/designs/pull/29).

## <a name="versioning-details"></a>Informations détaillées sur la gestion des versions

Avec .NET Core 2.0, les téléchargements comportent un numéro de version unique dans leur nom de fichier. Les numéros de version suivants ont été unifiés :

* Le framework partagé et le runtime associé.
* Le SDK .NET Core et l’interface CLI .NET Core associée.
* Le métapackage `Microsoft.NETCore.App`.

L’utilisation d’un seul numéro de version permet aux utilisateurs de savoir plus facilement quelle version du SDK installer sur leurs machines de développement et quelle doit être la version correspondante du framework partagé quand il faut approvisionner un environnement de production. Quand vous téléchargez un SDK ou un runtime, le numéro de version que vous voyez sera donc le même.

### <a name="installers"></a>Programmes d’installation

Avec .NET Core 2.0, les téléchargements correspondants aux [builds quotidiens](https://github.com/dotnet/core-setup#daily-builds) et aux [ versions](https://www.microsoft.com/net/download/core) respectent un nouveau schéma d’affectation de nom qui est plus facile à comprendre.
L’interface utilisateur du programme d’installation dans ces téléchargements a également été modifiée de façon à présenter clairement les noms et les versions des composants à installer. En particulier, les titres montrent désormais le même numéro de version que celui qui se trouve dans le nom de fichier du téléchargement.

#### <a name="file-name-format"></a>Format du nom de fichier

`[product]-[component]-[major].[minor].[patch]-[previewN]-[optional build #]-[rid].[file ext]`

Voici quelques exemples de ce format :

```
dotnet-runtime-2.0.4-macos.10.12-x64.pkg            # Mac runtime installer
dotnet-sdk-2.0.4-win10-x64.exe                      # Windows SDK installer
dotnet-sdk-2.0.4-fedora.24-x64.tar.gz               # Fedora 24 binary archive

#Ubuntu file set needed for the SDK
dotnet-host-2.0.4-ubuntu.16.04-x64.deb              # Host / muxer and host policy
dotnet-runtime-2.0.4-ubuntu.16.04-x64.deb           # runtime
dotnet-sdk-2.0.4-ubuntu.16.04-x64.deb               # SDK tools
```

Le format est lisible et montre clairement ce que vous téléchargez, de quelle version il s’agit et où vous pouvez l’utiliser. Le nom du package du runtime inclut `runtime`, tandis que le SDK inclut `SDK`.

#### <a name="ui-string-format"></a>Format des chaînes de l’interface utilisateur

Toutes les descriptions et les chaînes d’interface utilisateur du site web dans les programmes d’installation sont conservées cohérentes, simples et précises. Le tableau suivant montre quelques exemples :

| Programme d’installation | Titre de la fenêtre                          | Autre contenu dans le programme d’installation | Ce qui est installé                               |
| :--       | :--                                   | :--                        | :--                                             |
| SDK       | Programme d’installation du SDK .NET Core 2.0 (x64)     | SDK .NET Core 2.0.4        | Outils .NET Core 2.0.4 + Runtime .NET Core 2.0.4 |
| Runtime   | Runtime .NET Core 2.0 (x64) | Runtime .NET Core 2.0.4    | Runtime .NET Core 2.0.4                         |

Les préversions diffèrent seulement légèrement :

| Programme d’installation | Titre de la fenêtre                                    | Autre contenu dans le programme d’installation        | Ce qui est installé                                                   |
| :--       | :--                                             | :--                               | :--                                                                 |
| SDK       | Programme d’installation du SDK .NET Core 2.0 Preview 1 (x 64)     | SDK .NET Core 2.0.0 Preview 1     | Outils .NET Core 2.0.0 Preview 1 + .Runtime NET Core 2.0.0 Preview 1 |
| Runtime   | Programme d’installation du Runtime .NET Core 2.0 Preview 1 (x 64) | Runtime .NET Core 2.0.0 Preview 1 | Runtime .NET Core 2.0.0 Preview 1                                   |

Il peut arriver qu’une version du SDK contienne plusieurs versions du runtime. Quand cela se produit, l’expérience utilisateur du programme d’installation ressemble à ceci (seule la version du SDK est indiquée, et les versions installées du Runtime apparaissent sur une page récapitulative à la fin du processus d’installation sur Windows et sur Mac) :

| Programme d’installation | Titre de la fenêtre                      | Autre contenu dans le programme d’installation                                   | Ce qui est installé                                                         |
| :--       | :--                               | :--                                                          | :--                                                                       |
| SDK       | Programme d’installation du SDK .NET Core 2.1 (x64) | SDK .NET Core 2.1.1 <br> Runtime .NET Core 2.1.1 <br> Runtime .NET Core 2.0.6 | Outils .NET Core 2.1.1 + Runtime .NET Core 2.1.1 + Runtime .NET Core 2.0.6 |

Il est également possible que les outils .NET Core doivent être mis à jour, sans modifications du runtime. Dans ce cas, la version du SDK est augmentée (par exemple à 2.1.2) puis le runtime la rattrape lors de sa livraison suivante (par exemple, le runtime et le SDK sont livrés la prochaine fois sous le numéro 2.1.3).

### <a name="package-managers"></a>Gestionnaires de packages

.NET Core peut être distribué par d’autres entités que Microsoft. En particulier, les propriétaires d’une distribution Linux et les gestionnaires de packages peuvent ajouter des packages .NET Core à leurs gestionnaires de packages. Pour obtenir des recommandations sur la façon dont ces packages doivent être nommés et leurs versions gérées, consultez [Empaquetage de la distribution de .NET Core](../build/distribution-packaging.md).

#### <a name="minimum-package-set"></a>Ensemble minimal du package

* `dotnet-runtime-[major].[minor]` : un runtime avec la version spécifiée (seule la dernière version corrective pour une combinaison majeure + mineure doit être disponible dans le gestionnaire de packages). Les nouvelles versions correctives mettent à jour le package, mais les nouvelles versions mineures ou majeures sont des packages distincts.

  **Dépendances** : `dotnet-host`

* `dotnet-sdk` : dernière version du kit SDK. `update` restaure par progression les versions majeures, mineures et correctives.

  **Dépendances** : dernière version de `dotnet-sdk-[major].[minor]`.

* `dotnet-sdk-[major].[minor]` : Kit SDK avec la version spécifiée. La version spécifiée est la version la plus élevée incluse des frameworks partagés inclus, afin que les utilisateurs puissent facilement associer un kit SDK à un framework partagé. Les nouvelles versions correctives mettent à jour le package, mais les nouvelles versions mineures ou majeures sont des packages distincts.

  **Dépendances** : `dotnet-host`, une ou plusieurs versions `dotnet-runtime-[major].[minor]` (une de ces versions est utilisée par le code du SDK proprement dit, les autres servent aux utilisateurs pour la génération et l’exécution).

* `dotnet-host` : dernière version de l’hôte.

##### <a name="preview-versions"></a>Préversions

Ceux qui gèrent les packages peuvent décider d’inclure des préversions du runtime et du SDK. N’incluez pas ces préversions dans le package `dotnet-sdk` sans version. Vous pouvez cependant les publier en tant que packages versionnés avec un marqueur de préversion supplémentaire ajouté aux sections du nom correspondant à la version majeure et à la version mineure. Par exemple, il peut y avoir un package `dotnet-sdk-2.0-preview1-final`.

### <a name="docker"></a>Docker

Une convention générale de nommage des étiquettes Docker est de placer le numéro de version avant le nom du composant. Vous pouvez continuer à utiliser cette convention. Les étiquettes actuelles incluent seulement la version du runtime comme suit.

* 1.0.8-runtime
* 1.0.8-sdk
* 2.0.4-runtime
* 2.0.4-sdk
* 2.1.1-runtime
* 2.1.1-sdk

Les étiquettes du SDK doivent être mises à jour de façon à représenter la version du SDK au lieu de celle du runtime.

Il est également possible que les outils du CLI .NET Core (compris dans le Kit de développement logiciel) soient fixes mais réexpédiés avec un runtime existant. Dans ce cas, la version du Kit de développement logiciel (SDK) est augmentée (par exemple à 2.1.2) puis le runtime la rattrape lors de sa prochaine livraison (par exemple, le runtime et le Kit de développement logiciel (SDK) sont livrés la fois suivante sous le numéro 2.1.3).

## <a name="semantic-versioning"></a>Gestion sémantique des versions

.NET Core utilise la [gestion sémantique des versions (SemVer)](http://semver.org/), adoptant ainsi l’utilisation de la gestion de versions `MAJOR.MINOR.PATCH`, qui utilise différentes parties du numéro de version pour décrire le degré et le type de modification.

```
MAJOR.MINOR.PATCH[-PRERELEASE-BUILDNUMBER]
```

Les pièces facultatives `PRERELEASE` et `BUILDNUMBER` ne feront jamais partie des versions prises en charge, elles existent seulement sur les builds générés pendant la nuit, builds locaux générés à partir des cibles de la source et préversions non prises en charge.

### <a name="how-version-numbers-are-incremented"></a>Comment les numéros de version sont-ils incrémentés ?

`MAJOR` est incrémenté quand :

- Une version ancienne n’est plus prise en charge.
- Une version `MAJOR` plus récente d’une dépendance existante est adoptée.
- La valeur par défaut d’une anomalie de compatibilité est changée en « off ».

`MINOR` est incrémenté quand :

- Une surface d’exposition d’API publique est ajoutée.
- Un nouveau comportement est ajouté.
- Une version `MINOR` plus récente d’une dépendance existante est adoptée.
- Une nouvelle dépendance est introduite.

`PATCH` est incrémenté quand :

- Des correctifs de bogues sont effectués.
- La prise en charge d’une plateforme plus récente est ajoutée.
- Une version `PATCH` plus récente d’une dépendance existante est adoptée.
- Toute autre modification ne relevant pas d’un des cas précédents.

Quand il existe plusieurs modifications, l’élément le plus élevé affecté par des modifications individuelles est incrémenté et les suivants sont remis à zéro. Par exemple, quand `MAJOR` est incrémenté, `MINOR` et `PATCH` sont remis à zéro. Quand `MINOR` est incrémenté, `PATCH` est remis à zéro, tandis que `MAJOR` est laissé tel quel.

### <a name="preview-versions"></a>Préversions

Pour les préversions, un `-preview[number]-([build]|"final")` est ajouté à la version. Par exemple, `2.0.0-preview1-final`.

### <a name="servicing-versions"></a>Versions de maintenance

Une fois qu’une version est publiée, les branches de la version arrêtent généralement de produire des builds quotidiens pour commencer à produire des builds de maintenance. Pour les versions de maintenance, un `-servicing-[number]` est ajouté à la version. Par exemple, `2.0.1-servicing-006924`.

### <a name="lts-vs-current"></a>Versions LTS et Current

Il existe deux trains de versions pour .NET Core : LTS (Long Term Support) et Current. Ceci permet aux utilisateurs de choisir le niveau de stabilité et les nouvelles fonctionnalités souhaitées, avec des versions néanmoins toujours prises en charge.

- LTS signifie que vous obtenez des nouvelles fonctionnalités moins fréquemment, mais que vous avez une plateforme plus mature. LTS a aussi une période de prise en charge plus longue.
- Current signifie que vous obtenez des nouvelles fonctionnalités et des API plus fréquemment, mais l’inconvénient est que vous avez un laps de temps plus court pour installer les mises à jour, et que ces mises à jour se produisent plus fréquemment. Les versions Current sont également entièrement prises en charge, mais la période de prise en charge est plus courte que pour LTS.

Une version Current peut devenir une version LTS.

« LTS » et « Current » doivent être considérés comme des libellés que nous plaçons sur des versions spécifiques pour donner une indication sur le niveau de prise en charge associé.

Pour plus d’informations, consultez [.NET Core Support Lifecycle Fact Sheet](https://www.microsoft.com/net/core/support).

## <a name="versioning-scheme-details"></a>Détails du modèle de gestion de versions

.NET Core est constitué des composants suivants :

- Un ordinateur hôte : soit *dotnet.exe* pour les applications dépendantes du framework ou  *\<appname > .exe* pour les applications autonomes.
- Un SDK (l’ensemble des outils nécessaires sur la machine d’un développeur, mais pas en production).
- Un runtime.
- Une implémentation du framework partagé, distribuée sous forme de packages. La version de chaque package est attribuée indépendamment, en particulier pour les versions correctives.
- Facultativement, un ensemble de [métapackages](../packages.md) qui référencent des packages précis sous la forme d’une unité avec versions. Les versions des métapackages peuvent être gérées séparément de celles des packages.

.NET Core inclut également un ensemble de frameworks cibles (par exemple `netstandard` ou `netcoreapp`) qui représentent un ensemble progressivement plus important d’API, au fil de l’incrémentation des numéros de version.

### <a name="net-standard"></a>.NET Standard

.NET Standard a utilisé un modèle de gestion de versions `MAJOR.MINOR`. Le niveau `PATCH` n’est pas utile pour .NET Standard, car il représente un ensemble de contrats qui sont itérés moins souvent, mais ne présente pas les mêmes spécifications pour la gestion des versions comme implémentation réelle.

Il n’existe aucun couplage réel entre les versions de .NET Standard et de .NET Core : il se trouve que .NET Core 2.0 implémente .NET Standard 2.0, mais il n’existe aucune garantie que les versions ultérieures de .NET Core correspondront à la même version de .NET Standard. .NET Core peut contenir des API qui ne sont pas définies par .NET Standard : il peut donc fournir de nouvelles versions sans nécessiter un nouveau .NET Standard. .NET Standard est aussi un concept qui s’applique à d’autres cibles, comme .NET Framework ou Mono, même si son lancement a coïncidé avec celui de .NET Core.

### <a name="packages"></a>Packages

L’évolution et l’attribution des versions des packages de bibliothèque sont réalisées indépendamment. Les packages qui se chevauchent avec les assemblys System.\* .NET Framework utilisent généralement les versions 4.x, s’alignant ainsi sur la gestion de versions de .NET Framework 4.x (choix historique). Les packages qui n’entraînent pas de chevauchement avec les bibliothèques du .NET Framework (par exemple [`System.Reflection.Metadata`](https://www.nuget.org/packages/System.Reflection.Metadata)) commencent généralement à 1.0 et s’incrémentent à partir de là.

Les packages décrits par [`NETStandard.Library`](https://www.nuget.org/packages/NETStandard.Library) sont traités de façon spéciale, car ils sont à la base de la plateforme.

Les versions des packages `NETStandard.Library` sont généralement traitées comme un ensemble, car ces packages ont des dépendances entre eux au niveau de l’implémentation.

### <a name="metapackages"></a>Métapackages

Pour les métapackages .NET Core, la gestion de versions repose sur la version de .NET Core dont ils font partie.

Par exemple, les métapackages dans .NET Core 2.1.3 doivent tous avoir 2.1 comme numéros de version `MAJOR` et `MINOR`.

La version du correctif pour le métapackage est incrémentée chaque fois qu’un package référencé est mis à jour. Les versions des correctifs n’incluent jamais de version de framework mise à jour. Par conséquent, les métapackages ne sont pas strictement conformes aux règles de gestion sémantique de version (SemVer), car leur schéma de contrôle de version ne représente pas le degré de modification des packages sous-jacents, mais bien principalement le niveau de l’API.

Il existe actuellement deux métapackages principaux pour .NET Core :

**Microsoft.NETCore.App**

- V1.0 pour .NET Core 1.0 (ces versions correspondent).
- Est mappé au framework `netcoreapp`.
- Décrit les packages de la distribution .NET Core.

Remarque : [`Microsoft.NETCore.Portable.Compatibility`](https://www.nuget.org/packages/Microsoft.NETCore.Portable.Compatibility) est un autre métapackage .NET Core qui existe pour permettre la compatibilité avec l’implémentation de .NET antérieure à .NET Standard. Elle ne correspond pas à un framework particulier et ses versions sont donc gérées comme celles d’un package.

**NETStandard.Library**

[`NETStandard.Library`](https://www.nuget.org/packages/NETStandard.Library) décrit les bibliothèques qui font partie du [.NET Standard](../../standard/library.md). S’applique à toutes les implémentations de .NET qui prennent en charge .NET Standard (par exemple .NET Framework, .NET Core et Mono).

### <a name="target-frameworks"></a>Versions cibles de .NET Framework

Les versions du framework cible sont mises à jour quand de nouvelles API sont ajoutées. Elles ne comprennent pas le concept de version corrective, car elles représentent la forme de l’API et non son implémentation. La gestion des versions majeure et mineure suit les règles de la gestion sémantique de version spécifiées précédemment, et elle coïncide avec les numéros `MAJOR` et `MINOR` des distributions de .NET Core qui les implémentent.

## <a name="versioning-in-practice"></a>La gestion de versions dans la pratique

Quand vous téléchargez .NET Core, le nom du fichier téléchargé comporte la version, par exemple `dotnet-sdk-2.0.4-win10-x64.exe`.

Il y a tous les jours de nouvelles validations et de nouvelles demandes d’extraction sur les dépôts .NET Core sur GitHub, ce qui aboutit à de nouveaux builds de nombreuses bibliothèques. Il ne serait pas pratique de créer une nouvelle version publique de .NET Core à chaque modification. Au lieu de cela, les modifications sont agrégées pendant une période de temps non déterminée (par exemple des semaines ou des mois) avant de créer une nouvelle version publique stable de .NET Core.

Une nouvelle version de .NET Core peut signifier plusieurs choses :

- De nouvelles versions des packages et des métapackages.
- De nouvelles versions de différents frameworks, supposant l’ajout de nouvelles API.
- Une nouvelle version de la distribution .NET Core.

### <a name="shipping-a-patch-release"></a>Publication d’une version corrective

Après la publication d’une version majeure de .NET Core, comme la version 2.0.0, les modifications de niveau correctif sont effectuées dans les bibliothèques .NET Core pour corriger les bogues, et améliorer les performances et la fiabilité. Cela signifie qu’aucune nouvelle API n’est introduite. Les différents métapackages sont mis à jour pour référencer les packages de bibliothèque .NET Core mis à jour. Les versions des métapackages sont gérées en tant que mises à jour de correctif `MAJOR.MINOR.PATCH`. Les frameworks cibles ne sont jamais mis à jour dans le cadre des publications de correctifs. Une nouvelle distribution de .NET Core est publiée avec un numéro de version correspondant à celui du métapackage `Microsoft.NETCore.App`.

### <a name="shipping-a-minor-release"></a>Publication d’une version secondaire

Après la publication d’une version .NET Core avec un numéro de version `MAJOR` incrémenté, les nouvelles API sont ajoutées aux bibliothèques .NET Core pour permettre de nouveaux scénarios. Les différents métapackages sont mis à jour pour référencer les packages de bibliothèque .NET Core mis à jour. Les versions des métapackages sont gérées en tant que mises à jour de correctif avec des numéros de version `MAJOR` et `MINOR` correspondant à la nouvelle version du framework. Les noms des nouveaux frameworks cibles avec la nouvelle version `MAJOR.MINOR` sont ajoutés pour décrire les nouvelles API (par exemple `netcoreapp2.1`). Une nouvelle distribution .NET Core est fournie avec un numéro de version correspondant au métapackage `Microsoft.NETCore.App`.

### <a name="shipping-a-major-release"></a>Publication d’une version principale

Chaque fois qu’une nouvelle version majeure du .NET Core est publiée, le numéro de version `MAJOR` est incrémenté et le numéro de version `MINOR` est remis à zéro. La nouvelle version majeure contient au moins toutes les API qui ont été ajoutées par les versions mineures après la version majeure précédente. Une nouvelle version majeure doit normalement permettre de nouveaux scénarios importants, et elle peut aussi supprimer la prise en charge d’une plateforme plus ancienne.

Les différents métapackages sont mis à jour pour référencer les packages de bibliothèque .NET Core mis à jour. Les versions du métapackage [ `Microsoft.NETCore.App`](https://www.nuget.org/packages/Microsoft.NETCore.App) et du framework cible `netcore` sont gérées comme mise à jour majeure correspondant au numéro de version `MAJOR` de la nouvelle publication.

## <a name="see-also"></a>Voir aussi

[Frameworks cibles](../../standard/frameworks.md)  
[Empaquetage de la distribution de .NET Core](../build/distribution-packaging.md)  
[Fiche d’information sur le cycle de vie de support .NET Core](https://www.microsoft.com/net/core/support)  
[.NET Core 2+ Version Binding](https://github.com/dotnet/designs/issues/3)  
