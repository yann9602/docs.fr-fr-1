---
title: "Comment : rendre des certificats X.509 accessibles à WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- X.509 certificates [WCF]
- certificates [WCF], making X.509 certificates accessible to WCF
- X.509 certificates [WCF], making accessible to WCF
ms.assetid: a54e407c-c2b5-4319-a648-60e43413664b
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b95ee7c28c67ff861dc401d1405306c78b9663de
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-make-x509-certificates-accessible-to-wcf"></a>Comment : rendre des certificats X.509 accessibles à WCF
Pour rendre un certificat X.509 accessible à [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)], le code d'application doit spécifier le nom et l'emplacement du magasin de certificats. Dans certains cas, l'identité du processus doit avoir accès au fichier contenant la clé privée associée au certificat X.509. Pour obtenir la clé privée associée à un certificat X.509 dans un magasin de certificats, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] doit disposer de l'autorisation requise. Par défaut, seuls le propriétaire et le compte système peuvent accéder à la clé privée d'un certificat.  
  
### <a name="to-make-x509-certificates-accessible-to-wcf"></a>Pour rendre des certificats X.509 accessibles à WCF  
  
1.  Accordez au compte sous lequel [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] s'exécute l'accès en lecture au fichier contenant la clé privée associée au certificat X.509.  
  
    1.  Déterminez si [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] requiert l'accès en lecture à la clé privée du certificat X.509.  
  
         Le tableau suivant précise si une clé privée doit être disponible lors de l'utilisation d'un certificat X.509.  
  
        |Utilisation d'un certificat X.509|Clé privée|  
        |---------------------------|-----------------|  
        |Signature numérique d'un message SOAP sortant.|Oui|  
        |Vérification de la signature d'un message SOAP entrant.|Non|  
        |Chiffrement d'un message SOAP sortant.|Non|  
        |Déchiffrement d'un message SOAP entrant.|Oui|  
  
    2.  Déterminez l'emplacement et le nom du magasin de certificats dans lequel le certificat est stocké.  
  
         Le magasin de certificats dans lequel le certificat est stocké est spécifié dans le code d'application ou dans la configuration. Ainsi, l'exemple suivant spécifie que le certificat se trouve dans le magasin de certificats `CurrentUser` nommé `My`.  
  
         [!code-csharp[x509Accessible#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/x509accessible/cs/source.cs#1)]
         [!code-vb[x509Accessible#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/x509accessible/vb/source.vb#1)]  
  
    3.  Déterminer où la clé privée pour le certificat se trouve sur l’ordinateur à l’aide de la [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) outil.  
  
         Le [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) outil nécessite le nom du magasin de certificat et emplacement du magasin de certificats quelque chose qui identifie de façon unique le certificat. Il accepte le nom de sujet du certificat ou son empreinte numérique comme identificateur unique. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Comment déterminer l’empreinte numérique d’un certificat, consultez [Comment : récupérer l’empreinte numérique d’un certificat](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).  
  
         Le de code suivant montre comment utiliser le [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) outil pour déterminer l’emplacement de la clé privée d’un certificat dans le `My` stocker dans `CurrentUser` avec une empreinte numérique de `46 dd 0e 7a ed 0b 7a 31 9b 02 a3 a0 43 7a d8 3f 60 40 92 9d`.  
  
        ```  
        findprivatekey.exe My CurrentUser -t "46 dd 0e 7a ed 0b 7a 31 9b 02 a3 a0 43 7a d8 3f 60 40 92 9d" -a  
        ```  
  
    4.  Déterminez le compte sous lequel [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] s'exécute.  
  
         Le tableau suivant précise le compte sous lequel [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] s'exécute pour un scénario donné.  
  
        |Scénario|Identité du processus|  
        |--------------|----------------------|  
        |Client (console ou application WinForms).|Utilisateur actuellement connecté.|  
        |Service auto-hébergé.|Utilisateur actuellement connecté.|  
        |Service hébergé dans IIS 6.0 ([!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]) ou IIS 7.0 ([!INCLUDE[wv](../../../../includes/wv-md.md)]).|SERVICE RÉSEAU|  
        |Service hébergé dans IIS 5.X ([!INCLUDE[wxp](../../../../includes/wxp-md.md)]).|Contrôlé par l'élément `<processModel>` dans le fichier Machine.config. Le compte par défaut est ASPNET.|  
  
    5.  Accordez l'accès en lecture au fichier contenant la clé privée du compte sous lequel [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] s'exécute, à l'aide d'un outil tel que cacls.exe.  
  
         L'exemple de code suivant modifie (/E) la liste de contrôle d'accès (ACL) du fichier spécifié pour accorder (/G) au compte SERVICE RÉSEAU l'accès en lecture (: R) au fichier.  
  
        ```  
        cacls.exe "C:\Documents and Settings\All Users\Application Data\Microsoft\Crypto\RSA\MachineKeys\8aeda5eb81555f14f8f9960745b5a40d_38f7de48-5ee9-452d-8a5a-92789d7110b1" /E /G "NETWORK SERVICE":R  
        ```  
  
## <a name="see-also"></a>Voir aussi  
 [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md)  
 [Guide pratique pour récupérer l’empreinte numérique d’un certificat](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md)  
 [Utilisation des certificats](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
