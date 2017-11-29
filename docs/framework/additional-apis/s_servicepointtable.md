---
title: Champ de ServicePointManager.s_ServicePointTable
ms.date: 05/01/2017
ms.prod: .net-framework
ms.technology: 
ms.topic: reference
topic_type: apiref
api_name: System.Net.ServicePointManager.s_ServicePointTable
api_location: System.dll
api_type: Assembly
ms.assetid: 24459679-291c-401a-9def-e42b29466fcf
author: guardrex
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 2f12a8ba4d2b84e5b5d73d26199adf687a95a2df
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="servicepointmanagersservicepointtable-field"></a>ServicePointManager.s\_ServicePointTable champ

`ServicePointManager.s_ServicePointTable`est un <xref:System.Collections.Hashtable> qui contient la liste des connexions HTTP actives (<xref:System.Net.ServicePoint>s) dans le <xref:System.AppDomain>.

## <a name="syntax"></a>Syntaxe
  
```csharp  
private static Hashtable s_ServicePointTable
```

> [!WARNING]
> Le `ServicePointManager.s_ServicePointTable` champ est privée et ne revient pas à être utilisée directement dans votre code.
> 
> Microsoft ne prend pas en charge l’utilisation de ce champ dans une application de production en toutes circonstances.

## <a name="requirements"></a>Spécifications

**Namespace :**<xref:System.Net>

**Assembly :** système (dans System.dll)

**Versions du .NET framework :** disponible depuis la version 2.0.
