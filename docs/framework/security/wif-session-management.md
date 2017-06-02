---
title: "Gestion de session WIF | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 98bce126-18a9-401b-b20d-67ee462a5f8a
caps.latest.revision: 7
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 7
---
# Gestion de session WIF
Lorsqu'un client essaie d'abord d'accéder à une ressource protégée hébergée par une partie de confiance, le client doit d'abord s'authentifier à un service d'émission de jeton de sécurité \(STS\) approuvé par la partie de confiance.  STS fournit ensuite un jeton de sécurité au client.  Le client présente ce jeton à la partie de confiance, qui accorde l'accès client à la ressource protégée.  Toutefois, vous ne souhaitez pas que le client pour s'authentifier à nouveau STS pour chaque demande, notamment car elle ne peut pas même être sur le même ordinateur ou dans le même domaine que la partie de confiance.  À la place, IDENTITY Windows Foundation \(WIF\) pour générer le client et dans la partie de confiance une session dans laquelle le client utilise un jeton de sécurité de session pour s'authentifier à la partie de confiance pour toutes les demandes après la première demande.  La partie de confiance peut utiliser ce jeton de sécurité de session, qui est stocké dans un cookie, pour reconstruire <xref:System.Security.Claims.ClaimsPrincipal?displayProperty=fullName>du client.  
  
 STS définit une authentification du client doit fournir.  Toutefois, le client peut avoir plusieurs informations d'identification avec lesquelles il peut s'authentifier à STS.  Par exemple, il peut avoir un jeton Windows Live, un nom d'utilisateur et un mot de passe, un certificat, et un smartkey.  Dans ce cas, STS accorde au client plusieurs identités, chaque identité correspondant à l'une des informations d'identification que le client présente.  La partie de confiance peut utiliser une ou plusieurs de ces identités lorsqu'elle décide le niveau d'accès pour accorder le client.  
  
 <xref:System.IdentityModel.Tokens.SessionSecurityToken?displayProperty=fullName> est utilisé pour reconstruire <xref:System.Security.Claims.ClaimsPrincipal?displayProperty=fullName>du client, qui contient les identités de tout le client dans <xref:System.Security.Claims.ClaimsPrincipal.Identities%2A>.  Chaque <xref:System.Security.Claims.ClaimsIdentity?displayProperty=fullName> dans la collection contient les jetons de démarrage qui sont associés à cette identité.  
  
 Si un nouveau jeton de session est émise avec l'ID de session du jeton d'origine de session, <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler?displayProperty=fullName> ne met pas à jour la marque de session dans le cache de jeton.  Vous devez toujours instancier un jeton de session avec un ID de session  
  
> [!NOTE]
>  Session.SecurityTokenHandler.ReadToken lève une exception d' <xref:System.Xml.XmlException> s'il reçoit l'entrée non valide ; par exemple, si le cookie qui contient le jeton de session est endommagé.  Nous recommandons que vous interceptez cette exception et fournissez le comportement spécifique à l'application.  
  
 Si une page Web protégée contient beaucoup de ressources \(telles que des petits graphiques\) qui sont également dans le champ protégé, le client doit signer s'authentifier à la partie de confiance pour télécharger chacune de ces ressources.  L'utilisation d'un jeton d'authentification de session éviter la nécessité d'authentifier à STS pour chaque demande, mais qui signifie toujours que de nombreux cookies sont envoyés sur.  Vous pouvez installer la page Web afin que les données et les ressources importantes sont stockées dans le champ protégé alors que les éléments mineurs sont stockés dans un domaine non protégé et liés à la propriété de la page Web principale.  En outre, définissez le chemin d'accès du cookie pour référencer uniquement le champ protégé.  
  
 Pour fonctionner en mode de référence, Microsoft recommande de fournir un gestionnaire pour l'événement d' <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.SessionSecurityTokenCreated> dans le fichier de **global.asax.cs** et de définir la propriété d' **IsReferenceMode** sur le jeton passé dans la propriété d' <xref:System.IdentityModel.Services.SessionSecurityTokenCreatedEventArgs.SessionToken%2A> .  Ces mises à jour garantiront que le jeton de session fonctionne en mode de référence pour chaque demande et est favorisée sur définir simplement la propriété d' <xref:System.IdentityModel.Services.SessionAuthenticationModule.IsReferenceMode%2A> sur le module d'authentification de session.  
  
## Extensibilité  
 Vous pouvez étendre le mécanisme de gestion de session.  Une raison de ceci est d'améliorer les performances.  Par exemple, vous pouvez créer un gestionnaire personnalisé de cookie qui transforme ou optimise le jeton de sécurité de session entre son état en mémoire et ce qu'entre dans le cookie.  Pour ce faire, vous pouvez configurer la propriété d' <xref:System.IdentityModel.Services.SessionAuthenticationModule.CookieHandler%2A?displayProperty=fullName> d' <xref:System.IdentityModel.Services.SessionAuthenticationModule?displayProperty=fullName> pour utiliser un gestionnaire personnalisé de cookie qui dérive d' <xref:System.IdentityModel.Services.CookieHandler?displayProperty=fullName>.  <xref:System.IdentityModel.Services.ChunkedCookieHandler?displayProperty=fullName> est le gestionnaire par défaut de cookie étant donné que les cookies dépassent la taille autorisée pour le protocole HTTP \(HTTP\) ; si vous utilisez un gestionnaire personnalisé de cookie à la place, vous devez implémenter le chunking.  
  
 Pour plus d'informations, consultez [ClaimsAwareWebFarm](http://go.microsoft.com/fwlink/?LinkID=248408) \(exemple de http:\/\/go.microsoft.com\/fwlink\/?LinkID\=248408\).  Cet exemple montre une ferme le cache prêt de session \(par opposition à un tokenreplycache\) afin que vous puissiez utiliser des sessions par référence au lieu d'échanger des grands cookies ; cet exemple illustre également une façon plus simple des cookies de sécurisation des dans une batterie de serveurs.  Le cache de session WCF\-est basé.  En ce qui concerne la sécurisation de session, l'exemple présente une nouvelle fonctionnalité dans WIF 4,5 d'une transformation de cookie sur MachineKey, qui peut être lancée en collant simplement l'extrait de code approprié dans le fichier web.config.  L'exemple lui\-même « n'est pas cultivé », mais il illustre des opérations nécessaires pour rendre votre application ferme\- prête.