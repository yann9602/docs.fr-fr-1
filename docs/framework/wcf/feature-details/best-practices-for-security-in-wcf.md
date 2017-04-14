---
title: "Meilleures pratiques pour la s&#233;curit&#233; dans WCF | Microsoft Docs"
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
  - "meilleures pratiques (WCF), sécurité"
ms.assetid: 3639de41-1fa7-4875-a1d7-f393e4c8bd69
caps.latest.revision: 19
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 19
---
# Meilleures pratiques pour la s&#233;curit&#233; dans WCF
Les sections suivantes répertorient les meilleures pratiques à considérer lors de la création d'applications sécurisées à l'aide de la sécurité [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].[!INCLUDE[crabout](../../../../includes/crabout-md.md)] la sécurité, consultez [Considérations relatives à la sécurité](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md), [Considérations sur la sécurité des données](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md), et [Considérations sur la sécurité des métadonnées](../../../../docs/framework/wcf/feature-details/security-considerations-with-metadata.md).  
  
## Identifier les services d'authentification Windows avec les SPN  
 Les services peuvent être identifiés avec les noms d'utilisateur principaux \(UPN\) ou les noms de principaux du service \(SPN\).Les services qui s'exécutent sous des comptes d'ordinateur, tels que les services réseau, ont une identité SPN qui correspond à l'ordinateur en question.Les services qui s'exécutent sous des comptes d'utilisateur ont une identité UPN qui correspond à l'utilisateur en question, bien que l'outil `setspn` puisse être utilisé pour assigner un SPN au compte d'utilisateur.La configuration d'un service de sorte qu'il puisse être identifié par son SPN et la configuration des clients qui se connectent au service pour utiliser ce SPN peuvent compliquer certaines attaques.Cette recommandation s'applique aux liaisons utilisant la négociation SSPI ou Kerberos.Les clients doivent toujours spécifier un SPN dans le cas où SSPI revient à NTLM.  
  
## Vérifier les identités des services dans WSDL  
 WS\-SecurityPolicy permet aux services de publier des informations concernant leurs propres identités dans les métadonnées.En cas d'extraction via `svcutil` ou d'autres méthodes telles que <xref:System.ServiceModel.Description.WsdlImporter>, ces informations d'identité sont converties en les propriétés d'identité des adresses du point de terminaison de service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].Les clients qui ne vérifient pas l'exactitude et la validité de ces identités de service contournent efficacement l'authentification des services.Un service malveillant peut exploiter ces clients pour transférer des informations d'identification et exécuter d'autres attaques « de l'intercepteur » en modifiant l'identité prétendue dans son WSDL.  
  
## Utiliser des certificats X509 au lieu de NTLM  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] offre deux mécanismes d'authentification de réseau pair à pair : les certificats X509 \(utilisés par le canal homologue\) et l'authentification Windows où une négociation SSPI passe de Kerberos à NTLM.L'authentification basée sur des certificats utilisant des tailles de clé de 1 024 bits ou plus est préférée à NTLM pour plusieurs raisons :  
  
-   la disponibilité de l'authentification mutuelle ;  
  
-   l'utilisation d'algorithmes de chiffrement plus robustes ;  
  
-   la plus grande complexité liée à l'utilisation des informations d'identification X509 transférées.  
  
 Pour une vue d'ensemble des attaques de transfert NTLM, allez à la page [http:\/\/msdn.microsoft.com\/msdnmag\/issues\/06\/09\/SecureByDesign\/default.aspx](http://go.microsoft.com/fwlink/?LinkId=109571).  
  
