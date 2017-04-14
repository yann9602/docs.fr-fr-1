---
title: "WSTrustChannelFactory et WSTrustChannel | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 96cec467-e963-4132-b18b-7d0b3a2e979f
caps.latest.revision: 9
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 9
---
# WSTrustChannelFactory et WSTrustChannel
Si vous êtes déjà familiarisé avec Windows Communication Foundation \(WCF\), vous savez qu'un client WCF est déjà fédération compatible.  En configurant un client WCF avec <xref:System.ServiceModel.WSFederationHttpBinding> ou une liaison personnalisée similaire, vous pouvez activer l'authentification fédérée un service.  
  
 WCF obtient le jeton qui est publié par le service d'émission de jeton de sécurité \(STS\) en arrière\-plan et utilise ce jeton pour authentifier au service.  La limitation principale de cette approche est qu'il n'existe aucun visibilité les communications du client avec le serveur.  WCF génère automatiquement le jeton de sécurité \(RST\) de requête à STS selon les paramètres de jeton émis sur la liaison.  Cela signifie que le client ne peut pas varier les paramètres de RST par demande, examiner la réponse \(RSTR\) de jeton de sécurité de demande pour obtenir des informations telles que des revendications d'affichage, ou placer le jeton en cache pour une utilisation ultérieure.  
  
 Actuellement, le client WCF convient pour les scénarios de base de fédération.  Toutefois, l'un des scénarios principaux que Windows Identity Foundation \(WIF\) prend en charge requiert le contrôle du RST à un niveau que WCF ne permet difficilement.  Par conséquent, WIF ajoute des fonctionnalités qui vous permettent de mieux contrôler la communication avec STS.  
  
 WIF prend en charge les scénarios suivants de fédération :  
  
-   Utilisation d'un client WCF sans toutes leurs dépendances de WIF à authentifier à un service fédéré  
  
-   Activation de WIF sur un client WCF pour insérer un ActAs ou l'élément OnBehalfOf dans le RST à STS  
  
-   Utilisation seul WIF pour obtenir un jeton de STS puis pour permettre à un client WCF pour authentifier avec ce jeton.  Pour plus d'informations, consultez [ClaimsAwareWebService](http://go.microsoft.com/fwlink/?LinkID=248406) l'exemple.  
  
 Le premier scénario est explicite : Les des clients WCF se poursuit avec les parties de confiance et STSs de WIF.  Cette rubrique décrit les scénarios restants.  
  
## Amélioration d'un client existant WCF avec ActAs\/OnBehalfOf  
 Dans un scénario courant de délégation d'identité, un client appelle un service de niveau intermédiaire, qui appelle ensuite un principal service.  Le service de niveau intermédiaire agit en tant que tel, ou agit au nom de, le client.  
  
> [!TIP]
>  Quelle est la différence entre ActAs et OnBehalfOf ?  
>   
>  Du point de procotol de WS\-Trust :  
>   
>  1.  Un élément d'ActAs RST indique que le demandeur souhaite un jeton qui contient des revendications de deux entités distinctes : le demandeur, et une entité externe représentée par le jeton de l'élément d'ActAs.  
> 2.  Un élément d'OnBehalfOf RST indique que le demandeur souhaite un jeton qui contient des revendications uniquement contrôler une entité : l'entité externe représentée par le jeton de l'élément OnBehalfOf.  
>   
>  La fonctionnalité d'ActAs est généralement utilisée dans des scénarios exigeant la délégation composite, où le destinataire final du jeton émis peut vérifier la chaîne entière de délégation et afficher non seulement le client, mais tous les intermédiaires.  Cela la permet de tester le contrôle d'accès, l'audit et d'autres activités connexes selon la chaîne de délégation d'identité entière.  La fonctionnalité d'ActAs est fréquemment utilisée dans les systèmes multicouches pour authentifier et passer des informations sur les identités entre les couches sans avoir à passer ces informations à l'application\/à couche de logique métier.  
>   
>  La fonctionnalité d'OnBehalfOf est utilisée dans des scénarios où uniquement l'identité du client d'origine est importante et est effectivement identique à la fonctionnalité d'emprunt d'identité disponible dans Windows.  Lorsque OnBehalfOf est utilisé, le destinataire final du jeton émis ne peut consulter des revendications sur le client d'origine, et les informations sur les intermédiaires ne sont pas conservées.  Un modèle commun lorsque la fonctionnalité d'OnBehalfOf est utilisée est le modèle de proxy où le client ne peut pas accéder STS directement mais plutôt communique via une passerelle de proxy.  La passerelle de proxy authentifie l'appelant et place les informations sur l'appelant l'élément OnBehalfOf du message de RST qu'il envoie ensuite valeur True STS pour traitement.  Le jeton résultant contient uniquement des revendications liées au client du proxy, rendant le proxy complètement transparent au récepteur du jeton émis. Notez que WIF ne prend pas en charge le \<wsse:SecurityTokenReference\> ou \<wsa:EndpointReferences\> comme enfant de \<wst:OnBehalfOf\>.  La spécification de WS\-Trust permet à trois façons identifient un demandeur d'origine \(au nom de qui le proxy agit\).  Il s'agit des valeurs suivantes :  
>   
>  -   Référence de jeton de sécurité.  Une référence à un jeton, dans le message, ou éventuellement extrait hors de la bande\).  
> -   Référence à un point de terminaison.  Utilisé comme clé dans les données de référence, de nouveau hors de la bande.  
> -   Jeton de sécurité.  Identifie le demandeur d'origine directement.  
>   
>  WIF prend uniquement en charge les jetons de sécurité, chiffrés ni déchiffrés, comme élément enfant direct du \<wst:OnBehalfOf\>.  
  
 Ces informations sont fournies à un émetteur du WS\-Trust à l'aide de éléments symboliques d'ActAs et d'OnBehalfOf dans le RST.  
  
 WCF expose un point d'extensibilité sur la liaison qui permet aux éléments XML arbitraires à ajouter au RST.  Cependant, le point d'extensibilité est bondé à la liaison, les scénarios nécessitant le contenu de RST à varier par appel doivent recréer le client pour chaque appel, ce qui diminue les performances.  WIF utilise des méthodes d'extension sur la classe `ChannelFactory` pour permettre aux développeurs de joindre n'importe quel jeton qui est obtenu à partir de la bande au RST.  L'exemple de code suivant explique comment prendre un jeton représentant le client \(jeton tel qu'un X.509, un nom d'utilisateur, ou en langage SAML \(SAML\)\) et l'attache au RST envoyé à l'émetteur.  
  
