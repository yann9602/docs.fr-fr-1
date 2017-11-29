---
title: 452 - MessageLogWarning
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 22a9f6ea-5b5f-4110-8a4e-9be9c983fbbb
caps.latest.revision: "4"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 4bc2b5a77a32e2209ef9ce0621d898486da3bc3e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="452---messagelogwarning"></a>452 - MessageLogWarning
## <a name="properties"></a>Propriétés  
  
|||  
|-|-|  
|ID|452|  
|Mots clés|Dépannage, WCFMessageLogging|  
|Niveau|Avertissement|  
|Canal|Microsoft-Windows-Application Server-Applications/Analyse|  
  
## <a name="description"></a>Description  
 Cet événement est émis lorsque l'avertissement du journal des messages est envoyé.  
  
## <a name="message"></a>Message  
 %1  
  
## <a name="details"></a>Détails  
  
|Nom d'élément de données|Type d'élément de données|Description|  
|--------------------|--------------------|-----------------|  
|data1|`xs:string`||  
|AppDomain|`xs:string`|Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.|
