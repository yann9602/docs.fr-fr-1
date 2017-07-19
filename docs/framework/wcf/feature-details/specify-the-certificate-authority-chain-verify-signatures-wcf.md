---
title: "Comment&#160;: sp&#233;cifier la cha&#238;ne de certificats d&#39;autorit&#233; de certification utilis&#233;e pour v&#233;rifier des signatures (WCF) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "certificats (WCF), spécification de la chaîne de certificats d'autorité de certification"
  - "certificats (WCF), vérification des signatures"
ms.assetid: 7c719355-aa41-4567-80d0-5115a8cf73fd
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# Comment&#160;: sp&#233;cifier la cha&#238;ne de certificats d&#39;autorit&#233; de certification utilis&#233;e pour v&#233;rifier des signatures (WCF)
Lorsque [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] reçoit un message SOAP signé à l'aide d'un certificat X.509, par défaut il vérifie que le certificat X.509 a été publié par une autorité de certification approuvée.Il consulte pour cela un magasin de certificats et détermine si le certificat de cette autorité de certification a été désigné comme approuvé.Pour que [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] puisse effectuer cette détermination, la chaîne de certificats d'autorité de certification doit être installée dans le magasin de certificats correct.  
  
### Pour installer une chaîne de certificats d'autorité de certification  
  
-   Pour chaque autorité de certification publiant des certificats X.509 qu'un destinataire de message SOAP prévoit d'approuver, installez la chaîne de certificats d'autorité de certification dans le magasin de certificats à partir duquel [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] est configuré pour récupérer des certificats X.509.  
  
     Par exemple, si un destinataire de message SOAP prévoit d'approuver des certificats X.509 publiés par Microsoft, la chaîne de certificats d'autorité de certification pour Microsoft doit être installée dans le magasin de certificats dans lequel [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] est configuré pour rechercher des certificats X.509.Le magasin de certificats dans lequel [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] recherche des certificats X.509 peut être spécifié dans le code ou dans la configuration.Par exemple, cela peut être spécifié dans le code à l'aide de la méthode <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> ou dans la configuration de plusieurs manières, y compris le [\<serviceCertificate\>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md).  
  
     Windows étant fourni avec un ensemble de chaînes de certificats par défaut pour les autorités de certification approuvées, il ne sera peut\-être pas nécessaire d'installer la chaîne de certificats pour toutes les autorités de certification.  
  
    1.  Exportez la chaîne de certificats d'autorité de certification.  
  
         La procédure exacte dépend de l'autorité de certification.Si l'autorité de certification exécute les Services de certificat Microsoft, sélectionnez **Télécharger un certificat d'Autorité de certification, chaîne de certificat ou la liste de révocation de certificats**, puis **Télécharger un certificat de l'Autorité de certification**.  
  
    2.  Importez la chaîne de certificats d'autorité de certification.  
  
         Dans la console MMC \(Microsoft Management Console\), ouvrez le composant logiciel enfichable Certificats.Pour le magasin de certificats à partir duquel [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] est configuré pour récupérer des certificats X.509, sélectionnez le dossier **Autorités de certification** **racines de confiance**.Sous le dossier **Autorités de certification racines de confiance**, cliquez avec le bouton droit sur le dossier **Certificats**, pointez sur **Toutes les tâches**, puis cliquez sur **Importer**.Fournissez le fichier exporté à l'étape a.  
  
         [!INCLUDE[crabout](../../../../includes/crabout-md.md)] l'utilisation du composant logiciel enfichable Certificats avec la console MMC, consultez [Comment : afficher des certificats à l'aide du composant logiciel enfichable MMC](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).  
  
## Voir aussi  
 [Utilisation des certificats](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)