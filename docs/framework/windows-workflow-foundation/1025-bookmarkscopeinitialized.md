---
title: 1025 - BookmarkScopeInitialized
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 63584434-e709-471d-9e96-97d3d99e70d6
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: caae26bbbab2ec9214c6801103f2e335f15ecf94
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="1025---bookmarkscopeinitialized"></a>1025 - BookmarkScopeInitialized
## <a name="properties"></a>Propriétés  
  
|||  
|-|-|  
|ID|1025|  
|Mots clés|WFRuntime|  
|Niveau|Verbose|  
|Canal|Microsoft-Windows-Application Server-Applications/Débogage|  
  
## <a name="description"></a>Description  
 Indique qu'un BookmarkScope a été initialisé.  
  
## <a name="message"></a>Message  
 Le BookmarkScope avec TemporaryId : « %1 » a été initialisé avec l'ID : « %2 ».  
  
## <a name="details"></a>Détails  
  
|Nom d'élément de données|Type d'élément de données|Description|  
|--------------------|--------------------|-----------------|  
|TemporaryId|xs:string|ID temporaire du signet.|  
|InitializedId|xs:string|Identificateur initialisé du signet.|  
|AppDomain|xs:string|Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.|
