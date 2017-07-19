---
title: "3550 - BufferOutOfOrderMessageNoInstance | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1299d294-99b8-430e-98b1-55f5f17002f3
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# 3550 - BufferOutOfOrderMessageNoInstance
## Propriétés  
  
|||  
|-|-|  
|ID|3550|  
|Mots clés|WFServices|  
|Niveau|Information|  
|Canal|Microsoft\-Windows\-Application Server\-Applications\/Analyse|  
  
## Description  
 Indique qu'une réception mise en mémoire tampon a échoué.  Une autre tentative d'opération sera faite lorsque l'instance de service sera prête à traiter cette opération.  
  
## Message  
 Impossible d'effectuer l'opération « %1 » actuellement.  Une autre tentative sera faite lorsque l'instance de service sera prête à traiter cette opération.  
  
## Détails  
  
|Nom d'élément de données|Type d'élément de données|Description|  
|------------------------------|-------------------------------|-----------------|  
|OperationName|xs:string|Nom de l'opération.|  
|AppDomain|xs:string|Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.|