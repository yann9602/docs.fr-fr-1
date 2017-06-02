---
title: "Comment&#160;: d&#233;sactiver le chiffrement des signatures num&#233;riques | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fd174313-ad81-4dca-898a-016ccaff8187
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# Comment&#160;: d&#233;sactiver le chiffrement des signatures num&#233;riques
Par défaut, un message est signé et la signature est chiffrée numériquement.  Cette opération est contrôlée en créant une liaison personnalisée à l'aide d'une instance de <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> ou de <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>, et en affectant à la propriété `MessageProtectionOrder` de l'une de ces deux classes une valeur d'énumération <xref:System.ServiceModel.Security.MessageProtectionOrder>.  La valeur par défaut est <xref:System.ServiceModel.Security.MessageProtectionOrder>.  Ce processus consomme jusqu'à 30 pour cent de temps de plus que la simple signature et le chiffrement à partir de la taille de message totale \(plus le message est petit, plus grand est l'impact sur les performances\).  Toutefois, désactiver le chiffrement de la signature présente un risque en matière de sécurité, puisqu'il peut permettre à un intrus de deviner le contenu du message.  En effet, l'élément de la signature contient le code de hachage du texte brut de chaque partie signée du message.  Par exemple, même si le corps des messages est chiffré par défaut, la signature non chiffrée contient le code de hachage du corps des messages avant le chiffrement.  Si le jeu de valeurs possibles pour la partie signée et chiffrée est petit, un intrus peut être en mesure de deviner le contenu en consultant la valeur de hachage.  Le chiffrement de la signature réduit les risques présents dans ce domaine.  
  
 Par conséquent, désactivez uniquement le chiffrement de la signature lorsque la valeur du contenu est basse ou le jeu de valeurs de contenu possible est grand et non déterministe, et le gain de performance est plus important que de réduire les risques d'attaque décrits précédemment.  
  
> [!NOTE]
>  Si le message ne contient aucun élément chiffré, l'élément de signature n'est pas chiffré, même lorsque la propriété <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement.MessageProtectionOrder%2A?displayProperty=fullName> ou <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.MessageProtectionOrder%2A?displayProperty=fullName> a la valeur <xref:System.ServiceModel.Security.MessageProtectionOrder>.  Ce comportement se produit même avec les liaisons fournies par le système ; toutes les liaisons fournies par le système ont l'ordre de protection des messages défini à `SignBeforeEncryptAndEncryptSignature`.  Toutefois, le code WSDL \(Web Services Description Language\) généré par [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] contiendra encore l'assertion `<sp:EncryptSignature>`.  
  
### Pour désactiver la signature numérique  
  
1.  Créer un <xref:System.ServiceModel.Channels.CustomBinding>.  [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [Comment : créer une liaison personnalisée à l'aide de SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).  
  
2.  Ajoutez un élément <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> ou un élément <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> à la collection de liaisons.  
  
3.  Affectez à la propriété <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement.MessageProtectionOrder%2A?displayProperty=fullName> la valeur <xref:System.ServiceModel.Security.MessageProtectionOrder> ou affectez à la propriété <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.MessageProtectionOrder%2A?displayProperty=fullName> la valeur <xref:System.ServiceModel.Security.MessageProtectionOrder>.  
  
## Voir aussi  
 [Fonctionnalités de sécurité avec des liaisons personnalisées](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)