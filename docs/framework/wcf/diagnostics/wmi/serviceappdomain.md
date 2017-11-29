---
title: ServiceAppDomain
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f28e5186-a66d-46c1-abe9-b50e07f8cb4f
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 36048f56c3b54447a112e6f0a457624062ce965a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="serviceappdomain"></a>ServiceAppDomain
Mappe un service à un domaine d'application.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class ServiceAppDomain  
{  
  Service ref;  
  AppDomainInfo ref;  
};  
```  
  
## <a name="methods"></a>Méthodes  
 La classe ServiceAppDomain ne définit pas de méthode.  
  
## <a name="properties"></a>Propriétés  
 La classe ServiceAppDomain a les propriétés suivantes :  
  
### <a name="ref"></a>ref  
 Type de données : service  
Qualificateurs : clé  
  
 Type d'accès : lecture seule  
  
 Service de ce domaine d'application.  
  
### <a name="ref"></a>ref  
 Type de données : AppDomainInfo  
Qualificateurs : clé  
  
 Type d'accès : lecture seule  
  
 Contient des propriétés du domaine d'application.  
  
## <a name="requirements"></a>Spécifications  
  
|MOF|Déclaré dans Servicemodel.mof.|  
|---------|-----------------------------------|  
|Espace de noms|Défini dans root\ServiceModel|
