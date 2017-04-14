---
title: "Diff&#233;rences de validation des certificats entre HTTPS, SSL sur TCP et la s&#233;curit&#233; SOAP | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "certificats (WCF), validation (différences de)"
ms.assetid: 953a219f-4745-4019-9894-c70704f352e6
caps.latest.revision: 14
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 14
---
# Diff&#233;rences de validation des certificats entre HTTPS, SSL sur TCP et la s&#233;curit&#233; SOAP
Vous pouvez utiliser des certificats dans [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] avec la sécurité de couche de message \(SOAP\) en plus de la sécurité de couche de transport \(TLS\) sur HTTP \(HTTPS\) ou TCP.Cette rubrique décrit les différences dans la façon dont ces certificats sont validés.  
  
## Validation des certificats clients HTTPS  
 Lors de l'utilisation du protocole HTTPS pour communiquer entre un client et un service, le certificat que le client utilise pour s'authentifier auprès du service doit prendre en charge l'approbation de chaîne.Autrement dit, il doit être chaîné à une autorité de certification racine approuvée.Dans le cas contraire, la couche HTTP lève une exception <xref:System.Net.WebException> avec le message "Le serveur distant a retourné une erreur : \(403\) Interdit". [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] revêt cette exception en tant que <xref:System.ServiceModel.Security.MessageSecurityException>.  
  
## Validation des certificats de service HTTPS  
 Lors de l'utilisation du protocole HTTPS pour communiquer entre un client et un service, le certificat avec lequel le serveur effectue l'authentification doit prendre en charge l'approbation de chaîne par défaut.Autrement dit, il doit être chaîné à une autorité de certification racine approuvée.Aucun contrôle en ligne n'est effectué pour voir si le certificat a été révoqué.Vous pouvez compenser ce comportement en enregistrant un rappel <xref:System.Net.Security.RemoteCertificateValidationCallback>, comme illustré dans le code ci\-dessous.  
  
 [!code-csharp[c_CertificateValidationDifferences#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_certificatevalidationdifferences/cs/source.cs#1)]
 [!code-vb[c_CertificateValidationDifferences#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_certificatevalidationdifferences/vb/source.vb#1)]  
  
 où la signature pour `ValidateServerCertificate` est comme suit :  
  
 [!code-csharp[c_CertificateValidationDifferences#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_certificatevalidationdifferences/cs/source.cs#2)]
 [!code-vb[c_CertificateValidationDifferences#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_certificatevalidationdifferences/vb/source.vb#2)]  
  
 L'implémentation de `ValidateServerCertificate` peut effectuer toutes les vérifications que le développeur d'une application cliente juge nécessaires pour valider le certificat de service.  
  
## Validation de certificats clients dans SSL sur TCP ou la sécurité SOAP  
 Lors de l'utilisation du protocole SSL \(Secure Sockets Layer\) sur TCP ou de la sécurité \(SOAP\) de message, les certificats clients sont validés en fonction de la valeur de propriété <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.CertificateValidationMode%2A> de la classe <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication>.La propriété a l'une des valeurs <xref:System.ServiceModel.Security.X509CertificateValidationMode>.La vérification de la révocation est effectuée en fonction des valeurs de la valeur de propriété <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.RevocationMode%2A> de la classe <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication>.La propriété a l'une des valeurs <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.  
  
 [!code-csharp[c_CertificateValidationDifferences#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_certificatevalidationdifferences/cs/source.cs#3)]
 [!code-vb[c_CertificateValidationDifferences#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_certificatevalidationdifferences/vb/source.vb#3)]  
  
## Validation d'un certificat de service dans SSL sur TCP et la sécurité SOAP  
 Lors de l'utilisation du protocole SSL sur TCP ou de la sécurité de message \(SOAP\), les certificats de service sont validés en fonction de la valeur de propriété <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> de la classe <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication>.La propriété a l'une des valeurs <xref:System.ServiceModel.Security.X509CertificateValidationMode>.  
  
 La vérification de la révocation est effectuée en fonction des valeurs de la valeur de propriété <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.RevocationMode%2A> de la classe <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication>.La propriété a l'une des valeurs <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.  
  
 [!code-csharp[c_CertificateValidationDifferences#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_certificatevalidationdifferences/cs/source.cs#4)]
 [!code-vb[c_CertificateValidationDifferences#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_certificatevalidationdifferences/vb/source.vb#4)]  
  
## Voir aussi  
 <xref:System.Net.Security.RemoteCertificateValidationCallback>   
 [Utilisation des certificats](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)