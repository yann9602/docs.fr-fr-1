---
title: "Informations de référence sur global.json | Microsoft Docs"
description: "Informations de référence sur global.json"
keywords: .NET, .NET Core
author: aL3891
ms.author: mairaw
ms.date: 11/02/2016
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: e1ac9659-425f-4486-a376-c12ca942ead8
translationtype: Human Translation
ms.sourcegitcommit: 796df1549a7553aa93158598d62338c02d4df73e
ms.openlocfilehash: a6b0ad546a8a121ad5ea4642c11842a8dccf7055

---

# <a name="globaljson-reference"></a>Informations de référence sur global.json

> [!WARNING]
> Cette rubrique s'applique aux outils .NET Core Preview 2. Pour la version RC4 des outils .NET Core, consultez la rubrique [Informations de référence sur global.json (outils .NET Core RC4)](../preview3/tools/global-json.md).

Le fichier global.json est utilisé sur les projets .NET Core pour définir les métadonnées de la solution. Ce fichier est utilisé quand la commande [dotnet-restore](dotnet-restore.md) est appelée pour restaurer les dépendances d’un projet .NET Core.
Cette rubrique de référence répertorie les propriétés que vous pouvez définir dans votre fichier global.json.

## <a name="projects"></a>projets
Type : String[]

Spécifie les dossiers dans lesquels le système de génération doit rechercher les projets pendant la résolution des dépendances. Le système de génération parcourt uniquement les dossiers enfants de niveau supérieur.

Par exemple :

```json
{
    "projects": [ "src", "test" ]
}
```

## <a name="packages"></a>packages
Type : chaîne

Emplacement de stockage des packages.

Par exemple :
```json
{
    "packages": "packages-dir"
}
```

## <a name="sdk"></a>sdk
Type : object

Spécifie des informations sur le SDK.

### <a name="version"></a>version
Type : chaîne

Version du SDK à utiliser.

Par exemple :

```json
{
    "sdk": {
        "version": "1.0.0-preview2-003121"
    }
}
```



<!--HONumber=Feb17_HO2-->


