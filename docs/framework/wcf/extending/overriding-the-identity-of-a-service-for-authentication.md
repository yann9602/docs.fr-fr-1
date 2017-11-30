---
title: "Substitution de l'identité d'un service pour l'authentification"
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
ms.assetid: d613a22b-07d7-41a4-bada-1adc653b9b5d
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6a3125504326f2cb129fef6f1f3e01dba577f599
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="overriding-the-identity-of-a-service-for-authentication"></a>Substitution de l'identité d'un service pour l'authentification
Généralement, vous n'avez pas besoin de définir l'identité sur un service car la sélection d'un type d'informations d'identification du client impose le type d'identité exposé dans les métadonnées du service. Par exemple, le code de configuration suivant utilise le [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) et affecte le `clientCredentialType` à Windows d’attribut.  
  
  
  
 Le fragment WSDL (Web Services Description Language) suivant affiche l'identité du point de terminaison défini précédemment. Dans cet exemple, le service s’exécute comme un service auto-hébergé sous un compte d’utilisateur particulier (username@contoso.com) et par conséquent, l’identité d’utilisateur principaux (UPN) contient le nom du compte. L'UPN est également appelé nom de connexion d'utilisateur dans un domaine Windows.  
  
  
  
 Pour un exemple d’application qui illustre la définition de l’identité, consultez [exemple](../../../../docs/framework/wcf/samples/service-identity-sample.md). [!INCLUDE[crabout](../../../../includes/crabout-md.md)]identité de service, consultez [l’identité du Service et l’authentification](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).  
  
## <a name="kerberos-authentication-and-identity"></a>Authentification et identité Kerberos  
 Par défaut, lorsqu’un service est configuré pour utiliser les informations d’identification Windows, un [ \<identité >](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md) élément contenant un [ \<userPrincipalName >](../../../../docs/framework/configure-apps/file-schema/wcf/userprincipalname.md) ou [ \<servicePrincipalName >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceprincipalname.md) élément est généré dans le WSDL. Si le service s’exécute sous le `LocalSystem`, `LocalService`, ou `NetworkService` compte, un service de nom principal (SPN) est généré par défaut sous la forme de `host/` \< *nom d’hôte*>, car ces comptes ont accès aux données SPN de l’ordinateur. Si le service s’exécute sous un compte différent, [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] génère un UPN sous la forme de \< *nom d’utilisateur*>@<*domainName*`>`. Cela est dû au fait que l'authentification Kerberos requiert qu'un UPN ou SPN soit fourni au client pour authentifier le service.  
  
 Vous pouvez également utiliser l'outil Setspn.exe pour inscrire un SPN supplémentaire avec un compte de service dans un domaine. Vous pouvez ensuite utiliser le SPN comme identité du service. Pour télécharger l’outil, consultez [Windows 2000 Resource Kit Tool : Setspn.exe](http://go.microsoft.com/fwlink/?LinkId=91752). [!INCLUDE[crabout](../../../../includes/crabout-md.md)]l’outil, consultez [présentation de Setspn](http://go.microsoft.com/fwlink/?LinkId=61374).  
  
> [!NOTE]
>  Pour utiliser le type d'informations d'identification Windows sans négociation, le compte d'utilisateur du service doit avoir accès au SPN inscrit avec le domaine Active Directory. Pour ce faire, vous pouvez procéder de différentes façons :  
  
-   Utilisez le compte NetworkService ou LocalSystem pour exécuter votre service. Comme ces comptes ont accès au SPN de l'ordinateur établi lorsque l'ordinateur rejoint le domaine Active Directory, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] génère automatiquement l'élément SPN approprié à l'intérieur du point de terminaison du service dans les métadonnées du service (WSDL).  
  
-   Utilisez un compte de domaine Active Directory arbitraire pour exécuter votre service. Dans ce cas, établissez un SPN pour ce compte de domaine, pour cela vous pouvez vous servir de l'utilitaire Setspn.exe. Une fois que le SPN du compte du service a été créé, configurez [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] pour publier ce SPN sur les clients du service par le biais de ses métadonnées (WSDL). Pour cela, il suffit de définir l'identité du point de terminaison exposé, à l'aide d'un fichier de configuration d'application ou du code.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Noms principaux de service, le protocole Kerberos et Active Directory, voir [Kerberos supplément technique pour Windows](http://go.microsoft.com/fwlink/?LinkId=88330).  
  
### <a name="when-spn-or-upn-equals-the-empty-string"></a>Lorsque SPN ou UPN équivaut à une chaîne vide  
 Si vous attribuez une valeur de chaîne vide à SPN ou UPN, plusieurs choses se produisent, en fonction du niveau de sécurité et du mode d'authentification utilisés :  
  
-   Si vous utilisez la sécurité de niveau transport, l'authentification NTLM (NT LanMan) est choisie.  
  
-   Si vous utilisez la sécurité de niveau message, l'authentification peut échouer, en fonction du mode d'authentification.  
  
-   Si vous utilisez le mode `spnego` et que l'attribut `AllowNtlm` a la valeur `false`, l'authentification échoue.  
  
-   Si vous utilisez le mode `spnego` et que l'attribut `AllowNtlm` a la valeur `true`, l'authentification échoue si l'UPN est vide, mais réussit si le SPN est vide.  
  
-   Si vous utilisez Kerberos direct (également appelé « one-shot »), l'authentification échoue.  
  
### <a name="using-the-identity-element-in-configuration"></a>À l’aide de la \<identité > élément de Configuration  
 Si vous remplacez le type d'informations d'identification du client dans la liaison présentée précédemment par Certificate`,` le fichier WSDL généré contient alors un certificat X.509 sérialisé pour la valeur d'identité, comme illustré dans le code suivant. Il s'agit de la valeur par défaut pour tous les types d'informations d'identification du client autres que Windows.  
  
  
  
 Vous pouvez modifier la valeur de l'identité de service par défaut ou le type de l'identité à l'aide de l'élément <`identity`> dans la configuration ou en définissant l'identité dans le code. Le code de configuration suivant affecte à une identité DNS (Domain Name System) la valeur `contoso.com`.  
  
  
  
### <a name="setting-identity-programmatically"></a>Définition de l'identité par programme  
 Votre service n'a pas besoin de spécifier une identité de manière explicite, car [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] la détermine automatiquement. Toutefois, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] vous permet de spécifier une identité sur un point de terminaison, le cas échéant. Le code suivant ajoute un point de terminaison de service avec une identité DNS spécifique.  
  
 [!code-csharp[C_Identity#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_identity/cs/source.cs#5)]
 [!code-vb[C_Identity#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_identity/vb/source.vb#5)]  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : créer un vérificateur d’identité Client personnalisés](../../../../docs/framework/wcf/extending/how-to-create-a-custom-client-identity-verifier.md)  
 [L’authentification et identité de Service](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
