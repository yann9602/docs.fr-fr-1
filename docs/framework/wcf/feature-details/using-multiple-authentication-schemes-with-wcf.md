---
title: "Utilisation de schémas d'authentification multiples avec WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f32a56a0-e2b2-46bf-a302-29e1275917f9
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e570185b7df06a47e8c7fb3319328e760079415d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="using-multiple-authentication-schemes-with-wcf"></a>Utilisation de schémas d'authentification multiples avec WCF
WCF vous permet maintenant de spécifier plusieurs schémas d'authentification sur un seul point de terminaison. En outre les services hébergés sur le Web peuvent hériter leurs paramètres d'authentification directement d'IIS. Les services auto-hébergés peuvent spécifier que les schémas d'authentification peuvent être utilisés. Pour plus d’informations sur la définition des paramètres d’authentification dans IIS, consultez [l’authentification IIS](http://go.microsoft.com/fwlink/?LinkId=232458)  
  
## <a name="iis-hosted-services"></a>Services hébergés IIS  
 Pour les services hébergés dans IIS, définissez les schémas d'authentification que vous souhaitez utiliser dans IIS. Puis dans le fichier web.config de votre service, dans la configuration de liaison spécifiez le type clientCredential en tant que « InheritedFromHost » comme indiqué dans l’extrait XML suivant :  
  
```xml  
<bindings>  
      <basicHttpBinding>  
        <binding name="secureBinding">  
          <security mode="Transport">  
            <transport clientCredentialType="InheritedFromHost" />  
          </security>  
        </binding>  
      </basicHttpBinding>  
    </bindings>  
```  
  
 Vous pouvez spécifier que vous voulez uniquement un sous-ensemble des schémas d’authentification à utiliser avec votre service à l’aide de ServiceAuthenticationBehavior ou \<serviceAuthenticationManager > élément. Lors de la configuration dans le code, utilisez ServiceAuthenticationBehavior comme indiqué dans l'extrait de code suivant.  
  
```csharp  
// ...  
ServiceAuthenticationBehavior sab = null;  
sab = serviceHost.Description.Behaviors.Find<ServiceAuthenticationBehavior>();  
  
if (sab == null)  
{  
    sab = new ServiceAuthenticationBehavior();  
    sab.AuthenticationSchemes = AuthenticationSchemes.Basic | AuthenticationSchemes.Negotiate | AuthenticationSchemes.Digest;  
    serviceHost.Description.Behaviors.Add(sab);  
}  
else  
{  
     sab.AuthenticationSchemes = AuthenticationSchemes.Basic | AuthenticationSchemes.Negotiate | AuthenticationSchemes.Digest;  
}  
// ...  
```  
  
 Lors de la configuration dans un fichier de configuration, utilisez le \<serviceAuthenticationManager > comme illustré dans l’extrait de code XML suivant.  
  
```xml  
<behaviors>  
      <serviceBehaviors>  
        <behavior name="limitedAuthBehavior">  
          <serviceAuthenticationManager authenticationSchemes="Negotiate, Digest, Basic"/>  
          <!-- ... -->  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
```  
  
 De cette façon, seul un sous-ensemble des schémas d'authentification répertoriés ici est pris en compte pour l'application sur le point de terminaison de service, selon ce qui est sélectionné dans IIS. Cela signifie qu'un développeur peut exclure l'authentification de base de la liste en l'omettant dans la liste serviceAuthenticationManager, et même si elle est activée dans IIS, elle ne sera pas appliquée sur le point de terminaison de service  
  
## <a name="self-hosted-services"></a>Services auto-hébergés  
 Les services auto-hébergés sont configurés un peu différemment étant donné l'absence d'IIS pour hériter des paramètres. Ici, vous utilisez le \<serviceAuthenticationManager > élément ou ServiceAuthenticationBehavior pour spécifier les paramètres d’authentification qui sont hérités. Le code présente l'aspect suivant :  
  
```csharp  
// ...  
ServiceAuthenticationBehavior sab = null;  
sab = serviceHost.Description.Behaviors.Find<ServiceAuthenticationBehavior>();  
  
if (sab == null)  
{  
    sab = new ServiceAuthenticationBehavior();  
    sab.AuthenticationSchemes = AuthenticationSchemes.Basic | AuthenticationSchemes.Negotiate | AuthenticationSchemes.Digest;  
    serviceHost.Description.Behaviors.Add(sab);  
}  
else  
{  
     sab.AuthenticationSchemes = AuthenticationSchemes.Basic | AuthenticationSchemes.Negotiate | AuthenticationSchemes.Digest;  
}  
// ...  
```  
  
 La configuration présente l'aspect suivant :  
  
```xml  
<behaviors>  
      <serviceBehaviors>  
        <behavior name="limitedAuthBehavior">  
          <serviceAuthenticationManager authenticationSchemes="Negotiate, Digest, Basic"/>  
          <!-- ... -->  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
```  
  
 Et vous pouvez ensuite spécifier InheritFromHost dans vos paramètres de liaison comme indiqué dans l'extrait de code XML suivant.  
  
```xml  
<bindings>  
      <basicHttpBinding>  
        <binding name="secureBinding">  
          <security mode="Transport">  
            <transport clientCredentialType="InheritedFromHost" />  
          </security>  
        </binding>  
      </basicHttpBinding>  
    </bindings>  
```  
  
 Sinon, vous pouvez spécifier les schémas d’authentification dans la liaison personnalisée, en définissant les schémas d’authentification sur l’élément de liaison de transport HTTP, comme indiqué dans l’extrait de code de configuration suivant.  
  
```xml  
<binding name="multipleBinding">  
      <textMessageEncoding/>  
      <httpTransport authenticationScheme="Negotiate, Ntlm, Digest, Basic" />  
    </binding>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Liaisons et sécurité](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)  
 [Points de terminaison : adresses, liaisons et contrats](../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)  
 [Configuration des liaisons fournies par le système](../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Fonctionnalités de sécurité avec des liaisons personnalisées](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
 [Liaisons](../../../../docs/framework/wcf/feature-details/bindings.md)  
 [Liaisons](../../../../docs/framework/wcf/feature-details/bindings.md)  
 [Liaisons personnalisées](../../../../docs/framework/wcf/extending/custom-bindings.md)
