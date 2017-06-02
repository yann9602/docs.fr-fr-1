---
title: "&lt;wsFederation&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c537f770-68bd-4f82-96ad-6424ad91369f
caps.latest.revision: 8
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 8
---
# &lt;wsFederation&gt;
Fournit la configuration pour le <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> \(WSFAM\).  
  
## Syntaxe  
  
```  
<system.identityModel.services>  
  <federationConfiguration>  
    <wsFederation authenticationType=xs:string (URI)  
        freshness=xs:decimal  
        homerealm=xs:string (URI)  
        issuer=xs:string (URI)  
        persistentCookiesOnPassiveRedirects=xs:boolean  
        passiveRedirectEnabled=xs:boolean  
        policy=xs:string (URI)  
        realm=xs:string (URI)  
        reply=xs:string (URI)  
        request=xs:string (URI)  
        requestPtr=xs:string (URI)  
        requireHttps=xs:boolean  
        resource=xs:string (URI)  
        signInQueryString=xs:string  
        signOutQueryString=xs:string  
        signOutReply=xs:string (URL)  
    </wsFederation>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|authenticationType|URI qui spécifie le type d'authentification.  Définit le paramètre de wauth WS\-Federation sign\-in de demande.  Facultatif.  La valeur par défaut est une chaîne vide, qui spécifie que le paramètre wauth n'est pas inclus dans la demande.|  
|fraîcheur|L'âge maximal souhaité des demandes d'authentification, en quelques minutes.  Définit le paramètre wfresh de WS\-Federation sign\-in de demande.  Facultatif.  La valeur par défaut est zéro.  Facultatif. **Warning:**  Dans la prochaine version de.NET Framework 4.5, la `freshness` attribut sera de type `xs:string` et sa valeur par défaut sera `null`.|  
|homeRealm|Le domaine Kerberos d'accueil du fournisseur d'identité \(IP\) à utiliser pour l'authentification.  Définit le paramètre Wh de WS\-Federation sign\-in de demande.  Facultatif.  La valeur par défaut est une chaîne vide, qui spécifie que le paramètre Wh n'est pas inclus dans la demande.|  
|issuer|L'URI de l'émetteur du jeton voulu.  Définit l'URL du WS\-Federation base sign\-in demandes et déconnexion obligatoire.|  
|persistentCookiesOnPassiveRedirects|Spécifie si les cookies persistants sont émis sur l'authentification.  Facultatif.  La valeur par défaut est « false », les cookies ne sont pas émises.|  
|passiveRedirectEnabled|Spécifie si le WSFAM est activé pour rediriger automatiquement les demandes non autorisées à un STS.  Facultatif.  La valeur par défaut est « true », les demandes non autorisées sont automatiquement redirigés.|  
|policy|Une URL qui spécifie l'emplacement de la stratégie appropriée à utiliser sur les demandes de connexion.  La valeur par défaut est une chaîne vide.  Définit le paramètre de wp WS\-Federation sign\-in de demande.  Facultatif.  La valeur par défaut est une chaîne vide, qui spécifie que le paramètre wp n'est pas inclus dans la demande.|  
|realm|L'URI du domaine demandeur.  \(Un URI qui identifie la partie utilisatrice \(RP\) pour le service de jeton de sécurité \(STS\).\) Définit le paramètre de demande de wtrealm WS\-Federation sign\-in de demande.  Obligatoire.|  
|réponse|Une URL qui identifie l'adresse à laquelle l'application \(RP\) partie utilisatrice aimerait recevoir les réponses à partir du Service STS \(Security Token\).  Définit le paramètre wreply de WS\-Federation sign\-in de demande.  Facultatif.  La valeur par défaut est une chaîne vide, qui spécifie que le paramètre wreply n'est pas inclus dans la demande.|  
|demande|La demande d'émission du jeton.  Définit le paramètre de wreq WS\-Federation sign\-in de demande.  Facultatif.  La valeur par défaut est une chaîne vide, qui spécifie que le paramètre wreq n'est pas inclus dans la demande.  Non compris la wreq ou le paramètre wreqptr dans la demande implique que le STS sait quel type de jeton à émettre.|  
|requestPtr|Une URL qui spécifie l'emplacement de la demande d'émission du jeton.  Définit le paramètre wreqptr de demande.  Facultatif.  La valeur par défaut est une chaîne vide, qui spécifie que le paramètre wreqptr n'est pas inclus dans la demande.  Non compris la wreq ou le paramètre wreqptr dans la demande implique que le STS sait quel type de jeton à émettre.|  
|requireHttps|Spécifie si la communication avec le service de jeton de sécurité \(STS\) doit utiliser le protocole HTTPS.  Facultatif.  La valeur par défaut est « true », HTTPS doit être utilisé.|  
|ressource|Un URI qui identifie la ressource accédée, la partie utilisatrice \(RP\), à la pour le service de jeton de sécurité \(STS\).  Facultatif.  Définit le paramètre wres de WS\-Federation sign\-in de demande.  Facultatif.  La valeur par défaut est une chaîne vide, qui spécifie que le paramètre wres n'est pas inclus dans la demande. **Note:**  WRES est un paramètre hérité.  Spécifier la `realm` attribut pour utiliser le paramètre wtrealm à la place.|  
|signInQueryString|Fournit un point d'extensibilité pour spécifier les paramètres de requête d'application définie dans l'URL de demande de signe WS\-Federation.  Facultatif.  La valeur par défaut est une chaîne vide, ce qui indique qu'aucun paramètre supplémentaire ne doit être incluse dans la demande.  Les paramètres sont spécifiés comme un fragment de chaîne de requête à l'aide de la forme suivante : `“param1=value1&param2=value2&param3=value3”` et ainsi de suite. **Note:**  Dans un fichier de configuration du » & « caractère de la chaîne de requête doit être spécifié à l'aide de sa référence d'entité, `&`.|  
|signOutQueryString|Fournit un point d'extensibilité pour spécifier les paramètres de requête d'application définie dans l'URL de demande de signe WS\-Federation.  Facultatif.  La valeur par défaut est une chaîne vide, ce qui indique qu'aucun paramètre supplémentaire ne doit être incluse dans la demande.  Les paramètres sont spécifiés comme un fragment de chaîne de requête à l'aide de la forme suivante : `“param1=value1&param2=value2&param3=value3”` et ainsi de suite. **Note:**  Dans un fichier de configuration du » & « caractère de la chaîne de requête doit être spécifié à l'aide de sa référence d'entité, `&`.|  
|signOutReply|Spécifie l'URL vers laquelle le client doit être redirigé par le service de jeton de sécurité \(STS\) lors de la déconnexion par le biais du protocole WS\-Federation passive.  Définit le paramètre wreply sur une demande de déconnexion de WS\-Federation.  Facultatif.  La valeur par défaut est une chaîne vide, ce qui indique qu'aucun paramètre supplémentaire ne doit être incluse dans la demande.|  
  
### Éléments enfants  
 Aucun  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<federationConfiguration\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md)|Contient les paramètres qui configurent le <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> \(WSFAM\) et le <xref:System.IdentityModel.Services.SessionAuthenticationModule> \(SAM\).|  
  
## Notes  
 Vous pouvez utiliser le `<wsFederation>` élément pour configurer les paramètres par défaut WS\-Federation et le comportement par défaut pour le WSFAM.  Configuration WS\-Federation des paramètres définies sous le `<wsFederation>` ensemble d'éléments équivalentes propriétés exposées par la <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> classe.  Ces propriétés restent les mêmes pour chaque demande émise par le WSFAM.  Vous pouvez modifier les paramètres de WS\-Federation dynamiquement lors de la demande de traitement en ajoutant des gestionnaires d'événements pour les événements exposés par WSFAM ; par exemple, la <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.RedirectingToIdentityProvider> événement.  Pour plus d'informations, consultez la documentation de la classe <xref:System.IdentityModel.Services.WSFederationAuthenticationModule>.  
  
 Le `<wsFederation>` élément est représenté par la <xref:System.IdentityModel.Services.Configuration.WSFederationElement> classe.  L'objet de configuration est représenté par la <xref:System.IdentityModel.Services.Configuration.WSFederationConfiguration> classe.  Un seul <xref:System.IdentityModel.Services.Configuration.WSFederationConfiguration> instance est définie sur le <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> objet est accessible via la <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=fullName> propriété et fournit la configuration pour le WSFAM.  
  
## Exemple  
 Le XML suivant un `<wsFederation>` élément qui spécifie les paramètres pour le WSFAM.  
  
> [!WARNING]
>  Dans cet exemple, le WSFAM n'est pas requis pour utiliser le protocole HTTPS.  C'est parce que le `requireHttps` d'attribut sur le `<wsFederation>` élément a la valeur `false`.  Ce paramètre n'est pas recommandé pour la plupart des environnements de production tel qu'il peut présenter un risque de sécurité.  
  
```  
<wsFederation passiveRedirectEnabled="true"   
  issuer="http://localhost:15839/wsFederationSTS/Issue"   
  realm="http://localhost:50969/"   
  reply="http://localhost:50969/"   
  requireHttps="false"   
  signOutReply="http://localhost:50969/SignedOutPage.html"   
  signOutQueryString="Param1=value2&Param2=value2"   
  persistentCookiesOnPassiveRedirects="true" />  
  
```  
  
## Voir aussi  
 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule>   
 <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=fullName>