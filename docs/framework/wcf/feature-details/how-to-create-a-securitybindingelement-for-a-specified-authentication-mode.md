---
title: "Comment : créer un SecurityBindingElement pour un mode d'authentification spécifié"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: a7c7747a-5b8c-463f-8493-7266dac75066
caps.latest.revision: "9"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 29cbe3c10ac68d508dc22781e46a6041f2d7eab7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-securitybindingelement-for-a-specified-authentication-mode"></a>Comment : créer un SecurityBindingElement pour un mode d'authentification spécifié
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] fournit plusieurs modes par lesquels les clients et services s'authentifient les uns les autres. Vous pouvez créer des éléments de liaison de sécurité pour ces modes d'authentification en utilisant des méthodes statiques sur la classe <xref:System.ServiceModel.Channels.SecurityBindingElement> ou par la configuration, comme indiqué dans l'exemple suivant.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]les modes de 18 authentification, consultez [Modes d’authentification SecurityBindingElement](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md).  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant présente des méthodes pour créer des liaisons pour les divers modes d’authentification.  
  
> [!NOTE]
>  Une fois qu'une instance de l'objet <xref:System.ServiceModel.Channels.SecurityBindingElement> est créée, plusieurs propriétés sont immuables, telles que <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.KeyType%2A> et <xref:System.ServiceModel.Channels.SecurityBindingElement.MessageSecurityVersion%2A>. L'appel de `set` sur de telles propriétés ne les modifie pas.  
  
 [!code-csharp[c_CustomBindingsAuthMode#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombindingsauthmode/cs/source.cs#2)]
 [!code-vb[c_CustomBindingsAuthMode#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_custombindingsauthmode/vb/source.vb#2)]  
  
## <a name="see-also"></a>Voir aussi  
 [Modes d’authentification SecurityBindingElement](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md)  
 [Guide pratique pour créer une liaison personnalisée à l’aide de SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
