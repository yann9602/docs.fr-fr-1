---
title: "Informations de référence sur global.json | Microsoft Docs"
description: "Informations de référence sur global.json"
keywords: .NET, .NET Core
author: blackdwarf
ms.author: mairaw
ms.date: 03/06/2016
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 96102f96-d403-4385-8ef6-5d80e406eb0c
translationtype: Human Translation
ms.sourcegitcommit: 3845ec46cbd1f65abd9b78f7b81487efed9de2f2
ms.openlocfilehash: 253b8642ae6fc5308d47552e9addfdbed6813ff1
ms.lasthandoff: 03/13/2017

---

# <a name="globaljson-reference"></a>Informations de référence sur global.json

Le fichier global.json permet de sélectionner la version des outils .NET Core utilisée par le biais de la propriété `sdk`. 

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
