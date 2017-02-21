---
title: "Informations de référence sur global.json | Microsoft Docs"
description: "Informations de référence sur global.json"
keywords: .NET, .NET Core
author: blackdwarf
ms.author: mairaw
ms.date: 11/02/2016
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 96102f96-d403-4385-8ef6-5d80e406eb0c
translationtype: Human Translation
ms.sourcegitcommit: 796df1549a7553aa93158598d62338c02d4df73e
ms.openlocfilehash: b814bfc79c2fcd0fd15b9494c18c6d0443a70fb1

---

# <a name="globaljson-reference-net-core-tools-rc4"></a>Informations de référence sur global.json (outils .NET Core RC4)

> [!WARNING]
> Cette rubrique s’applique aux outils .NET Core RC4. Pour la version Preview 2 des outils .NET Core, consultez la rubrique [Informations de référence sur global.json](../../tools/global-json.md).

Le fichier global.json est encore présent dans la ligne de commande .NET Core RC4. Toutefois, son objectif principal n’est pas de définir les métadonnées de la solution comme dans les versions Release précédentes, mais de permettre la sélection de la version CLI utilisée par le biais de la propriété `sdk`. 

Cette référence reflète le fait ci-dessus. 

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


