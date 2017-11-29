---
title: 211 - ParameterInspectorAfterCallInvoked
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c0e21297-10b8-4456-a0e1-e019145cd5ac
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a66941a9b505267e976620bed238b02440968f14
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="211---parameterinspectoraftercallinvoked"></a>211 - ParameterInspectorAfterCallInvoked
## <a name="properties"></a>Propriétés  
  
|||  
|-|-|  
|ID|211|  
|Mots clés|Dépannage, ServiceModel|  
|Niveau|Information|  
|Canal|Microsoft-Windows-Application Server-Applications/Analyse|  
  
## <a name="description"></a>Description  
 Cet événement est émis après que le modèle de service a appelé la méthode `AfterCall` sur un `ParameterInspector`.  
  
## <a name="message"></a>Message  
 Le répartiteur a appelé 'AfterCall' sur un ParameterInspector de type '%1'.  
  
## <a name="details"></a>Détails  
  
|Nom d'élément de données|Type d'élément de données|Description|  
|--------------------|--------------------|-----------------|  
|Nom de type|`xs:string`|CLR FullName du type de `ParameterInspector` appelé.|  
|HostReference|`xs:string`|Pour les services hébergés par le Web, ce champ identifie de manière unique le service dans la hiérarchie Web. Son format est défini en tant que ' chemin d’accès virtuel de Site Web de nom d’Application &#124; Chemin d’accès virtuel de service &#124; ServiceName'. Exemple : ' Default Web Site/CalculatorApplication &#124;/CalculatorService.svc &#124; CalculatorService ».|  
|AppDomain|`xs:string`|Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.|
