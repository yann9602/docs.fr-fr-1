---
title: 221 - MessageReceivedFromTransport
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4995f0d5-c182-4d97-981f-6951da6df1fb
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 4f977f938844f48182be6662f489506e8119fe67
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="221---messagereceivedfromtransport"></a>221 - MessageReceivedFromTransport
## <a name="properties"></a>Propriétés  
  
|||  
|-|-|  
|ID|221|  
|Mots clés|EndToEndMonitoring, Dépannage, ServiceModel|  
|Niveau|Information|  
|Canal|Microsoft-Windows-Application Server-Applications/Analyse|  
  
## <a name="description"></a>Description  
 Cet événement est émis lorsque le modèle de service reçoit un message du transport.  
  
## <a name="message"></a>Message  
 Le répartiteur a reçu un message du transport. ID de corrélation == '%1.'  
  
## <a name="details"></a>Détails  
  
|Nom d'élément de données|Type d'élément de données|Description|  
|--------------------|--------------------|-----------------|  
|ID de corrélation|`xs:GUID`|ID d'activité utilisé pour mettre en corrélation un événement `MessageSentToTransport` provenant d'un service ou d'un client avec son événement `MessageReceivedFromTransport` correspondant à l'autre bout.|  
|HostReference|`xs:string`|Pour les services hébergés par le Web, ce champ identifie de manière unique le service dans la hiérarchie Web. Son format est défini en tant que ' chemin d’accès virtuel de Site Web de nom d’Application &#124; Chemin d’accès virtuel de service &#124; ServiceName'. Exemple : ' Default Web Site/CalculatorApplication &#124;/CalculatorService.svc &#124; CalculatorService ».|  
|AppDomain|`xs:string`|Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.|
