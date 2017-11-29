---
title: "Comment : spécifier la chaîne de certificats d'autorité de certification utilisée pour vérifier des signatures (WCF)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- certificates [WCF], specifying the certificate authority certificate chain
- certificates [WCF], verifying signatures
ms.assetid: 7c719355-aa41-4567-80d0-5115a8cf73fd
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ce846d5637c6d49b4a3b1c6f28ae533e4900f696
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-specify-the-certificate-authority-certificate-chain-used-to-verify-signatures-wcf"></a>Comment : spécifier la chaîne de certificats d'autorité de certification utilisée pour vérifier des signatures (WCF)
Lorsque [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] reçoit un message SOAP signé à l'aide d'un certificat X.509, par défaut il vérifie que le certificat X.509 a été publié par une autorité de certification approuvée. Il consulte pour cela un magasin de certificats et détermine si le certificat de cette autorité de certification a été désigné comme approuvé. Pour que [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] puisse effectuer cette détermination, la chaîne de certificats d'autorité de certification doit être installée dans le magasin de certificats correct.  
  
### <a name="to-install-a-certification-authority-certificate-chain"></a>Pour installer une chaîne de certificats d'autorité de certification  
  
-   Pour chaque autorité de certification publiant des certificats X.509 qu'un destinataire de message SOAP prévoit d'approuver, installez la chaîne de certificats d'autorité de certification dans le magasin de certificats à partir duquel [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] est configuré pour récupérer des certificats X.509.  
  
     Par exemple, si un destinataire de message SOAP prévoit d'approuver des certificats X.509 publiés par Microsoft, la chaîne de certificats d'autorité de certification pour Microsoft doit être installée dans le magasin de certificats dans lequel [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] est configuré pour rechercher des certificats X.509. Le magasin de certificats dans lequel [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] recherche des certificats X.509 peut être spécifié dans le code ou dans la configuration. Par exemple, cela peut être spécifié dans le code à l’aide du <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> méthode ou dans la configuration de plusieurs façons, y compris le [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md) .  
  
     Windows étant fourni avec un ensemble de chaînes de certificats par défaut pour les autorités de certification approuvées, il ne sera peut-être pas nécessaire d'installer la chaîne de certificats pour toutes les autorités de certification.  
  
    1.  Exportez la chaîne de certificats d'autorité de certification.  
  
         La procédure exacte dépend de l'autorité de certification. Si l’autorité de certification est en cours d’exécution des Services de certificats Microsoft, sélectionnez **télécharger un certificat autorité de certification, chaîne de certificats ou la liste CRL**, puis choisissez **certificat d’autorité de certification télécharger**.  
  
    2.  Importez la chaîne de certificats d'autorité de certification.  
  
         Dans la console MMC (Microsoft Management Console), ouvrez le composant logiciel enfichable Certificats. Pour le certificat de magasin de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] est configuré pour récupérer des certificats X.509 dans, sélectionnez le **racine de confiance** **autorités de Certification**dossier. Sous le **autorités de Certification racines de confiance** dossier, avec le bouton droit le **certificats**dossier, pointez sur **toutes les tâches**, puis cliquez sur **importation** . Fournissez le fichier exporté à l'étape a.  
  
         [!INCLUDE[crabout](../../../../includes/crabout-md.md)]à l’aide du composant logiciel enfichable Certificats à la console MMC, consultez [Comment : afficher les certificats avec le composant logiciel enfichable MMC](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation des certificats](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
