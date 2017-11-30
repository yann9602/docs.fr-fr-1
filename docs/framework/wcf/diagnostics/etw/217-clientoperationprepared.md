---
title: 217 - ClientOperationPrepared
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ad207f04-b038-4f33-95e9-27a361df8ecd
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 5062d2c2146dae8b22165cfbea0c6a78241d17b8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="217---clientoperationprepared"></a>217 - ClientOperationPrepared
## <a name="properties"></a>Propriétés  
  
|||  
|-|-|  
|ID|217|  
|Mots clés|Dépannage, ServiceModel|  
|Niveau|Information|  
|Canal|Microsoft-Windows-Application Server-Applications/Analyse|  
  
## <a name="description"></a>Description  
 Cet événement est émis par des clients juste avant qu'une opération soit envoyée au service.  
  
## <a name="message"></a>Message  
 Le client exécute l'action '%1' associée au contrat '%2'. Le message sera envoyé à '%3'.  
  
## <a name="details"></a>Détails  
  
|Nom d'élément de données|Type d'élément de données|Description|  
|--------------------|--------------------|-----------------|  
|Action|`xs:string`|En-tête d'action SOAP du message sortant.|  
|Nom de contrat|`xs:string`|Nom du contrat. Exemple : ICalculator.|  
|Destination|`xs:string`|Adresse du point de terminaison de service auquel le message est envoyé.|  
|HostReference|`xs:string`|Pour les services hébergés par le Web, ce champ identifie de manière unique le service dans la hiérarchie Web. Son format est défini en tant que ' chemin d’accès virtuel de Site Web de nom d’Application &#124; Chemin d’accès virtuel de service &#124; ServiceName'. Exemple : ' Default Web Site/CalculatorApplication &#124;/CalculatorService.svc &#124; CalculatorService ».|  
|AppDomain|`xs:string`|Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.|
