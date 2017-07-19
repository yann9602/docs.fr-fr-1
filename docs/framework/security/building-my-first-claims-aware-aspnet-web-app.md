---
title: "Cr&#233;ation de ma premi&#232;re application web ASP.NET prenant en charge les revendications | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3ee8ee7f-caba-4267-9343-e313fae2876d
caps.latest.revision: 5
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 5
---
# Cr&#233;ation de ma premi&#232;re application web ASP.NET prenant en charge les revendications
## S'applique à  
  
-   Windows Identity Foundation \(WIF\)  
  
-   ASP.NET  
  
 Cette rubrique décrit le scénario de création des applications Web qui prennent en charge les revendications ASP.NET à l'aide de WIF.  Il y a généralement trois participants dans un scénario d'application qui prend en charge les revendications : l'application elle\-même, l'utilisateur final et le service d'émission de jeton de sécurité \(STS\).  L'illustration suivante décrit ce scénario :  
  
 ![Application web basique WIF](../../../docs/framework/security/media/wifbasicwebapp.png "WIFBasicWebApp")  
  
1.  L'application prenant en charge les revendications utilise WIF pour identifier des demandes non authentifiées et pour les rediriger vers STS.  
  
2.  L'utilisateur final fournit les informations d'identification à STS et une fois qu'il est authentifié, un jeton est émis par STS pour l'utilisateur.  
  
3.  L'utilisateur est redirigé à partir de STS vers l'application prenant en charge les revendications avec le jeton publié par STS dans la demande.  
  
4.  L'application qui prend en charge les revendications est configurée pour approuver STS et les jetons qu'il émet.  L'application qui prend en charge les revendications utilise WIF pour valider le jeton et l'analyser.  Les développeurs utilisent l'API WIF et les types appropriés \(par exemple **ClaimsPrincpal**\) pour les besoins de l'application, tels que l'implémentation de l'autorisation pour cette dernière.  
  
 À partir de la version .NET 4.5, WIF fait partie du package .NET Framework.  Le fait d'avoir les classes WIF directement disponibles dans l'infrastructure elle\-même permet une intégration plus profonde de l'identité basée sur les revendications de la plateforme. NET, facilitant l'utilisation des revendications.  Avec WIF 4.5, vous n'avez pas besoin d'installer de composant hors plage pour démarrer le développement d'applications Web qui prennent en charge les revendications.  Les classes WIF sont maintenant réparties sur plusieurs assemblys, les principaux étant System.Security.Claims, System.IdentityModel et System.IdentityModel.Services.  
  
 STS est un service qui émet des jetons en cas de réussite de l'authentification.  Microsoft propose deux STS standard compatibles :  
  
-   [Active Directory Federation Services \(AD FS\) 2.0](http://go.microsoft.com/fwlink/?LinkID=247516) \(http:\/\/go.microsoft.com\/fwlink\/?LinkID\=247516\)  
  
-   [Microsoft Azure Access Control Service \(ACS\)](http://go.microsoft.com/fwlink/?LinkID=247517) \(http:\/\/go.microsoft.com\/fwlink\/?LinkID\=247517\).  
  
 AD FS 2.0 fait partie de Windows Server R2 et peut être utilisé comme un STS pour les scénarios sur site.  ACS est un service Cloud, proposé dans le cadre de la plateforme Microsoft Azure.  À des fins de test ou à titre éducatif, vous pouvez également utiliser d'autres STS pour générer des applications qui prennent en charge les revendications.  Par exemple, vous pouvez utiliser le développement STS local qui fait partie de l'outil [Identité et accès pour Visual Studio](http://go.microsoft.com/fwlink/?LinkID=245849) \(http:\/\/go.microsoft.com\/fwlink\/?LinkID\=245849\) qui est disponible gratuitement en ligne.  
  
 Pour créer votre première application ASP.NET. NET prenant en charge les revendications à l'aide de WIF, suivez les instructions de l'une des opérations suivantes :  
  
-   [Comment : générer une application web ASP.NET MVC prenant en charge les revendications à l’aide de WIF](../../../docs/framework/security/how-to-build-claims-aware-aspnet-mvc-web-app-using-wif.md)  
  
-   [Comment : générer une application Web Forms ASP.NET prenant en charge les revendications à l’aide de WIF](../../../docs/framework/security/how-to-build-claims-aware-aspnet-web-forms-app-using-wif.md)  
  
-   [Comment : générer une application ASP.NET prenant en charge les revendications à l’aide de l’authentification basée sur les formulaires](../../../docs/framework/security/claims-aware-aspnet-app-forms-authentication.md)  
  
## Voir aussi  
 [Prise en main de WIF](../../../docs/framework/security/getting-started-with-wif.md)