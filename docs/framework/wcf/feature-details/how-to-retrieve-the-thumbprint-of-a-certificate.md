---
title: "Comment&#160;: r&#233;cup&#233;rer l&#39;empreinte num&#233;rique d&#39;un certificat | Microsoft Docs"
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
  - "certificats [WCF], récupération d'empreinte numérique"
ms.assetid: da3101aa-78cd-4c34-9652-d1f24777eeab
caps.latest.revision: 15
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 15
---
# Comment&#160;: r&#233;cup&#233;rer l&#39;empreinte num&#233;rique d&#39;un certificat
Lors de l'écriture d'une application [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] qui utilise un certificat X.509 pour l'authentification, il est souvent nécessaire de spécifier les revendications incluses dans le certificat. Par exemple, vous devez fournir une revendication d'empreinte numérique lors de l'utilisation de l'énumération <xref:System.Security.Cryptography.X509Certificates.X509FindType> dans la méthode <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A>. La recherche de la valeur de revendication s'effectue en deux étapes. En premier lieu, ouvrez le composant logiciel enfichable MMC \(Microsoft Management Console\) pour les certificats. \(Consultez [Comment : afficher des certificats à l'aide du composant logiciel enfichable MMC](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).\) Ensuite, comme décrit ici, recherchez un certificat approprié et copiez son empreinte numérique \(ou d'autres valeurs de revendication\).  
  
 Si vous utilisez un certificat pour l'authentification du service, il est important de noter la valeur de la colonne **Délivré à** \(la première colonne dans la console\). Lors de l'utilisation du protocole SSL \(Secure Sockets Layer\) comme sécurité de transport, l'un des premiers contrôles effectués consiste à comparer l'URI \(Uniform Resource Identifier\) d'adresse de base d'un service à la valeur **Délivré à**. Les valeurs doivent correspondre ou le processus d'authentification s'interrompt.  
  
 Vous pouvez également vous servir de l'outil Makecert.exe dans le Kit de développement logiciel \(SDK\) [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] pour créer des certificats temporaires à utiliser uniquement lors du développement. Toutefois, par défaut, ce type de certificat n'est pas délivré par une autorité de certification, il est donc inutilisable à des fins de production.[!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [Comment : créer des certificats temporaires à utiliser au cours du développement](../../../../docs/framework/wcf/feature-details/how-to-create-temporary-certificates-for-use-during-development.md).  
  
### Pour récupérer l'empreinte numérique d'un certificat  
  
1.  Ouvrez le composant logiciel enfichable MMC \(Microsoft Management Console\) pour les certificats. \(Consultez [Comment : afficher des certificats à l'aide du composant logiciel enfichable MMC](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).\)  
  
2.  Dans le volet gauche de la fenêtre **Racine de la console**, cliquez sur **Certificats \(ordinateur local\)**.  
  
3.  Cliquez sur le dossier **Personnel** pour le développer.  
  
4.  Cliquez sur le dossier **Certificats** pour le développer.  
  
5.  Dans la liste de certificats, notez le titre **Rôles prévus**. Recherchez un certificat qui répertorie **Authentification du client** comme rôle prévu.  
  
6.  Double\-cliquez sur le certificat.  
  
7.  Dans la boîte de dialogue **Certificat**, cliquez sur l'onglet **Détails**.  
  
8.  Faites défiler la liste de champs et cliquez sur **Empreinte numérique**.  
  
9. Copiez les caractères hexadécimaux de la zone. Si cette empreinte numérique est utilisée dans le code pour `X509FindType`, supprimez les espaces entre les nombres hexadécimaux. Par exemple, l'empreinte numérique "a9 09 50 2d d8 2a e4 14 33 e6 f8 38 86 b0 0d 42 77 a3 2a 7b" doit être spécifiée sous la forme "a909502dd82ae41433e6f83886b00d4277a32a7b" dans le code.  
  
## Voir aussi  
 <xref:System.Security.Cryptography.X509Certificates.X509FindType>   
 <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A>   
 [Comment : configurer un port avec un certificat SSL](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)   
 [Comment : afficher des certificats à l'aide du composant logiciel enfichable MMC](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md)   
 [Comment : créer des certificats temporaires à utiliser au cours du développement](../../../../docs/framework/wcf/feature-details/how-to-create-temporary-certificates-for-use-during-development.md)