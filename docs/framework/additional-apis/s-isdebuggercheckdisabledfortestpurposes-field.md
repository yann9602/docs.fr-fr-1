---
title: s_isDebuggerCheckDisabledForTestPurposes champ
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
api_name: System.Windows.Diagnostics.VisualDiagnostics.s_isDebuggerCheckDisabledForTestPurposes
api_location: PresentationCore.dll
api_type: Assembly
ms.assetid: 9033a513-c255-4f31-b6d7-09b8d8c50e2d
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
robots: noindex,nofollow
ms.openlocfilehash: 97e5d32bff3e3150b56e8d9492aacc40f09f2afe
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="sisdebuggercheckdisabledfortestpurposes-field"></a>s_isDebuggerCheckDisabledForTestPurposes champ

Ce champ privé dans la `System.Windows.Diagnostics.VisualDiagnostics` classe est utilisée par Visual Studio pour déterminer si une vérification interne pour le débogueur actif sera effectuée.

## <a name="syntax"></a>Syntaxe
  
```csharp  
private static bool s_isDebuggerCheckDisabledForTestPurposes
```
  
> [!WARNING]
>  L’API dans la `System.Windows.Diagnostics.VisualDiagnostics` classe sont disponibles uniquement quand une application s’exécute sous un débogueur. Définissez `s_isDebuggerCheckDisabledForTestPurposes` à `true` pour accéder aux API en dehors d’un débogueur.  
>   
>  Microsoft ne prend pas en charge l’utilisation de ce champ dans une application de production en toutes circonstances.  

## <a name="requirements"></a>Spécifications

**Namespace :**<xref:System.Windows.Diagnostics>

**Assembly :** PresentationCore (dans PresentationCore.dll)

**Versions du .NET framework :** disponible depuis 4.6.
