---
title: "@ServiceHost | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 96ba6967-00f2-422f-9aa7-15de4d33ebf3
caps.latest.revision: 9
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 9
---
# @ServiceHost
Associe la fabrique utilisée pour générer l'hôte de service au service à héberger ainsi qu'à d'autres aspects de programmation requis pour compiler le code d'hébergement fourni dans le fichier .svc ou pour y accéder.  
  
## Syntaxe  
  
```  
  
<% @ServiceHost   
Service = "Service, ServiceNamespace"   
Factory = "Factory, FactoryNamespace"  
Debug = "Debug"  
Language = "Language"   
CodeBehind = "CodeBehind"%>  
```  
  
## Attributs  
  
#### Service  
 Nom de type CLR du service hébergé.  Il doit s'agir d'un nom qualifié correspondant à un type qui implémente un ou plusieurs contacts du service.  
  
#### Fabrique  
 Nom de type CLR correspondant à la fabrique de l'hôte de service utilisée pour instancier l'hôte de service.  Cet attribut est facultatif.  S'il n'est pas spécifié, le <xref:System.ServiceModel.Activation.ServiceHostFactory> par défaut est utilisé et renvoie une instance de <xref:System.ServiceModel.ServiceHost>.  
  
#### Déboguer  
 Indique si le service [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] doit être compilé avec les symboles de débogage.  `true` si le service [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] doit être compilé avec les symboles de débogage ; sinon, `false`.  
  
#### Langage  
 Spécifie le langage utilisé lors de la compilation de l'intégralité du code incorporé dans le fichier \(.svc\).  Ces valeurs peuvent représenter tout langage pris en charge par .NET, notamment C\#, VB et JS, qui font respectivement référence à C\#, Visual Basic .NET et JScript .NET.  Cet attribut est facultatif.  
  
#### CodeBehind  
 Spécifie le fichier source qui implémente le service Web XML, lorsque la classe implémentant le service Web XML ne réside pas dans le même fichier et n'a pas été compilée dans un assembly et placée dans le répertoire \\Bin.  
  
## Notes  
 Le <xref:System.ServiceModel.ServiceHost> utilisé pour héberger le service est un point d'extensibilité figurant dans le modèle de programmation [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)].  Un modèle de fabrique est utilisé pour instancier le <xref:System.ServiceModel.ServiceHost> car il peut s'agir d'un type polymorphe ne devant pas être instancié directement par l'environnement d'hébergement.  
  
 L'implémentation par défaut utilise <xref:System.ServiceModel.Activation.ServiceHostFactory> pour créer une instance de <xref:System.ServiceModel.ServiceHost>.  Vous pouvez toutefois fournir votre propre fabrique \(une qui renvoie votre hôte dérivé\) en spécifiant le nom de type CLR correspondant à l'implémentation de votre fabrique dans la directive [@ServiceHost](../../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md).  
  
 Pour utiliser votre propre fabrique hôte de service personnalisée au lieu de la fabrique par défaut, il vous suffit d'indiquer le nom de type dans la directive [@ServiceHost](../../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) de la manière suivante :  
  
```  
<% @ServiceHost Factory=”DerivedFactory” Service=”MyService” %>  
```  
  
 Surchargez les implémentations de fabrique le moins possible.  Si vous disposez d'une importante logique personnalisée, votre code est plus facilement réutilisable si vous intégrez cette logique à votre hôte et non à la fabrique.  
  
 Par exemple, pour activer un point de terminaison compatible AJAX pour `MyService`, spécifiez le <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> comme valeur de l'attribut `Factory` dans la directive [@ServiceHost](../../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md), au lieu <xref:System.ServiceModel.Activation.ServiceHostFactory> par défaut \(voir l'exemple suivant\).  
  
## Exemple  
  
```  
<% @ServiceHost   
Service="MyService"  
Language="C#"  
Debug="true"  
Factory="WebScriptServiceHostFactory"  
%>  
```  
  
## Voir aussi  
 [Custom Service Host](../../../../../docs/framework/wcf/samples/custom-service-host.md)