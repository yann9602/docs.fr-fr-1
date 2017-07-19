---
title: "Instructions d&#39;installation du certificat de serveur des services Internet (IIS) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 11281490-d2ac-4324-8f33-e7714611a34b
caps.latest.revision: 18
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 18
---
# Instructions d&#39;installation du certificat de serveur des services Internet (IIS)
Pour pouvoir exécuter les exemples qui utilisent la communication sécurisée avec Internet Information Services \(IIS\), vous devez créer et installer un certificat de serveur.  
  
## Étape 1.Création de certificats  
 Pour créer un certificat pour votre ordinateur, ouvrez une invite de commandes de Visual studio avec des privilèges d'administrateur, puis exécutez le fichier Setup.bat inclus dans chacun des exemples qui utilisent la communication sécurisée avec IIS.Vérifiez que le chemin d'accès inclut le dossier qui contient Makecert.exe avant d'exécuter ce fichier batch.La commande suivante permet de créer le certificat dans Setup.bat.  
  
```  
makecert -sr LocalMachine -ss My -n CN=ServiceModelSamples-HTTPS-Server -sky exchange -sk ServiceModelSamples-HTTPS-Key  
```  
  
## Étape 2.Installation de certificats  
 La procédure d'installation des certificats que vous venez de créer varie en fonction de la version d'IIS utilisée.  
  
#### Pour installer IIS sur IIS 5.1 \(Windows XP\) et IIS 6.0 \(Windows Server 2003\)  
  
1.  Ouvrez le composant logiciel enfichable MMC du Gestionnaire des services IIS.  
  
2.  Cliquez avec le bouton droit sur le site Web par défaut, puis sélectionnez **Propriétés**.  
  
3.  Cliquez sur l'onglet **Sécurité de répertoire**.  
  
4.  Cliquez sur le bouton **Certificat de serveur**.L'Assistant de création de certificats de serveur Web démarre.  
  
5.  Suivez les instructions de l'Assistant.Sélectionnez l'option d'assignation de certificat.Sélectionnez le certificat ServiceModelSamples\-HTTPS\-Server dans la liste de certificats qui s'affiche.  
  
     ![Assistant Certificat IIS](../../../../docs/framework/wcf/samples/media/iiscertificate-wizard.GIF "IISCertificate\_Wizard")  
  
6.  Testez l'accès au service dans un navigateur, en utilisant l'adresse HTTPS suivante : https:\/\/localhost\/servicemodelsamples\/service.svc.  
  
#### Si SSL a été configuré précédemment via l'utilisation du fichier Httpcfg.exe :  
  
1.  Utilisez Makecert.exe \(ou exécutez Setup.bat\) pour créer le certificat de serveur.  
  
2.  Exécutez le Gestionnaire des services IIS et installez le certificat conformément aux instructions des étapes précédentes.  
  
3.  Ajoutez la ligne de code suivante au programme client :  
  
> [!IMPORTANT]
>  Ce code est uniquement requis pour les certificats de test tels que ceux créés par Makecert.exe.Il n'est pas recommandé pour le code de production.  
  
```  
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");  
```  
  
#### Pour installer IIS sur IIS 7.0 \(Windows Vista et Windows Server 2008\)  
  
1.  Dans le menu **Démarrer**, cliquez sur **Exécuter**, puis tapez **inetmgr** pour ouvrir le composant logiciel enfichable MMC Internet Information Services \(IIS\).  
  
2.  Cliquez avec le bouton droit sur **Site Web par défaut** et sélectionnez **Modifier les liaisons**.  
  
3.  Cliquez sur le bouton **Ajouter** dans la boîte de dialogue **Liaisons de sites**.  
  
4.  Dans la liste déroulante **Type**, sélectionnez **HTTPS**.  
  
5.  Sélectionnez le certificat **ServiceModelSamples\-HTTPS\-Server** dans la liste déroulante **Certificat SSL** et cliquez sur **OK**.  
  
6.  Testez l'accès au service dans un navigateur, en utilisant l'adresse HTTPS suivante : https:\/\/localhost\/servicemodelsamples\/service.svc.  
  
> [!NOTE]
>  Étant donné que le certificat de test que vous venez d'installer n'est pas un certificat approuvé, vous risquez de recevoir des avertissements de sécurité Internet Explorer supplémentaires lorsque vous recherchez des adresses Web locales sécurisées à l'aide de ce certificat.  
  
## Suppression de certificats  
  
-   Utilisez le Gestionnaire des services IIS comme indiqué précédemment, mais supprimez le certificat ou la liaison au lieu de l'ajouter.  
  
-   Supprimez le certificat d'ordinateur en utilisant la commande suivante.  
  
    ```  
    httpcfg delete ssl -i 0.0.0.0:443  
    ```