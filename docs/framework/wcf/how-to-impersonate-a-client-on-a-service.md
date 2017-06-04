---
title: "Comment&#160;: emprunter l&#39;identit&#233; d&#39;un client sur un service | Microsoft Docs"
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
  - "WCF, emprunt d’identité"
  - "emprunt d'identité"
  - "WCF, sécurité"
ms.assetid: 431db851-a75b-4009-9fe2-247243d810d3
caps.latest.revision: 33
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 33
---
# Comment&#160;: emprunter l&#39;identit&#233; d&#39;un client sur un service
Emprunter l'identité d'un client sur un service [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] permet au service d'exécuter des actions au nom du client. Pour les actions soumises à la vérification de la liste de contrôle d'accès \(ACL\), telles que l'accès aux répertoires et aux fichiers sur un ordinateur ou l'accès à une base de données SQL Server, la vérification de la liste ACL est effectuée en fonction du compte d'utilisateur client. Cette rubrique décrit les étapes de base requises pour permettre à un client dans un domaine Windows de définir un niveau d'emprunt de l'identité du client. Pour obtenir un exemple fonctionnel, consultez [Emprunt de l'identité du client](../../../docs/framework/wcf/samples/impersonating-the-client.md).[!INCLUDE[crabout](../../../includes/crabout-md.md)] l’emprunt d’identité du client, consultez [Délégation et emprunt d'identité](../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md).  
  
> [!NOTE]
>  Lorsque le client et le service s'exécutent sur le même ordinateur et que le client s'exécute sous un compte système \(c'est\-à\-dire `Local System` ou `Network Service`\), il n'est pas possible d'emprunter l'identité du client lorsqu'une session sécurisée est établie avec les jetons de contexte de sécurité avec état. Une application WinForms ou console s'exécute en général sous le compte actuellement connecté, afin que le l'emprunt d'identité du compte puisse être effectué par défaut. Toutefois, lorsque le client est une page [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] et que celle\-ci est hébergée dans [!INCLUDE[iis601](../../../includes/iis601-md.md)] ou IIS 7.0, le client ne s'exécute pas par défaut sous le compte `Network Service`. Toutes les liaisons fournies par le système qui prennent en charge des sessions sécurisées utilisent par défaut un jeton de contexte de sécurité sans état. Toutefois, si le client est une page [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)], et que des sessions sécurisées avec jetons de contexte de sécurité avec état sont utilisées, l'emprunt de l'identité du client est impossible.[!INCLUDE[crabout](../../../includes/crabout-md.md)] l’utilisation de jetons de contexte de sécurité avec état dans une session sécurisée, consultez [Procédure : créer un jeton de contexte de sécurité pour une session sécurisée](../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md).  
  
### Pour activer l'emprunt de l'identité d'un client depuis un jeton Windows mis en cache sur un service  
  
1.  Créez le service. Pour obtenir un didacticiel sur cette procédure de base, consultez [Didacticiel de mise en route](../../../docs/framework/wcf/getting-started-tutorial.md).  
  
2.  Utilisez une liaison qui fait appel à l'authentification Windows et crée une session, telle que <xref:System.ServiceModel.NetTcpBinding> ou <xref:System.ServiceModel.WSHttpBinding>.  
  
3.  Lorsque vous créez l'implémentation de l'interface du service, appliquez la classe <xref:System.ServiceModel.OperationBehaviorAttribute> à la méthode qui requiert l'emprunt de l'identité du client. Affectez à la propriété <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A> la valeur <xref:System.ServiceModel.ImpersonationOption>.  
  
     [!code-csharp[c_SimpleImpersonation#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_simpleimpersonation/cs/source.cs#2)]
     [!code-vb[c_SimpleImpersonation#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_simpleimpersonation/vb/source.vb#2)]  
  
### Pour définir le niveau d'emprunt d'identité autorisé sur le client  
  
1.  Créez le code client du service à l’aide de [Outil Service Model Metadata Tool \(Svcutil.exe\)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).[!INCLUDE[crdefault](../../../includes/crdefault-md.md)] [Accès aux services à l'aide d'un client WCF](../../../docs/framework/wcf/accessing-services-using-a-wcf-client.md).  
  
2.  Après avoir créé le client [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], affectez à la propriété <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> de la classe <xref:System.ServiceModel.Security.WindowsClientCredential> l'une des valeurs d'énumération <xref:System.Security.Principal.TokenImpersonationLevel>.  
  
    > [!NOTE]
    >  Pour utiliser <xref:System.Security.Principal.TokenImpersonationLevel>, l'authentification Kerberos négociée \(parfois appelée Kerberos *multi\-leg* ou *multi\-step*\) doit être utilisée. Pour savoir comment procéder, consultez [Meilleures pratiques pour la sécurité](../../../docs/framework/wcf/feature-details/best-practices-for-security-in-wcf.md).  
  
     [!code-csharp[c_SimpleImpersonation#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_simpleimpersonation/cs/source.cs#1)]
     [!code-vb[c_SimpleImpersonation#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_simpleimpersonation/vb/source.vb#1)]  
  
## Voir aussi  
 <xref:System.ServiceModel.OperationBehaviorAttribute>   
 <xref:System.Security.Principal.TokenImpersonationLevel>   
 [Emprunt de l'identité du client](../../../docs/framework/wcf/samples/impersonating-the-client.md)   
 [Délégation et emprunt d'identité](../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)