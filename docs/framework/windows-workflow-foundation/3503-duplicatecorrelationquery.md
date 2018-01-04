---
title: 3503 - DuplicateCorrelationQuery
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b857f8e6-ce4d-4da4-bc9d-6cd63fa558a4
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 997bdf4423364e9b5361635820849a6bde9e8960
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="3503---duplicatecorrelationquery"></a>3503 - DuplicateCorrelationQuery
## <a name="properties"></a>Propriétés  
  
|||  
|-|-|  
|ID|3503|  
|Mots clés|WFServices|  
|Niveau|Avertissement|  
|Canal|Microsoft-Windows-Application Server-Applications/Analyse|  
  
## <a name="description"></a>Description  
 Indique qu'un CorrelationQuery en double a été trouvé. Cette requête en double ne sera pas utilisée lors du calcul de la corrélation.  
  
## <a name="message"></a>Message  
 CorrelationQuery en double trouvé avec Where='%1'. Cette requête en double ne sera pas utilisée lors du calcul de la corrélation.  
  
## <a name="details"></a>Détails  
  
|Nom d'élément de données|Type d'élément de données|Description|  
|--------------------|--------------------|-----------------|  
|Où|xs:string|Partie Where de la requête de corrélation.|  
|AppDomain|xs:string|Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.|
