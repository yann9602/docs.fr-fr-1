---
title: "S&#233;lection et validation de certificats | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
ms.assetid: c933aca2-4cd0-4ff1-9df9-267143f25a6f
caps.latest.revision: 15
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 15
---
# S&#233;lection et validation de certificats
Les classes d' <xref:System.Net> prennent en charge plusieurs moyens de sélectionner et valider <xref:System.Security.Cryptography.X509Certificates> pour les connexions SSL de Socket Layer \(SSL\).  Un client peut sélectionner un ou plusieurs certificats pour s'authentifier à un serveur.  Un serveur peut avoir besoin d'un certificat client ont un ou plusieurs attributs spécifiques pour l'authentification.  
  
## Définition  
 Un certificat est un flux d'octets ASCII qui contient une clé publique, les attributs \(tels que le numéro de version, le nombre de série, et la date d'expiration\) et une signature numérique d'une autorité de certification.  Les certificats sont utilisés pour établir une connexion chiffrée ou pour authentifier un client à un serveur.  
  
## Sélection et validation de certificat client  
 Un client peut sélectionner un ou plusieurs certificats pour une connexion SSL spécifique.  Les certificats clients peuvent être associés à la connexion SSL sur un serveur Web ou un Serveur de messagerie SMTP.  Un client ajoute des certificats à une collection d' <xref:System.Security.Cryptography.X509Certificates.X509Certificate> ou d'objets de classe d' <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> .  À l'aide de la messagerie électronique par exemple, la collection de certificat est une instance d' <xref:System.Security.Cryptography.X509Certificates.X509CertificateCollection>\) associé à la propriété d' <xref:System.Net.Mail.SmtpClient.ClientCertificates%2A> de la classe d' <xref:System.Net.Mail.SmtpClient> .  La classe d' <xref:System.Net.HttpWebRequest> a une propriété similaire d' <xref:System.Net.HttpWebRequest.ClientCertificates%2A> .  
  
 La principale différence entre <xref:System.Security.Cryptography.X509Certificates.X509Certificate> et la classe d' <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> est que la clé privée doit résider dans le magasin de certificats pour la classe d' <xref:System.Security.Cryptography.X509Certificates.X509Certificate> .  
  
 Même si les certificats sont ajoutés à une collection et associés à une connexion SSL spécifique, aucun certificat n'est envoyé au serveur à moins que le serveur d'application.  Si plusieurs certificats clients sont placés sur une connexion, la meilleure sera utilisée sur un algorithme qui considère que la correspondance entre la liste d'émetteurs de certificat fournis par le serveur et le nom d'expéditeur de certificat client.  
  
 La classe d' <xref:System.Net.Security.SslStream> offre encore plus de contrôle sur la négociation SSL.  Un client peut spécifier un délégué pour choisir quelle certificat client à utiliser.  
  
 Un serveur distant peut vérifier qu'un certificat client est valide, actuel, et signé par l'autorité de certification appropriée.  Un délégué peut être ajouté à <xref:System.Net.ServicePointManager.ServerCertificateValidationCallback%2A> pour appliquer la validation de certificat.  
  
## Sélection de certificat client  
 Le .NET Framework sélectionne le certificat client pour présenter à partir de la manière suivante :  
  
1.  Si un certificat client a été présenté précédemment au serveur, le certificat est mis en cache une fois d'abord présenté et est réutilisé pour les demandes suivantes de certificat client.  
  
2.  Si un délégué est présent, utilisez toujours le résultat du délégué comme certificat client pour sélectionner.  Essayez d'utiliser un certificat mis en cache si possible, mais n'utilisez pas les informations d'identification anonymes mises en cache si le délégué est retourné null et la collection de certificat n'est pas vide.  
  
3.  Si c'est la première défi pour un certificat client, l'infrastructure énumère les certificats dans <xref:System.Security.Cryptography.X509Certificates.X509Certificate> ou les objets de classe d' <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> associés à la connexion, la recherche une correspondance entre la liste d'émetteurs de certificat fournis par le serveur et le nom d'expéditeur de certificat client.  Le premier certificat qui correspond est envoyée au serveur.  Si aucun certificat ne correspond ou la collection de certificat est vide, une informations d'identification anonyme est envoyée au serveur.  
  
## Outils pour la configuration de certificat  
 Plusieurs outils disponibles pour la configuration de certificats clients et serveur.  
  
 l'outil de *Winhttpcertcfg.exe* peut être utilisé pour configurer des certificats client.  L'outil de *Winhttpcertcfg.exe* est fourni comme l'un des outils du kit de ressources Windows Server 2003.  Cet outil est également disponible en téléchargement dans le cadre de les outils du Kit de ressources Windows Server 2003 dans www.microsoft.com.  
  
 L'outil de*Le HttpCfg.exe* peut être utilisé pour configurer des certificats du serveur de la classe d' <xref:System.Net.HttpListener> .  L'outil de *HttpCfg.exe* est fourni comme l'un des outils de prise en charge pour Windows Server 2003 et Windows XP Service Pack 2.  *HttpCfg.exe* et les autres outils de charge ne sont pas installés par défaut sous Windows Server 2003 ou Windows XP.  Sur Windows Server 2003.  les outils de charge sont installés séparément à partir de le dossier suivant et du fichier sur le CD\-ROM Windows Server 2003 :  
  
 \\Support\\Tools\\Suptools .msi  
  
 Pour être utilisées avec les Windows XP Service Pack 2, les outils de prise en charge Windows XP sont disponibles en tant que téléchargement de www.microsoft.com.  
  
 Code source à une version de l'outil de *HttpCfg.exe* est également fourni comme exemple de Windows Server Kit de développement logiciel.  Code source à l'exemple de *HttpCfg.exe* est installé par défaut avec les exemples de mise en réseau dans le Kit de développement logiciel dans le dossier suivant :  
  
 *C:\\Program Files\\Microsoft SDKs\\Windows\\v1.0\\Samples\\NetDS\\http\\serviceconfigP*  
  
 En plus de ces outils, les classes d' <xref:System.Security.Cryptography.X509Certificates.X509Certificate> et d' <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> fournit des méthodes pour charger un certificat dans le système de fichiers.  
  
## Voir aussi  
 [Sécurité dans la programmation réseau](../../../docs/framework/network-programming/security-in-network-programming.md)   
 [Programmation réseau dans le .NET Framework](../../../docs/framework/network-programming/index.md)