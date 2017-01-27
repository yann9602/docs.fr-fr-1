---
title: "Informations de référence sur global.json │ .NET Core"
description: "Informations de référence sur global.json"
keywords: .NET, .NET Core
author: blackdwarf
ms.author: mairaw
ms.date: 11/02/2016
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: e1ac9659-425f-4486-a376-c12ca942ead8
translationtype: Human Translation
ms.sourcegitcommit: 1a84c694945fe0c77468eb77274ab46618bccae6
ms.openlocfilehash: 281f1b717a0e220e533078e973711977617a1401

---

# <a name="globaljson-reference"></a>Informations de référence sur global.json

Le fichier global.json est encore présent dans la ligne de commande .NET Core Preview 3. Toutefois, son objectif principal n’est pas de définir les métadonnées de la solution comme dans les versions Release précédentes, mais de permettre la sélection de la version CLI utilisée par le biais de la propriété `sdk`. 

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



<!--HONumber=Nov16_HO3-->


