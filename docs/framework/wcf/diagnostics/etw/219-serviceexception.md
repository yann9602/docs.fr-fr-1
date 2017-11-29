---
title: 219 - ServiceException
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 81e2efac-39aa-4ed2-85a9-97eb8793b844
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: dd38ab45bceeee577d9e33f699a03a81c09dfc99
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="219---serviceexception"></a>219 - ServiceException
## <a name="properties"></a>Propriétés  
  
|||  
|-|-|  
|ID|219|  
|Mots clés|EndToEndMonitoring, HealthMonitoring, Dépannage, ServiceModel|  
|Niveau|Erreur|  
|Canal|Microsoft-Windows-Application Server-Applications/Analyse|  
  
## <a name="description"></a>Description  
 Cet événement est émis lorsqu'un service WCF rencontre une exception non gérée. Cela inclut les exceptions non gérées pendant l'activation, pendant le traitement du message et dans le code utilisateur.  
  
## <a name="message"></a>Message  
 Une exception non gérée de type '%2' s'est produite lors du traitement du message. Exception totale ToString : %1.  
  
## <a name="details"></a>Détails  
  
|Nom d'élément de données|Type d'élément de données|Description|  
|--------------------|--------------------|-----------------|  
|ExceptionToString|`xs:string`|Résultat de l'appel à `ToString`() sur l'exception CLR.|  
|ExceptionTypeName|`xs:string`|CLR FullName du type de l'exception.|  
|HostReference|`xs:string`|Pour les services hébergés par le Web, ce champ identifie de manière unique le service dans la hiérarchie Web. Son format est défini en tant que ' chemin d’accès virtuel de Site Web de nom d’Application &#124; Chemin d’accès virtuel de service &#124; ServiceName'. Exemple : ' Default Web Site/CalculatorApplication &#124;/CalculatorService.svc &#124; CalculatorService ».|  
|AppDomain|`xs:string`|Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.|
