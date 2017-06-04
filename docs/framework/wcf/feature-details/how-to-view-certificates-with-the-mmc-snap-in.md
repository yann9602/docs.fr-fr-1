---
title: "Comment&#160;: afficher des certificats &#224; l&#39;aide du composant logiciel enfichable MMC | Microsoft Docs"
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
  - "certificats (WCF), affichage avec le composant logiciel enfichable MMC"
ms.assetid: 2b8782aa-ebb4-4ee7-974b-90299e356dc5
caps.latest.revision: 12
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 12
---
# Comment&#160;: afficher des certificats &#224; l&#39;aide du composant logiciel enfichable MMC
Le certificat X.509 est un type courant d'information d'identification.Lorsque vous créez des clients ou des services sécurisés, vous pouvez spécifier l'utilisation d'un certificat comme informations d'identification de client ou de service en utilisant des méthodes telles que <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A>.Cette méthode requiert divers paramètres, tels que le magasin dans lequel le certificat est stocké ainsi qu'une valeur à utiliser lorsque vous recherchez ce certificat.La procédure suivante montre comment rechercher un certificat approprié dans les magasins d'un ordinateur.Pour obtenir un exemple de recherche d'empreinte numérique de certificat, consultez [Comment : récupérer l'empreinte numérique d'un certificat](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).  
  
### Pour afficher des certificats dans le composant logiciel enfichable MMC  
  
1.  Ouvrez une fenêtre Invite de commandes.  
  
2.  Tapez `mmc` et appuyez sur la touche ENTRÉE.Notez que pour afficher des certificats dans le magasin de l'ordinateur local, vous devez être dans le rôle Administrateur.  
  
3.  Dans le menu **Fichier**, cliquez sur **Ajouter\/Supprimer un composant logiciel enfichable**.  
  
4.  Cliquez sur **Ajouter**.  
  
5.  Dans la boîte de dialogue **Ajout d'un composant logiciel enfichable autonome**, sélectionnez **Certificats**.  
  
6.  Cliquez sur **Ajouter**.  
  
7.  Dans la boîte de dialogue du composant logiciel enfichable **Certificats**, sélectionnez **Le compte de l'ordinateur** et cliquez sur **Suivant**.Vous pouvez également sélectionner **Mon compte d'utilisateur** ou **Compte de service**.Si vous n'êtes pas administrateur de l'ordinateur, vous pouvez uniquement gérer les certificats de votre compte d'utilisateur.  
  
8.  Dans la boîte de dialogue **Sélectionner un ordinateur**, cliquez sur **Terminer**.  
  
9. Dans la boîte de dialogue **Ajout d'un composant logiciel enfichable autonome**, cliquez sur **Fermer**.  
  
10. Dans la boîte de dialogue **Ajouter\/Supprimer un composant logiciel enfichable**, cliquez sur **OK**.  
  
11. Dans la fenêtre **Racine de la console**, cliquez sur **Certificats \(ordinateur local\)** pour afficher les magasins de certificats de l'ordinateur.  
  
12. Facultatif.Pour consulter des certificats pour votre compte, répétez les étapes 3 à 6.À l'étape 7, au lieu de sélectionner **Le compte de l'ordinateur**, cliquez sur **Mon compte d'utilisateur** et répétez les étapes 8 à 10.  
  
13. Facultatif.Dans le menu **Fichier**, cliquez sur **Enregistrer** ou sur **Enregistrer sous**.Enregistrez le fichier de console pour une utilisation ultérieure.  
  
## Affichage de certificats à l'aide d'Internet Explorer  
 Vous pouvez également afficher, exporter, importer et supprimer des certificats à l'aide d'Internet Explorer.  
  
#### Pour afficher des certificats à l'aide d'Internet Explorer  
  
1.  Dans Internet Explorer, cliquez sur **Outils**, puis sur **Options Internet** pour afficher la boîte de dialogue **Options Internet**.  
  
2.  Cliquez sur l'onglet **Contenu**.  
  
3.  Sous **Certificats**, cliquez sur **Certificats**.  
  
4.  Pour afficher les détails d'un certificat, sélectionnez\-le et cliquez sur **Affichage**.  
  
## Voir aussi  
 [Utilisation des certificats](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)   
 [Comment : créer des certificats temporaires à utiliser au cours du développement](../../../../docs/framework/wcf/feature-details/how-to-create-temporary-certificates-for-use-during-development.md)   
 [Comment : récupérer l'empreinte numérique d'un certificat](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md)