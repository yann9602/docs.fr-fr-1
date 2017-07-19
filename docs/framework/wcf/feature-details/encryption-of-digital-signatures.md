---
title: "Chiffrement de signatures num&#233;riques | Microsoft Docs"
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
  - "signatures numériques (WCF)"
  - "signatures numériques (WCF), chiffrement"
  - "chiffrement de signatures numériques (WCF)"
ms.assetid: 0868866d-40b4-4341-8e42-eee3b7f15b69
caps.latest.revision: 9
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 9
---
# Chiffrement de signatures num&#233;riques
Par défaut, un message est signé et chiffré et sa signature chiffrée numériquement.Vous pouvez contrôler ce paramètre en créant une liaison personnalisée à l'aide d'une instance de <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> ou de <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>, puis en affectant à la propriété `MessageProtectionOrder` de l'une de ces deux classes une valeur d'énumération <xref:System.ServiceModel.Security.MessageProtectionOrder>.La valeur par défaut est <xref:System.ServiceModel.Security.MessageProtectionOrder>.Ce processus nécessite 10 à 40 pour cent plus de temps que lorsque les messages sont seulement signés et chiffrés.Toutefois, désactiver le chiffrement de la signature présente un risque en matière de sécurité, les intrus pouvant deviner en son absence le contenu des messages.La signature contient en effet le code de hachage du texte brut de chaque partie signée des messages.Par exemple, même si le corps des messages est chiffré par défaut, la signature non chiffrée contient le code de hachage du corps des messages.Si le message est petit, un intrus risque de parvenir à déduire son contenu.Le chiffrement de la signature limite ou élimine complètement ce risque.  
  
 En conclusion, désactivez uniquement le chiffrement de la signature lorsque les messages ne contiennent pas d'informations à caractère sensible et lorsque cela peut permettre une amélioration significative des performances, par exemple lorsque vous envoyez des fichiers binaires de grande taille ne nécessitant pas de protection particulière.  
  
### Pour désactiver la signature numérique  
  
1.  Créez une liaison <xref:System.ServiceModel.Channels.CustomBinding>.[!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Comment : créer une liaison personnalisée à l'aide de SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).  
  
2.  Ajoutez un élément <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> ou un élément <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> à la collection de liaisons.  
  
3.  Affectez à la propriété <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement.MessageProtectionOrder%2A?displayProperty=fullName> la valeur <xref:System.ServiceModel.Security.MessageProtectionOrder> ou affectez à la propriété <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.MessageProtectionOrder%2A?displayProperty=fullName> la valeur <xref:System.ServiceModel.Security.MessageProtectionOrder>.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)] la création de liaisons personnalisées, consultez [Création de liaisons définies par l'utilisateur](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md).[!INCLUDE[crabout](../../../../includes/crabout-md.md)] la création d'une liaison personnalisée pour un mode d'authentification donné, consultez [Comment : créer un SecurityBindingElement pour un mode d'authentification spécifié](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md).  
  
## Voir aussi  
 <xref:System.ServiceModel.Security.MessageProtectionOrder>   
 <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>   
 <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>   
 [Comment : créer une liaison personnalisée à l'aide de SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)   
 [Création de liaisons définies par l'utilisateur](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md)   
 [Comment : créer un SecurityBindingElement pour un mode d'authentification spécifié](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)