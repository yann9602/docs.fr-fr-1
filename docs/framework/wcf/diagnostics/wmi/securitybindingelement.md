---
title: SecurityBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ef93b6e6-3524-48a8-94d3-c8837f1872f9
caps.latest.revision: "8"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: b567c173c5a04421bce57585d96b8b45144c5625
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="securitybindingelement"></a>SecurityBindingElement
SecurityBindingElement  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class SecurityBindingElement : BindingElement  
{  
  string DefaultAlgorithmSuite;  
  boolean IncludeTimestamp;  
  string KeyEntropyMode;  
  LocalServiceSecuritySettings LocalServiceSecuritySettings;  
  string MessageSecurityVersion;  
  string SecurityHeaderLayout;  
};  
```  
  
## <a name="methods"></a>Méthodes  
 La classe SecurityBindingElement ne définit pas de méthode.  
  
## <a name="properties"></a>Propriétés  
 La classe SecurityBindingElement a les propriétés suivantes :  
  
### <a name="defaultalgorithmsuite"></a>DefaultAlgorithmSuite  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Spécifie les algorithmes à utiliser avec la liaison.  
  
### <a name="includetimestamp"></a>IncludeTimestamp  
 Type de données : booléen  
  
 Type d'accès : lecture seule  
  
 Valeur booléenne qui spécifie si chaque message contient un horodatage.  
  
### <a name="keyentropymode"></a>KeyEntropyMode  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Source d'entropie utilisée pour créer des clés.  
  
### <a name="localservicesecuritysettings"></a>LocalServiceSecuritySettings  
 Type de données : LocalServiceSecuritySettings  
  
 Type d'accès : lecture seule  
  
 Propriétés de sécurité spécifiques d'une liaison pour le service local.  
  
### <a name="messagesecurityversion"></a>MessageSecurityVersion  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Version utilisée pour la sécurité de message.  
  
### <a name="securityheaderlayout"></a>SecurityHeaderLayout  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Ordre des éléments dans l'en-tête de sécurité pour cette liaison.  
  
## <a name="requirements"></a>Spécifications  
  
|MOF|Déclaré dans Servicemodel.mof.|  
|---------|-----------------------------------|  
|Espace de noms|Défini dans root\ServiceModel|  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.ServiceModel.Channels.SecurityBindingElement>
