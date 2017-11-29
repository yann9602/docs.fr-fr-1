---
title: Authorizing Access to Service Operations
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- service behaviors, authorizing access sample
- Authorizing Access To Service Operations Sample [Windows Communication Foundation]
- authorization, Windows Communication Foundation sample
ms.assetid: ddcfdaa5-8b2e-4e13-bd85-887209dc6328
caps.latest.revision: "23"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: cfa1eefa9f7bd940baf3796d92ac7b49e0f9843e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="authorizing-access-to-service-operations"></a>Authorizing Access to Service Operations
Cet exemple montre comment utiliser le [ \<serviceAuthorization >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) pour permettre l’utilisation de la <xref:System.Security.Permissions.PrincipalPermissionAttribute> attribut pour autoriser l’accès aux opérations de service. Cet exemple est basé sur le [mise en route](../../../../docs/framework/wcf/samples/getting-started-sample.md) exemple. Le service et le client sont configurés à l’aide de la [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md). Le `mode` attribut de la [ \<sécurité >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) a été défini sur `Message` et `clientCredentialType` a été défini sur `Windows`. L'attribut <xref:System.Security.Permissions.PrincipalPermissionAttribute> est appliqué à chaque méthode de service et utilisé afin de restreindre l'accès à chaque opération. L'appelant doit être un administrateur Windows pour pouvoir accéder à chaque opération.  
  
 Dans cet exemple, le client est une application console (.exe) et le service est hébergé par les services IIS (Internet Information Services).  
  
> [!NOTE]
>  La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.  
  
 Le fichier de configuration de service utilise le [ \<serviceAuthorization >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) pour définir le `principalPermissionMode` attribut :  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior>   
      <!-- The serviceAuthorization behavior sets the  
           principalPermissionMode to UseWindowsGroups.  
           This puts a WindowsPrincipal on the current thread when a   
           service is invoked. -->  
      <serviceAuthorization principalPermissionMode="UseWindowsGroups" />  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 Affecter au `principalPermissionMode` la valeur `UseWindowsGroups` permet d'utiliser l'attribut <xref:System.Security.Permissions.PrincipalPermissionAttribute> en fonction des noms de groupe Windows.  
  
 L'attribut <xref:System.Security.Permissions.PrincipalPermissionAttribute> est appliqué à chaque opération, indiquant que l'appelant doit appartenir à un groupe Administrateurs Windows, tel qu'illustré dans l'exemple de code suivant.  
  
```  
[PrincipalPermission(SecurityAction.Demand,   
                             Role = "Builtin\\Administrators")]  
public double Add(double n1, double n2)  
{  
    double result = n1 + n2;  
    return result;  
}  
```  
  
 Lorsque vous exécutez l'exemple, les demandes et réponses d'opération s'affichent dans la fenêtre de console du client. Le client parvient à communiquer avec chaque opération s'il s'exécute sous un compte appartenant à un groupe Administrateurs. Dans le cas contraire, l'accès aux opérations lui sera refusé. Faites l'expérience de ce genre d'échec en exécutant le client sous un compte n'appartenant pas à un groupe Administrateurs. Appuyez sur ENTER dans la fenêtre de console pour arrêter le client.  
  
 Les services peuvent être informés des échecs d'autorisation en implémentant un <xref:System.ServiceModel.Dispatcher.IErrorHandler>. Consultez [extension de contrôle sur la gestion d’erreur et de création de rapports](../../../../docs/framework/wcf/samples/extending-control-over-error-handling-and-reporting.md) pour plus d’informations sur l’implémentation `IErrorHandler`.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple  
  
1.  Assurez-vous d’avoir effectué la [procédure d’installation d’à usage unique pour les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [en cours d’exécution les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
## <a name="see-also"></a>Voir aussi
