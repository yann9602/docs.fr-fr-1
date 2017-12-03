---
title: "Stratégie de protection étendue"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e2616a10-317e-4c34-8023-0c015a80a82f
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ef77df0681f7177a3b006b84d5ed3b60b7954555
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="extended-protection-policy"></a>Stratégie de protection étendue
La protection étendue est une initiative de sécurité visant à se protéger des attaques de l'intercepteur (MITM, Man In The Middle). Une attaque de l'intercepteur est une atteinte à la sécurité dans laquelle un intercepteur prend les informations d'identification d'un client et les envoie à un serveur.  
  
## <a name="demonstrates"></a>Démonstrations  
 Protection étendue  
  
## <a name="discussion"></a>Discussion  
 Lorsque des applications s'authentifient à l'aide de Kerberos, de Digest ou de NTLM via le protocole HTTPS, un canal TLS (Transport Level Security) est d'abord établi, puis l'authentification s'effectue au moyen du canal sécurisé. Toutefois, il n'existe aucune liaison entre la clé de session générée par SSL (Secure Sockets Layer) et celle qui est générée au cours de l'authentification. Tout intercepteur peut s'établir entre le client et le serveur et commencer à transférer les requêtes émanant du client, même quand le canal de transport lui-même est sécurisé, car le serveur n'a aucun moyen de savoir si le canal sécurisé est établi depuis le client ou un intercepteur. Dans un tel scénario, la solution consiste à lier le canal TLS externe avec le canal d'authentification interne de façon à permettre au serveur de détecter la présence d'un intercepteur.  
  
> [!NOTE]
>  Cet exemple ne fonctionne que s'il est hébergé sur IIS et ne peut pas fonctionner sur Cassini (serveur Visual Studio Development), car Cassini ne prend pas en charge HTTPS.  
  
> [!NOTE]
>  Cette fonctionnalité est actuellement disponible uniquement sur Windows 7. Les étapes suivantes sont propres à Windows 7.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple  
  
1.  Installez Internet Information Services à partir de **panneau**, **Ajout/Suppression de programmes**, **des fonctionnalités Windows**.  
  
2.  Installer **l’authentification Windows** dans **des fonctionnalités Windows**, **Internet Information Services**, **Services World Wide Web**,  **Sécurité**, et **l’authentification Windows**.  
  
3.  Installer **Activation Windows Communication Foundation HTTP** dans **des fonctionnalités Windows**, **Microsoft .NET Framework 3.5.1**, et **Communication de Windows Activation Foundation HTTP**.  
  
4.  Cet exemple requiert l'établissement par le client d'un canal sécurisé avec le serveur et nécessite donc la présence d'un certificat de serveur qui peut être installé à partir du Gestionnaire des services Internet (IIS).  
  
    1.  Ouvrez le gestionnaire des services Internet (IIS). Ouvrez **des certificats de serveur**, qui s’affiche dans le **affichage des fonctionnalités** onglet lorsque le nœud racine (nom de l’ordinateur) est sélectionné.  
  
    2.  À des fins de test de cet exemple, créez un certificat auto-signé. Si vous ne souhaitez pas qu'Internet Explorer vous informe que le certificat n'est pas sécurisé, installez le certificat dans le magasin d'autorités racine approuvées de certificats.  
  
5.  Ouvrez le **Actions** volet pour le site Web par défaut. Cliquez sur **de modifier le Site**, **liaisons**. S'il n'est pas déjà présent, ajoutez le type HTTPS avec le numéro de port 443. Assignez le certificat SSL créé au cours de l'étape précédente.  
  
6.  Générez le service. Un répertoire virtuel est alors créé dans IIS et les fichiers dll, .svc et .config requis pour l'hébergement Web du service sont copiés.  
  
7.  Ouvrez le gestionnaire des services Internet (IIS). Cliquez sur le répertoire virtuel (**ExtendedProtection**), qui a été créé à l’étape précédente. Sélectionnez **convertir en Application**.  
  
8.  Ouvrez le **authentification** module dans le Gestionnaire des services Internet pour ce répertoire virtuel et les activer **l’authentification Windows**.  
  
9. Ouvrez **paramètres avancés** sous **l’authentification Windows** pour ce répertoire virtuel et affectez-lui la valeur **requis**.  
  
10. Vous pouvez tester le service en accédant à l'URL HTTPS à partir d'une fenêtre de navigateur (fournissez un nom de domaine complet). Si vous souhaitez accéder à cette URL à partir d'un ordinateur distant, assurez-vous que le pare-feu est ouvert pour l'ensemble des connexions HTTP et HTTPS entrantes.  
  
11. Ouvrez le fichier de configuration du client et fournissez un nom de domaine complet pour le client ou l'attribut d'adresse du point de terminaison qui remplace `<<full_machine_name>>`.  
  
12. Exécutez le client. Le client communique avec le service, qui établit un canal sécurisé et utilise la protection étendue.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Security\ExtendedProtection`
