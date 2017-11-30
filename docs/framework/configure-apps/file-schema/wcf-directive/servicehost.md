---
title: '@ServiceHost'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 96ba6967-00f2-422f-9aa7-15de4d33ebf3
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ed64a90131fcd8f2d9f2120c03db4a21d8dc6efe
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="servicehost"></a>@ServiceHost
Associe la fabrique utilisée pour générer l'hôte de service au service à héberger ainsi qu'à d'autres aspects de programmation requis pour compiler le code d'hébergement fourni dans le fichier .svc ou pour y accéder.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<% @ServiceHost   
Service = "Service, ServiceNamespace"   
Factory = "Factory, FactoryNamespace"  
Debug = "Debug"  
Language = "Language"   
CodeBehind = "CodeBehind"%>  
```  
  
## <a name="attributes"></a>Attributs  
  
#### <a name="service"></a>Service  
 Nom de type CLR du service hébergé. Il doit s'agir d'un nom qualifié correspondant à un type qui implémente un ou plusieurs contacts du service.  
  
#### <a name="factory"></a>Fabrique  
 Nom de type CLR correspondant à la fabrique de l'hôte de service utilisée pour instancier l'hôte de service. Cet attribut est facultatif. S'il n'est pas spécifié, le <xref:System.ServiceModel.Activation.ServiceHostFactory> par défaut est utilisé et renvoie une instance de <xref:System.ServiceModel.ServiceHost>.  
  
#### <a name="debug"></a>Déboguer  
 Indique si le service [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] doit être compilé avec les symboles de débogage. `true` si le service [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] doit être compilé avec les symboles de débogage ; sinon, `false`.  
  
#### <a name="language"></a>Langage  
 Spécifie le langage utilisé lors de la compilation de l'intégralité du code incorporé dans le fichier (.svc). Ces valeurs peuvent représenter tout langage pris en charge par .NET, notamment C#, VB et JS, qui font respectivement référence à C#, Visual Basic .NET et JScript .NET. Cet attribut est facultatif.  
  
#### <a name="codebehind"></a>CodeBehind  
 Spécifie le fichier source qui implémente le service web XML, lorsque la classe implémentant le service web XML ne réside pas dans le même fichier et n’a pas été compilée dans un assembly et placée dans le répertoire \Bin.  
  
## <a name="remarks"></a>Remarques  
 Le <xref:System.ServiceModel.ServiceHost> utilisé pour héberger le service est un point d'extensibilité figurant dans le modèle de programmation [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]. Un modèle de fabrique est utilisé pour instancier le <xref:System.ServiceModel.ServiceHost> car il peut s'agir d'un type polymorphe ne devant pas être instancié directement par l'environnement d'hébergement.  
  
 L'implémentation par défaut utilise <xref:System.ServiceModel.Activation.ServiceHostFactory> pour créer une instance de <xref:System.ServiceModel.ServiceHost>. Mais vous pouvez fournir votre propre fabrique (celle qui retourne votre hôte dérivé) en spécifiant le nom de type CLR de l’implémentation de fabrique dans la [ @ServiceHost ](../../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) la directive.  
  
 Pour utiliser fabrique hôte de service personnalisé propre au lieu de la fabrique par défaut, simplement fournir le nom de type dans le [ @ServiceHost ](../../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive comme suit :  
  
```xml  
<% @ServiceHost Factory="DerivedFactory" Service="MyService" %>  
```  
  
 Surchargez les implémentations de fabrique le moins possible. Si vous disposez d'une importante logique personnalisée, votre code est plus facilement réutilisable si vous intégrez cette logique à votre hôte et non à la fabrique.  
  
 Par exemple, pour activer un point de terminaison compatible AJAX pour `MyService`, spécifiez la <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> pour la valeur de la `Factory` attribut, au lieu de la valeur par défaut <xref:System.ServiceModel.Activation.ServiceHostFactory>, dans le [ @ServiceHost ](../../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive en tant que indiqué dans l’exemple suivant.  
  
## <a name="example"></a>Exemple  
  
```  
<% @ServiceHost   
Service="MyService"  
Language="C#"  
Debug="true"  
Factory="WebScriptServiceHostFactory"  
%>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Hôte de Service personnalisé](../../../../../docs/framework/wcf/samples/custom-service-host.md)
