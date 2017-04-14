---
title: "&lt;messageSenderAuthentication&gt;, &#233;l&#233;ment | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8d979dfc-a6f9-42ec-96d5-7fbc13a48118
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# &lt;messageSenderAuthentication&gt;, &#233;l&#233;ment
Spécifie les options d'authentification pour les expéditeurs du message du réseau pair à pair.  
  
 Pour plus d'informations sur la programmation pair à pair, consultez [Réseaux homologues](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).  
  
## Syntaxe  
  
```  
  
<messageSenderAuthentication  
customCertificateValidatorType= "namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"  
certificateValidationMode = "ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"  
revocationMode="NoCheck/Online/Offline"  
trustedStoreLocation="CurrentUser/LocalMachine"   
/>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|customCertificateValidatorType|Type et assembly utilisés pour valider un type personnalisé.  Cet attribut doit être défini lorsque `certificateValidationMode` a la valeur `Custom`.|  
|certifcateValidationMode|Spécifie l'un de trois modes utilisés pour valider des informations d'identification.  S'il est défini à `Custom`, un `customCertificateValidator` doit également être fourni.|  
|revocationMode|Un des modes utilisés pour vérifier des listes de certificat révoqués \(CRL\).|  
|trustedStoreLocation|L'un des deux emplacements du magasin du système : `LocalMachine` ou `CurrentUser`.  Cette valeur est utilisée lorsqu'un certificat de service est négocié au client.  La validation est exécutée sur le magasin **Personnes autorisées** dans l'emplacement de magasin spécifié.|  
  
## customCertificateValidatorType, attribut  
  
|Valeur|Description|  
|------------|-----------------|  
|Chaîne|Facultatif.  Spécifie le nom de type, l'assembly et d'autres données utilisées pour rechercher le type.  Au minimum, un espace de noms et un nom de type sont requis.  Les informations facultatives incluent : le nom de l'assembly, le numéro de version, la culture et le jeton de clé publique.|  
  
## certificateValidationMode, attribut  
  
|Valeur|Description|  
|------------|-----------------|  
|Énumération|Facultatif.  Une des valeurs suivantes : `None`, `PeerTrust`, `ChainTrust`, `PeerOrChainTrust` et `Custom`.  La valeur par défaut est `ChainTrust`.  La valeur par défaut est `ChainTrust`.<br /><br /> Pour plus d'informations, consultez [Utilisation des certificats](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).|  
  
## revocationMode, attribut  
  
|Valeur|Description|  
|------------|-----------------|  
|Énumération|Une des valeurs suivantes : `NoCheck`, `Online` et `Offline`.  La valeur par défaut est `Online`.<br /><br /> Pour plus d'informations, consultez [Utilisation des certificats](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).|  
  
## trustedStoreLocation, attribut  
  
|Valeur|Description|  
|------------|-----------------|  
|Énumération|Une des valeurs suivantes : `LocalMachine` ou `CurrentUser`.  La valeur par défaut est `CurrentUser`.  Si l'application cliente s'exécute sous un compte système, le certificat se trouve généralement dans `LocalMachine`.  Si l'application cliente s'exécute sous un compte d'utilisateur, le certificat se trouve généralement dans `CurrentUser`.  La valeur par défaut est `CurrentUser`.|  
  
### Éléments enfants  
 Aucun  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<peer\>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-clientcredentials-element.md)|Spécifie une information d'identification utilisée pour authentifier le client auprès d'un service homologue.|  
  
## Notes  
 Cet élément doit être configuré si l'authentification des messages est sélectionnée.  Pour les canaux de sortie, chaque message est signé à l'aide du certificat fourni par [\<certificate\>](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-element.md).  Avant d'être remis à l'application, tous les messages sont vérifiés par rapport aux informations d'identification de message à l'aide du validateur spécifié par l'attribut `customCertificateValidatorType` de cet élément.  Le validateur peut accepter ou rejeter les informations d'identification.  
  
## Exemple  
 Les jeux de codes suivants affectent le mode de validation de l'expéditeur du message à `PeerOrChainTrust`.  
  
```  
<behaviors>  
 <endpointBehaviors>  
  <behavior name="MyEndpointBehavior">  
   <clientCredentials>  
    <peer>  
      <certificate findValue="www.contoso.com"   
                   storeLocation="LocalMachine"  
                   x509FindType="FindByIssuerName" />  
        <messageSenderAuthentication   
          certificateValidationMode="PeerOrChainTrust" />  
       <messageSenderAuthentication certificateValidationMode="None" />  
    </peer>  
   </clientCredentials>  
  </behavior>  
 </endpointBehaviors>  
```  
  
## Voir aussi  
 <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>   
 <xref:System.ServiceModel.Security.PeerCredential.MessageSenderAuthentication%2A>   
 <xref:System.ServiceModel.Configuration.PeerCredentialElement.MessageSenderAuthentication%2A>   
 <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>   
 [Utilisation des certificats](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)   
 [Réseaux homologues](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)   
 [Peer Channel Message Authentication](http://msdn.microsoft.com/fr-fr/80e73386-514e-4c30-9e4a-b9ca8c173a95)   
 [Peer Channel Custom Authentication](http://msdn.microsoft.com/fr-fr/4aa8a82e-41a8-48e2-8621-7e1cbabdca7c)   
 [Sécurisation des applications de canal homologue](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)