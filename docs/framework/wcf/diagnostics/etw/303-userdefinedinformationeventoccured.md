---
title: 303 - UserDefinedInformationEventOccured
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5ed5acaf-3755-4417-92c4-4ebc8e854ca1
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3bc04837834277dccc9d21d27e89c84f09f36167
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="303---userdefinedinformationeventoccured"></a>303 - UserDefinedInformationEventOccured
## <a name="properties"></a>Propriétés  
  
|||  
|-|-|  
|ID|303|  
|Mots clés|Dépannage, HealthMonitoring, UserEvents, ServiceModel, EndToEndMonitoring|  
|Niveau|Information|  
|Canal|Microsoft-Windows-Application Server-Applications/Analyse|  
  
## <a name="description"></a>Description  
 Cet événement est émis à partir du code utilisateur. Les développeurs peuvent émettre cet événement lorsqu'un événement d'informations personnalisé se produit dans leur service. Cela peut s'effectuer à l'aide des API <xref:System.Diagnostics.Eventing>. En outre, il existe un exemple WCF qui encapsule cette API et montre comment émettre correctement cet événement.  
  
## <a name="message"></a>Message  
 Nom : '%1', Référence : '%2', Charge : %3  
  
## <a name="details"></a>Détails  
  
|Nom d'élément de données|Type d'élément de données|Description|  
|--------------------|--------------------|-----------------|  
|Nom|`xs:string`|Nom de l'événement défini par l'utilisateur.|  
|HostReference|`xs:string`|Pour les services hébergés par le Web, ce champ identifie de manière unique le service dans la hiérarchie Web. Son format est défini en tant que ' chemin d’accès virtuel de Site Web de nom d’Application &#124; Chemin d’accès virtuel de service &#124; ServiceName'. Exemple : ' Default Web Site/CalculatorApplication &#124;/CalculatorService.svc &#124; CalculatorService ».|  
|Charge utile|`xs:string`|Charge utile de l'événement définie par l'utilisateur.|
