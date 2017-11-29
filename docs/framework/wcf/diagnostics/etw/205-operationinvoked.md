---
title: 205 - OperationInvoked
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9c8d6c90-dfa5-4ae0-a589-96679a8fb3ba
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2b0a96f1e3ba72a226d9b1a871382a27db61c57e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="205---operationinvoked"></a>205 - OperationInvoked
## <a name="properties"></a>Propriétés  
  
|||  
|-|-|  
|ID|205|  
|Mots clés|Dépannage, ServiceModel|  
|Niveau|Information|  
|Canal|Microsoft-Windows-Application Server-Applications/Analyse|  
  
## <a name="description"></a>Description  
 Cet événement est émis juste avant que l'`OperationInvoker` par défaut du modèle de service commence à appeler une méthode.  
  
## <a name="message"></a>Message  
 Un OperationInvoker a appelé la méthode '%1'. Informations sur l'appelant : '%2'.  
  
## <a name="details"></a>Détails  
  
|Nom d'élément de données|Type d'élément de données|Description|  
|--------------------|--------------------|-----------------|  
|Nom de la méthode|`xs:string`|Nom CLR de la méthode qui a été appelée par l'`OperationInvoker`.|  
|Informations relatives à l'appelant|`xs:string`|Adresse IP et numéro de port du client au format « Adresse IP:Numéro de port ». Les deux valeurs sont extraites de la propriété de message « System.ServiceModel.Channels.RemoteEndpointMessageProperty » dans le contexte de l'opération. Notez que pour les liaisons autres que TCP, cette valeur est `null`.|  
|HostReference|`xs:string`|Pour les services hébergés par le Web, ce champ identifie de manière unique le service dans la hiérarchie Web. Son format est défini en tant que ' chemin d’accès virtuel de Site Web de nom d’Application &#124; Chemin d’accès virtuel de service &#124; ServiceName'. Exemple : ' Default Web Site/CalculatorApplication &#124;/CalculatorService.svc &#124; CalculatorService ».|  
|AppDomain|`xs:string`|Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.|