```  
IHelloService serviceChannel = channelFactory.CreateChannelActingAs<IHelloService>( clientSamlToken );  
serviceChannel.Hello(“Hi!”);  
```  
  
 WIF fournit les avantages suivants :  
  
-   Le RST peut être modifié par canal ; Par conséquent, les services de niveau intermédiaire ne doivent pas recréer la fabrique de canaux pour chaque client, qui améliore les performances.  
  
-   Cela fonctionne avec exister des clients WCF, qui rend un tracé de mise à jour simple possible pour exister des services de niveau intermédiaire WCF qui souhaitent activer la sémantique de délégation d'identité.  
  
 Toutefois, il ne reste aucune visibilité la communication entre le client avec STS.  Nous étudierons ces paramètres dans la troisième scénario.  
  
## Communication directement avec un émetteur et l'utilisation du jeton émis pour authentifier  
 Pour certains scénarios avancés, l'amélioration d'un client WCF ne suffit pas.  Développeurs qui utilisent uniquement le message d'utilisation de WCF généralement Dans\/contrats de message et gérez l'analyse côté client de la réponse d'émetteur manuellement.  
  
 WIF présente <xref:System.ServiceModel.Security.WSTrustChannelFactory> et les classes <xref:System.ServiceModel.Security.WSTrustChannel> pour laisser le client communiquer directement avec un émetteur du WS\-Trust.  Les classes <xref:System.ServiceModel.Security.WSTrustChannelFactory> et <xref:System.ServiceModel.Security.WSTrustChannel> Activer les objets fortement typés de RST et de RSTR au flux entre le client et l'émetteur, comme indiqué dans l'exemple de code suivant.  
  
```  
WSTrustChannelFactory trustChannelFactory = new WSTrustChannelFactory( stsBinding, stsAddress );  
WSTrustChannel channel = (WSTrustChannel) trustChannelFactory.CreateChannel();  
RequestSecurityToken rst = new RequestSecurityToken(RequestTypes.Issue);  
rst.AppliesTo = new EndpointAddress(serviceAddress);  
RequestSecurityTokenResponse rstr = null;  
SecurityToken token = channel.Issue(rst, out rstr);  
```  
  
 Notez que le paramètre `out` sur la méthode <xref:System.ServiceModel.Security.WSTrustChannel.Issue%2A> autorise l'accès au RSTR pour l'inspection côté client.  
  
 Jusqu'à présent, nous avons uniquement vu comment obtenir un jeton.  Le jeton retourné par l'objet <xref:System.ServiceModel.Security.WSTrustChannel> est un `GenericXmlSecurityToken` qui contient toutes les informations nécessaires pour l'authentification d'une partie de confiance.  L'exemple de code suivant montre comment utiliser ce jeton.  
  
```  
IHelloService serviceChannel = channelFactory.CreateChannelWithIssuedToken<IHelloService>( token ); serviceChannel.Hello(“Hi!”);  
```  
  
 La méthode d'extension de <xref:System.ServiceModel.ChannelFactory%601.CreateChannelWithIssuedToken%2A> sur l'objet `ChannelFactory` indique à WIF que vous avez obtenu un jeton hors de la bande, et qu'il doit arrêter l'appel normal WCF à l'émetteur et plutôt utiliser le jeton que vous avez obtenu pour authentifier sur la partie de confiance.  Cela offre les avantages suivants :  
  
-   Il vous permet de contrôler entièrement le processus symbolique d'émission.  
  
-   Il prend en charge les scénarios d'ActAs\/OnBehalfOf en définissant directement ces propriétés sur le RST sortant.  
  
-   Il active des décisions d'approbation côté client dynamiques d'être effectué au contenu du RSTR.  
  
-   Il vous permet de mettre en cache et réutiliser le jeton retourné par la méthode <xref:System.ServiceModel.Security.WSTrustChannel.Issue%2A>.  
  
-   <xref:System.ServiceModel.Security.WSTrustChannelFactory> et <xref:System.ServiceModel.Security.WSTrustChannel> permettent de contrôler la mise en cache du canal, du défaut, et la sémantique de récupération d'après les meilleures pratiques de WCF.  
  
## Voir aussi  
 [Fonctionnalités WIF](../../../docs/framework/security/wif-features.md)