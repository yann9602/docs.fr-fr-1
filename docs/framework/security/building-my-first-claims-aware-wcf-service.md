---
title: "G&#233;n&#233;ration de mon premier service WCF prenant en charge les revendications | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e0e6d091-9a97-4888-8f2c-cbcee42d90ee
caps.latest.revision: 7
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 7
---
# G&#233;n&#233;ration de mon premier service WCF prenant en charge les revendications
## S'applique à  
  
-   Windows Identity Foundation \(WIF\)  
  
-   Windows Communication Foundation \(WCF\)  
  
## Vue d'ensemble  
 Cette rubrique décrit le scénario de création des services WCF qui prennent en charge les revendications à l'aide de WIF.  Il y a généralement trois participants dans un scénario de service Web qui prend en charge les revendications : le service Web lui\-même, l'utilisateur final, et le service d'émission de jeton de sécurité \(STS\).  L'illustration suivante décrit ce scénario :  
  
 ![Service WIF Basic Claims Aware WCF](../../../docs/framework/security/media/wifbasicclaimsawarewcfservice.png "WIFBasicClaimsAwareWCFService")  
  
1.  Le client du service WCF \(parfois appelé agent\) utilise WIF pour envoyer les informations d'identification à STS et une fois l'authentification réussie, un jeton est émis par STS pour l'agent.  
  
2.  L'agent envoie ce jeton émis par STS au service WCF.  
  
3.  Le service WCF qui prend en charge les revendications est configuré pour approuver STS et les jetons qu'il émet.  Le service WCF qui prend en charge les revendications utilise WIF pour valider le jeton et l'analyser.  Les développeurs utilisent l'API WIF et les types appropriés, par exemple, **ClaimsPrincipal** pour les besoins de l'application, tels que l'implémentation de l'autorisation pour ce dernier.  
  
 À partir de la version .NET 4.5, WIF fait partie du package .NET Framework.  Le fait d'avoir les classes WIF directement disponibles dans l'infrastructure elle\-même permet une intégration plus profonde de l'identité basée sur les revendications de la plateforme. NET, facilitant l'utilisation des revendications.  Avec WIF 4.5, vous n'avez pas besoin d'installer de composant hors plage pour démarrer le développement d'applications Web qui prennent en charge les revendications.  Les classes WIF sont maintenant réparties sur plusieurs assemblys, les principaux étant System.Security.Claims, System.IdentityModel et System.IdentityModel.Services.  
  
 STS est un service qui émet des jetons en cas de réussite de l'authentification.  Microsoft propose deux STS standard compatibles :  
  
-   [Active Directory Federation Services \(AD FS\) 2.0](http://go.microsoft.com/fwlink/?LinkID=247516) \(http:\/\/go.microsoft.com\/fwlink\/?LinkID\=247516\)  
  
-   [Microsoft Azure Access Control Service \(ACS\)](http://go.microsoft.com/fwlink/?LinkID=247517) \(http:\/\/go.microsoft.com\/fwlink\/?LinkID\=247517\).  
  
 AD FS 2.0 fait partie de Windows Server R2 et peut être utilisé comme un STS pour les scénarios sur site.  Azure Active Directory Access Control \(également appelé Service de contrôle d'accès ou ACS\) est un service cloud proposé dans le cadre de Microsoft Azure.  À des fins de test ou à titre éducatif, vous pouvez également utiliser d'autres STS pour générer des applications qui prennent en charge les revendications.  Par exemple, vous pouvez utiliser le développement STS local qui fait partie de l'[outil Identité et accès pour Visual Studio](http://go.microsoft.com/fwlink/?LinkID=245849) \(http:\/\/go.microsoft.com\/fwlink\/?LinkID\=245849\) qui est disponible gratuitement en ligne.  
  
 Pour générer votre premier service WCF prenant en charge les revendications à l'aide de WIF, consultez [How To: Build Claims\-Aware WCF Service Using WIF](http://msdn.microsoft.com/fr-fr/431e6415-62ed-4a9f-af03-f14d2b4dfe6d).  
  
## Voir aussi  
 [Prise en main de WIF](../../../docs/framework/security/getting-started-with-wif.md)