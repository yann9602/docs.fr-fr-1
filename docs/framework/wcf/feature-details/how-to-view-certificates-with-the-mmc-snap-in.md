---
title: "Comment : afficher des certificats à l'aide du composant logiciel enfichable MMC"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: certificates [WCF], viewing with the MMC snap-in
ms.assetid: 2b8782aa-ebb4-4ee7-974b-90299e356dc5
caps.latest.revision: "12"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 43925a301d4f0d2ca1a852912255be49dd330ae5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-view-certificates-with-the-mmc-snap-in"></a>Comment : afficher des certificats à l'aide du composant logiciel enfichable MMC
Le certificat X.509 est un type courant d'information d'identification. Lorsque vous créez des clients ou des services sécurisés, vous pouvez spécifier l'utilisation d'un certificat comme informations d'identification de client ou de service en utilisant des méthodes telles que <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A>. Cette méthode requiert divers paramètres, tels que le magasin dans lequel le certificat est stocké ainsi qu'une valeur à utiliser lorsque vous recherchez ce certificat. La procédure suivante montre comment rechercher un certificat approprié dans les magasins d'un ordinateur. Pour obtenir un exemple de recherche de l’empreinte de certificat, consultez [Comment : récupérer l’empreinte numérique d’un certificat](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).  
  
### <a name="to-view-certificates-in-the-mmc-snap-in"></a>Pour afficher des certificats dans le composant logiciel enfichable MMC  
  
1.  Ouvrez une fenêtre Invite de commandes.  
  
2.  Type `mmc` et appuyez sur ENTRÉE. Notez que pour afficher des certificats dans le magasin de l'ordinateur local, vous devez être dans le rôle Administrateur.  
  
3.  Sur le **fichier** menu, cliquez sur **ajouter/supprimer un composant logiciel enfichable**.  
  
4.  Cliquez sur **Ajouter**.  
  
5.  Dans le **ajouter Standalone Snap-in** boîte de dialogue, sélectionnez **certificats**.  
  
6.  Cliquez sur **Ajouter**.  
  
7.  Dans le **enfichable Certificats** boîte de dialogue, sélectionnez **compte d’ordinateur** et cliquez sur **suivant**. Si vous le souhaitez, vous pouvez sélectionner **mon compte d’utilisateur** ou **compte de Service**. Si vous n'êtes pas administrateur de l'ordinateur, vous pouvez uniquement gérer les certificats de votre compte d'utilisateur.  
  
8.  Dans le **sélectionner un ordinateur** boîte de dialogue, cliquez sur **Terminer**.  
  
9. Dans le **ajouter Standalone Snap-in** boîte de dialogue, cliquez sur **fermer**.  
  
10. Sur le **ajouter/supprimer un composant logiciel enfichable** boîte de dialogue, cliquez sur **OK**.  
  
11. Dans le **racine de la Console** fenêtre, cliquez sur **certificats (ordinateur Local)** pour afficher le certificat des magasins pour l’ordinateur.  
  
12. Facultatif. Pour consulter des certificats pour votre compte, répétez les étapes 3 à 6. À l’étape 7, au lieu de sélectionner **compte d’ordinateur**, cliquez sur **mon compte d’utilisateur** et répétez les étapes 8 à 10.  
  
13. Facultatif. Sur le **fichier** menu, cliquez sur **enregistrer** ou **Enregistrer sous**. Enregistrez le fichier de console pour une utilisation ultérieure.  
  
## <a name="viewing-certificates-with-internet-explorer"></a>Affichage de certificats à l'aide d'Internet Explorer  
 Vous pouvez également afficher, exporter, importer et supprimer des certificats à l'aide d'Internet Explorer.  
  
#### <a name="to-view-certificates-with-internet-explorer"></a>Pour afficher des certificats à l'aide d'Internet Explorer  
  
1.  Dans Internet Explorer, cliquez sur **outils**, puis cliquez sur **Options Internet** pour afficher les **Options Internet** boîte de dialogue.  
  
2.  Cliquez sur le **contenu** onglet.  
  
3.  Sous **certificats**, cliquez sur **certificats**.  
  
4.  Pour afficher les détails d’un certificat, sélectionnez le certificat, cliquez sur **vue**.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation des certificats](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [Comment : créer des certificats temporaires à utiliser pendant le développement](../../../../docs/framework/wcf/feature-details/how-to-create-temporary-certificates-for-use-during-development.md)  
 [Comment : récupérer l’empreinte numérique d’un certificat](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md)
