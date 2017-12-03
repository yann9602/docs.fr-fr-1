---
title: ClientCredentials
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 41dffd6b-8f14-4fed-aefb-2a1bb168efb3
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 55f7ef12f67bd719f72f158a1fca6f120b4f448a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="clientcredentials"></a>ClientCredentials
ClientCredentials  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class ClientCredentials : Behavior  
{  
  string ClientCertificate;  
  string HttpDigest;  
  string IssuedToken;  
  string Peer;  
  string ServiceCertificate;  
  boolean SupportInteractive;  
  string UserName;  
  string Windows;  
};  
```  
  
## <a name="methods"></a>Méthodes  
 La classe ClientCredentials ne définit pas de méthode.  
  
## <a name="properties"></a>Propriétés  
 La classe ClientCredentials a les propriétés suivantes :  
  
### <a name="clientcertificate"></a>ClientCertificate  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Certificat X.509 que le client utilise pour s'authentifier auprès du service.  
  
### <a name="httpdigest"></a>HttpDigest  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Informations d'identification Http Digest actuelles.  
  
### <a name="issuedtoken"></a>IssuedToken  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Adresse de point de terminaison et liaison utilisées pour contacter le service de jetons de sécurité local.  
  
### <a name="peer"></a>Peer  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Informations d'identification que le nœud d'homologue utilise pour s'authentifier auprès d'autres nœuds dans la maille.  
  
### <a name="servicecertificate"></a>ServiceCertificate  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Certificat X.509 du service.  
  
### <a name="supportinteractive"></a>SupportInteractive  
 Type de données : booléen  
  
 Type d'accès : lecture seule  
  
 Valeur booléenne qui spécifie si les informations d'identification prennent en charge la négociation interactive.  
  
### <a name="username"></a>Nom d'utilisateur  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Nom d'utilisateur et mot de passe que le client utilise pour s'authentifier auprès du service.  
  
### <a name="windows"></a>Windows  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Informations d'identification que le client utilise pour s'authentifier auprès du service.  
  
## <a name="requirements"></a>Spécifications  
  
|MOF|Déclaré dans Servicemodel.mof.|  
|---------|-----------------------------------|  
|Espace de noms|Défini dans root\ServiceModel|  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.ServiceModel.Description.ClientCredentials>
