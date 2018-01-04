---
title: System.ServiceModel.Channels.PeerNodeAuthenticationFailure
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0b50f782-ca06-4a82-aa7f-71f78ddc5177
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4ffca9a587bdb32afc252f9719eb35e3139dd3f8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="systemservicemodelchannelspeernodeauthenticationfailure"></a>System.ServiceModel.Channels.PeerNodeAuthenticationFailure
Une négociation de sécurité avec un voisin potentiel n'a pas réussi.  
  
## <a name="description"></a>Description  
 Cette trace se produit lors de la tentative d'établissement d'une connexion de voisin sécurisée. Cela peut arriver lorsque les informations d'identification sont incomplètes ou incorrectes.  
  
 PeerChannel reconnaît un seul type de jeton pour les certificats d'identification X.509 puissants qui fournissent un modèle d'identité performant basé sur le type d'authentification et d'autorisation qui peut être implémenté. PeerChannel prend également en charge les applications simples via l'utilisation de mots de passe. Les mots de passe peuvent uniquement être utilisés pour autoriser l'entrée à la session, mais ne peuvent pas l'être pour effectuer l'authentification des messages. Cela et dû au fait qu'un jeton symétrique partagé par un groupe d'homologues est difficile à utiliser et s'avère inapproprié pour l'authentification de la source.  
  
## <a name="troubleshooting"></a>Résolution des problèmes  
 Vérifiez que tous les voisins ont les informations d'identification de sécurité appropriées.  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurité de canal homologue](../../../../../docs/framework/wcf/feature-details/peer-channel-security.md)  
 [Suivi](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [Utilisation du suivi pour résoudre les problèmes posés par votre application](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [Administration et diagnostics](../../../../../docs/framework/wcf/diagnostics/index.md)
