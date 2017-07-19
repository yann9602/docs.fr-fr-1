---
title: "Strat&#233;gie de protection &#233;tendue | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e2616a10-317e-4c34-8023-0c015a80a82f
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# Strat&#233;gie de protection &#233;tendue
La protection étendue est une initiative de sécurité visant à se protéger des attaques de l'intercepteur \(MITM, Man In The Middle\).  Une attaque de l'intercepteur est une atteinte à la sécurité dans laquelle un intercepteur prend les informations d'identification d'un client et les envoie à un serveur.  
  
## Démonstrations  
 Protection étendue  
  
## Discussion  
 Lorsque des applications s'authentifient à l'aide de Kerberos, de Digest ou de NTLM via le protocole HTTPS, un canal TLS \(Transport Level Security\) est d'abord établi, puis l'authentification s'effectue au moyen du canal sécurisé.  Toutefois, il n'existe aucune liaison entre la clé de session générée par SSL \(Secure Sockets Layer\) et celle qui est générée au cours de l'authentification.  Tout intercepteur peut s'établir entre le client et le serveur et commencer à transférer les requêtes émanant du client, même quand le canal de transport lui\-même est sécurisé, car le serveur n'a aucun moyen de savoir si le canal sécurisé est établi depuis le client ou un intercepteur.  Dans un tel scénario, la solution consiste à lier le canal TLS externe avec le canal d'authentification interne de façon à permettre au serveur de détecter la présence d'un intercepteur.  
  
> [!NOTE]
>  Cet exemple ne fonctionne que s'il est hébergé sur IIS et ne peut pas fonctionner sur Cassini \(serveur Visual Studio Development\), car Cassini ne prend pas en charge HTTPS.  
  
> [!NOTE]
>  Cette fonctionnalité est actuellement disponible uniquement sur Windows 7.  Les étapes suivantes sont propres à Windows 7.  
  
#### Pour configurer, générer et exécuter l'exemple  
  
1.  Installez Internet Information Services à partir du **Panneau de configuration**, **Ajout\/Suppression de programmes** et **Fonctionnalités de Windows**.  
  
2.  Installez **Authentification Windows** dans **Fonctionnalités de Windows**, **Internet Information Services**, **Services World Wide Web**, **Sécurité** et **Authentification Windows**.  
  
3.  Installez **Activation HTTP de Windows Communication Foundation** dans **Fonctionnalités de Windows**, **Microsoft .NET Framework 3.5.1** et **Activation HTTP de Windows Communication Foundation**.  
  
4.  Cet exemple requiert l'établissement par le client d'un canal sécurisé avec le serveur et nécessite donc la présence d'un certificat de serveur qui peut être installé à partir du Gestionnaire des services Internet \(IIS\).  
  
    1.  Ouvrez le Gestionnaire des services Internet \(IIS\).  Ouvrez **Certificats de serveur**, visible sous l'onglet **Affichage des fonctionnalités** lorsque le nœud racine \(nom de l'ordinateur\) est sélectionné.  
  
    2.  À des fins de test de cet exemple, créez un certificat auto\-signé.  Si vous ne souhaitez pas qu'Internet Explorer vous informe que le certificat n'est pas sécurisé, installez le certificat dans le magasin d'autorités racine approuvées de certificats.  
  
5.  Ouvrez le volet **Actions** du site Web par défaut.  Cliquez sur **Modifier le site** et **Liaisons**.  S'il n'est pas déjà présent, ajoutez le type HTTPS avec le numéro de port 443.  Assignez le certificat SSL créé au cours de l'étape précédente.  
  
6.  Générez le service.  Un répertoire virtuel est alors créé dans IIS et les fichiers dll, .svc et .config requis pour l'hébergement Web du service sont copiés.  
  
7.  Ouvrez le Gestionnaire des services Internet \(IIS\).  Cliquez avec le bouton droit sur le répertoire virtuel \(**ExtendedProtection**\), créé au cours de l'étape précédente.  Sélectionnez **Convertir en application**.  
  
8.  Ouvrez le module **Authentification** dans le Gestionnaire des services Internet \(IIS\) de ce répertoire virtuel et activez **Authentification Windows**.  
  
9. Ouvrez **Paramètres avancés** sous **Authentification Windows** pour ce répertoire virtuel et affectez\-lui la valeur **Obligatoire**.  
  
10. Vous pouvez tester le service en accédant à l'URL HTTPS à partir d'une fenêtre de navigateur \(fournissez un nom de domaine complet\).  Si vous souhaitez accéder à cette URL à partir d'un ordinateur distant, assurez\-vous que le pare\-feu est ouvert pour l'ensemble des connexions HTTP et HTTPS entrantes.  
  
11. Ouvrez le fichier de configuration du client et fournissez un nom de domaine complet pour le client ou l'attribut d'adresse du point de terminaison qui remplace `<<full_machine_name>>`.  
  
12. Exécutez le client.  Le client communique avec le service, qui établit un canal sécurisé et utilise la protection étendue.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur.  Recherchez le répertoire \(par défaut\) suivant avant de continuer.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n'existe pas, rendez\-vous sur la page \(éventuellement en anglais\) des [exemples Windows Communication Foundation \(WCF\) et Windows Workflow Foundation \(WF\) pour .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].  Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples\WCF\Basic\Services\Security\ExtendedProtection`