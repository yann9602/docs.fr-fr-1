---
title: "Comment&#160;: utiliser un moniker de service avec des contrats d&#39;&#233;change de m&#233;tadonn&#233;es | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c41a07e5-cb9d-45d6-9ea4-34511e227faf
caps.latest.revision: 11
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 11
---
# Comment&#160;: utiliser un moniker de service avec des contrats d&#39;&#233;change de m&#233;tadonn&#233;es
Après avoir développé de nouveaux services [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], vous pouvez décider que vous souhaitez être en mesure d'appeler ces services à partir d'un script ou d'une application Visual Basic 6.0.  Une méthode consisterait à générer un assembly client [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], à inscrire l'assembly avec COM, à installer l'assembly dans le Global Assembly Cache \(GAC\), puis à référencer les types COM à partir de votre code Visual Basic.  Lors de la distribution de l'application, vous devrez distribuer également l'assembly client [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  L'utilisateur devra ensuite inscrire l'assembly client WCF avec COM et le placer dans le GAC.  COM Interop [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] vous permet également d'effectuer les mêmes appels de service sans reposer sur un assembly client [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  Le moniker [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] vous permet d'appeler tout service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] à partir de tout langage compatible avec COM \(Visual Basic, VBScript, Visual Basic pour applications \(VBA\), et ainsi de suite\) en spécifiant un URI de point de terminaison d'échange de métadonnées \(Mex\) que le moniker de service utilise pour extraire des informations de type à propos du service.  Cette rubrique décrit comment appeler l'exemple [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] de Mise en route à l'aide d'un moniker [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] qui spécifie un point de terminaison Mex.  
  
> [!NOTE]
>  Les types définis par l'assembly client [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ne sont jamais réellement instanciés.  L'assembly est utilisé uniquement pour les métadonnées.  
  
### Utilisation du moniker de service avec une adresse Mex  
  
1.  Générez l'exemple de Mise en route et utilisez Internet Explorer pour naviguer jusqu'à son URL \(http:\/\/localhost\/ServiceModelSamples\/Service.svc\) afin de vous assurer que le service fonctionne.  
  
2.  Créez un script Visual Basic ou une application Visual Basic qui contient le code suivant :  
  
    ```  
    monString = "service:mexaddress=http://localhost/ServiceModelSamples/Service.svc/MEX"  
    monString = monString + ", address=http://localhost/ServiceModelSamples/Service.svc"  
    monString = monString + ", contract=ICalculator, contractNamespace=http://Microsoft.ServiceModel.Samples"  
    monString = monString + ", binding=WSHttpBinding_ICalculator, bindingNamespace=http://Microsoft.ServiceModel.Samples"  
  
    Set calc = GetObject(monString)  
    MsgBox calc.Add(3, 4)  
    ```  
  
3.  Exécutez l'application ou le script Visual Basic.  
  
    > [!NOTE]
    >  Le service que vous appelez doit exposer un point de terminaison Mex pour que le moniker soit en mesure de lire les métadonnées du service.  Pour plus d'informations, consultez [Comment : publier les métadonnées d'un service à l'aide d'un fichier de configuration](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md).  
  
    > [!NOTE]
    >  Si le moniker est mal formé ou si le service n'est pas disponible, l'appel à `GetObject` retourne une erreur indiquant que la syntaxe n'est pas valide.  Si vous recevez cette erreur, assurez\-vous que le moniker que vous utilisez est correct et que le service est disponible.  
  
## Voir aussi  
 [Comment : utiliser le moniker de service Windows Communication Foundation sans inscription](../../../../docs/framework/wcf/feature-details/use-the-wcf-service-moniker-without-registration.md)   
 [Comment : utiliser un moniker de service avec des contrats WSDL](../../../../docs/framework/wcf/feature-details/how-to-use-a-service-moniker-with-wsdl-contracts.md)