## Toujours rétablir après l'emprunt d'identité  
 Lorsque vous utilisez des API qui activent l'emprunt d'identité d'un client, veillez à rétablir l'identité d'origine.Par exemple, lorsque vous utilisez le <xref:System.Security.Principal.WindowsIdentity> et <xref:System.Security.Principal.WindowsImpersonationContext>, utilisez l'instruction `using` C\# ou l'instruction `Using`[!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)], comme indiqué dans le code suivant.La classe <xref:System.Security.Principal.WindowsImpersonationContext> implémente l'interface <xref:System.IDisposable>, et par conséquent, le common language runtime \(CLR\) rétablit automatiquement l'identité d'origine dès que le code quitte le bloc `using`.  
  
 [!code-csharp[c_SecurityBestPractices#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securitybestpractices/cs/source.cs#1)]
 [!code-vb[c_SecurityBestPractices#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securitybestpractices/vb/source.vb#1)]  
  
## Personnifier uniquement si nécessaire  
 À l'aide de la méthode <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A> de la classe <xref:System.Security.Principal.WindowsIdentity>, il est possible d'utiliser l'emprunt d'identité dans une étendue très contrôlée.Cette approche s'oppose à l'utilisation de la propriété <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A> du <xref:System.ServiceModel.OperationBehaviorAttribute> qui autorise l'emprunt d'identité pour l'étendue de l'opération entière.Si possible, contrôlez l'étendue de l'emprunt d'identité en utilisant la méthode <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A> plus précise.  
  
## Obtenir des métadonnées de sources fiables  
 Soyez sûr de la source de vos métadonnées et vérifiez qu'elles n'ont pas été falsifiées.Les métadonnées récupérées à l'aide du protocole HTTP sont envoyées en texte clair et peuvent être falsifiées.Si le service utilise les propriétés <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> et <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A>, utilisez l'URL que le créateur du service vous a fournie pour télécharger les données à l'aide du protocole HTTPS.  
  
## Publier des métadonnées à l'aide de la sécurité  
 Pour empêcher la falsification des métadonnées publiées d'un service, sécurisez le point de terminaison d'échange de métadonnées avec la sécurité de transport ou au niveau du message.[!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Publication de points de terminaison de métadonnées](../../../../docs/framework/wcf/publishing-metadata-endpoints.md) et [Comment : publier les métadonnées d'un service à l'aide de code](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md).  
  
## Utiliser un émetteur local  
 Si une liaison et une adresse d'émetteur sont spécifiées pour une liaison donnée, l'émetteur local n'est pas utilisé pour les points de terminaison qui utilisent cette liaison.Les clients qui prévoient d'utiliser systématiquement l'émetteur local doivent s'assurer de ne pas utiliser de liaison de ce type ou de modifier la liaison afin que l'adresse de l'émetteur ait la valeur null.  
  
## Quotas de taille de jeton SAML  
 Lorsque les jetons SAML \(Security Assertions Markup Language\) sont sérialisés dans des messages, soit lorsqu'ils sont délivrés par un service de jeton de sécurité \(STS\), soit lorsque les clients les présentent à des services dans le cadre de l'authentification, le quota de taille maximale de message doit être suffisamment grand pour accommoder le jeton SAML et les autres parties de message.Dans un cas normal, les quotas de taille de message par défaut sont suffisants.Toutefois, dans les cas où un jeton SAML est grand parce qu'il contient des centaines de revendications, les quotas doivent être augmentés pour accommoder le jeton sérialisé.[!INCLUDE[crabout](../../../../includes/crabout-md.md)] les quotas, consultez [Considérations sur la sécurité des données](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md).  
  
## Affectation de la valeur True à SecurityBindingElement.IncludeTimestamp sur des liaisons personnalisées  
 Lorsque vous créez une liaison personnalisée, vous devez affecter la valeur `true` à <xref:System.ServiceModel.Channels.SecurityBindingElement.IncludeTimestamp%2A>.Sinon, si <xref:System.ServiceModel.Channels.SecurityBindingElement.IncludeTimestamp%2A> a la valeur `false` et que le client utilise un jeton basé sur une clé asymétrique comme un certificat X509, le message ne sera pas signé.  
  
## Voir aussi  
 [Considérations relatives à la sécurité](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md)   
 [Considérations sur la sécurité des données](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md)   
 [Considérations sur la sécurité des métadonnées](../../../../docs/framework/wcf/feature-details/security-considerations-with-metadata.md)