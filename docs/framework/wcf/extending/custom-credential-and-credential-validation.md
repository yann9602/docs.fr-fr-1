---
title: "Informations d&#39;identification personnalis&#233;es et validation d&#39;informations d&#39;identification | Microsoft Docs"
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
  - "validation d'informations d'identification (WCF)"
  - "informations d'identification (WCF)"
  - "informations d'identification (WCF), personnalisé"
  - "informations d'identification (WCF), validation"
  - "informations d'identification personnalisées (WCF)"
ms.assetid: da831bec-e281-4d44-b343-437b5eef688e
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# Informations d&#39;identification personnalis&#233;es et validation d&#39;informations d&#39;identification
La sécurité dans [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] est basée sur l'échange d'informations d'identification entre les services et les clients.  La plupart des besoins en matière de sécurité peuvent être satisfaits à l'aide de types d'informations d'identification communs, tels que Windows \(Kerberos\), le nom d'utilisateur et les mots de passe et les certificats.  Toutefois, si un nouveau type d'informations d'identification est requis, les rubriques de cette section expliquent comment gérer et valider des types nouveaux.  
  
## Dans cette section  
 [Comment : créer un service qui utilise un validateur de certificat personnalisé](../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)  
 Explique comment personnaliser la validation [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] en héritant de la classe <xref:System.IdentityModel.Selectors.X509CertificateValidator>.  
  
 [Procédure pas à pas : création d'informations d'identification de client et de service personnalisées](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md)  
 Montre comment étendre les classes <xref:System.ServiceModel.Description.ClientCredentials> et <xref:System.ServiceModel.Description.ServiceCredentials> pour prendre en charge de nouveaux types d'informations d'identification.  Il s'agit du premier volet d'une série de rubriques qui permettent de créer des types d'informations d'identification personnalisés.  
  
 [Comment : créer un fournisseur de jetons de sécurité personnalisé](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-provider.md)  
 Explique comment créer un fournisseur de jetons de sécurité pour gérer de nouveaux types d'informations d'identification et retourner de nouveaux jetons pour les informations d'authentification.  Il s'agit de la deuxième rubrique de la série.  
  
 [Comment : créer un authentificateur de jetons de sécurité personnalisé](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-authenticator.md)  
 Explique comment créer un authentificateur personnalisé pour authentifier un nouveau type d'informations d'identification.  Il s'agit de la troisième rubrique de la série.  
  
## Référence  
 <xref:System.ServiceModel.Security>  
  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.IdentityModel.Policy>  
  
 <xref:System.IdentityModel.Tokens>  
  
 <xref:System.IdentityModel.Selectors>  
  
 <xref:System.IdentityModel.Selectors.X509CertificateValidator>  
  
 <xref:System.ServiceModel.Description.ClientCredentials>  
  
 <xref:System.ServiceModel.Description.ServiceCredentials>  
  
## Rubriques connexes  
 [Authentification](../../../../docs/framework/wcf/feature-details/authentication-in-wcf.md)  
  
 [Fédération et jetons émis](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
  
 [Autorisation](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)  
  
## Voir aussi  
 [Sécurité](../../../../docs/framework/wcf/feature-details/security.md)