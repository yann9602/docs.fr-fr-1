---
title: ServiceCredentials
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9c780793-4785-46f7-add9-ac1ebeadb614
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 73fad36b5bf14745ca70d297fa988b90d46990df
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="servicecredentials"></a>ServiceCredentials
ServiceCredentials  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class ServiceCredentials : Behavior  
{  
  string ClientCertificate;  
  string IssuedTokenAuthentication;  
  string Peer;  
  string SecureConversationAuthentication;  
  string ServiceCertificate;  
  string UserNameAuthentication;  
  string WindowsAuthentication;  
};  
```  
  
## <a name="methods"></a>Méthodes  
 La classe ServiceCredentials ne définit aucune méthode.  
  
## <a name="properties"></a>Propriétés  
 La classe ServiceCredentials a les propriétés suivantes :  
  
### <a name="clientcertificate"></a>ClientCertificate  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Paramètres d'authentification et d'approvisionnement des certificats clients pour ce service.  
  
### <a name="issuedtokenauthentication"></a>IssuedTokenAuthentication  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Paramètres actuels d'authentification de jeton émis pour ce service.  
  
### <a name="peer"></a>Peer  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Authentification des informations d'identification actuelles et fourniture des paramètres à utiliser par les points de terminaison de transport d'homologue.  
  
### <a name="secureconversationauthentication"></a>SecureConversationAuthentication  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Spécifie les paramètres actuels de conversation sécurisée.  
  
### <a name="servicecertificate"></a>ServiceCertificate  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Certificat associé à ce service.  
  
### <a name="usernameauthentication"></a>UserNameAuthentication  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Paramètres de nom d'utilisateur/mot de passe pour ce service.  
  
### <a name="windowsauthentication"></a>WindowsAuthentication  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Paramètres d'authentification Windows pour ce service.  
  
## <a name="requirements"></a>Configuration requise  
  
|MOF|Déclaré dans Servicemodel.mof.|  
|---------|-----------------------------------|  
|Espace de noms|Défini dans root\ServiceModel|  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.ServiceModel.Description.ServiceCredentials>
