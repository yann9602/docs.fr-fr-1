---
title: "ReadMe pour l&#39;exemple d&#39;authentification de protection &#233;tendue | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 80bf2e97-398d-4db5-9040-d96478a2ccab
caps.latest.revision: 3
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 3
---
# ReadMe pour l&#39;exemple d&#39;authentification de protection &#233;tendue
La protection étendue est une initiative de sécurité assurant la protection contre les attaques de l'intercepteur, dans lesquelles un intrus \(« man\-in\-the\-middle »\) intercepte les informations d'identification d'un client et les utilise pour accéder à des ressources sécurisées sur le serveur choisi par le client.  
  
 Pour plus d'informations, consultez [Vue d'ensemble de la protection étendue de l'authentification](../../../../docs/framework/wcf/feature-details/extended-protection-for-authentication-overview.md).  
  
> [!NOTE]
>  Cet exemple fonctionne uniquement dans le cadre d'un hébergement sur IIS.Ile ne fonctionne pas sur Visual Studio Development Server car il ne prend pas en charge HTTPS.  
  
## Pour configurer, générer et exécuter l'exemple  
  
1.  Installez IIS sur l'ordinateur via Ajout\/Suppression de programmes \-\> Fonctionnalités de Windows.  
  
2.  Activez Authentification Windows dans les fonctionnalités de Windows : Internet Information Services \-\> Services World Wide Web \-\> Sécurité \-\> Authentification Windows.  
  
3.  Activez Activation HTTP dans les fonctionnalités de Windows : Microsoft .NET Framework 3.5.1 \-\> Activation HTTP de Windows Communication Foundation.  
  
4.  Cet exemple requiert l'établissement par le client d'un canal sécurisé avec le serveur et nécessite la présence d'un certificat de serveur qui peut être installé à partir du gestionnaire des services IIS \(Internet Information Services\).  
  
    1.  Ouvrez le gestionnaire des services IIS \-\> Certificats de serveur \(à partir de l'onglet d'affichage des fonctionnalités\).  
  
    2.  À des fins de test de cet exemple, vous pouvez créer un certificat auto\-signé.\(Si vous ne souhaitez pas qu'Internet Explorer vous informe que le certificat n'est pas sécurisé, vous pouvez l'installer dans la banque d'autorités racine approuvées de certificats\).  
  
5.  Accédez au volet Actions pour le site Web par défaut.Cliquez sur Modifier le site \-\> Liaisons.Ajoutez HTTPS comme type s'il ne l'est pas encore, avec le numéro de port 443, et affectez le certificat SSL créé à l'étape précédente.  
  
6.  Générez le service.Un répertoire virtuel est alors créé dans IIS \(à partir de l'action post\-build spécifiée dans les propriétés de projet\) et les fichiers dll, .svc et de configuration sont copiés comme requis pour l'hébergement d'un service sur le Web.  
  
7.  Ouvrez le gestionnaire des services IIS.Cliquez avec le bouton droit sur le répertoire virtuel \(ExtendedProtection\) que vous avez créé à l'étape précédente et sélectionnez Convertir en application.  
  
8.  Ouvrez le module Authentification dans le gestionnaire des services IIS de ce répertoire virtuel et activez l'authentification Windows.  
  
9. Ouvrez les paramètres avancés de l'authentification Windows pour ce répertoire virtuel et définissez la valeur Requis, car, dans cet exemple, le paramètre ExtendedProtection correspondant est défini sur Toujours.  
  
10. Vous pouvez tester le service en accédant à l'URL depuis une fenêtre de navigateur.Si vous souhaitez accéder à cette URL depuis plusieurs ordinateurs, assurez\-vous que le pare\-feu est ouvert pour l'ensemble des connexions HTTP et HTTPS entrantes.  
  
11. Ouvrez le fichier de configuration client et fournissez un nom d'ordinateur complet pour l'attribut d'adresse \<client\> \- \<point de terminaison\>, en remplaçant \<\<nom\_complet\_ordinateur\>\>.  
  
12. Exécutez le client.Le client communique avec le service en établissant un canal sécurisé et en utilisant une protection étendue de manière discrète.