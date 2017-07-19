---
title: "&lt; issuerNameRegistry &gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 58b39d12-c953-40c4-88af-d7eb3343ca28
caps.latest.revision: 13
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 12
---
# &lt; issuerNameRegistry &gt;
Configure le Registre de nom de l'émetteur qui est utilisé par les gestionnaires dans la collection de gestionnaires de jeton.  
  
## Syntaxe  
  
```  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration>  
        <issuerNameRegistry type=xs:string>  
          <optionalCustomConfigurationElements />  
        </issuerNameRegistry>  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|type|Un type qui dérive de la <xref:System.IdentityModel.Tokens.IssuerNameRegistry> classe.  Pour plus d'informations sur la façon de spécifier un personnalisé `type`, voir [Custom Type References](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md#BKMK_CustomTypeReferences).|  
  
### Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<trustedIssuers\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/trustedissuers.md)|Lors de la `type` attribut spécifie le Registre de nom basé sur la configuration de l'émetteur \(le <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> classe\), le [\<trustedIssuers\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/trustedissuers.md) élément doit être spécifié.  Le [\<trustedIssuers\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/trustedissuers.md) élément peut prendre `<add>`, `<clear>`, ou `<remove>` éléments comme éléments enfants.|  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<securityTokenHandlerConfiguration\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|Fournit les gestionnaires de jetons de configuration pour une collection de sécurité.|  
  
## Notes  
 Tous les jetons de l'émetteur sont validés à l'aide d'un Registre de nom de l'émetteur.  Il s'agit d'un objet qui dérive de la <xref:System.IdentityModel.Tokens.IssuerNameRegistry> classe.  Le Registre de nom de l'émetteur est utilisé pour associer un nom mnémonique pour le matériel cryptographique qui est nécessaire pour vérifier les signatures de jetons produites par l'émetteur correspondant.  Le Registre de nom d'émetteur gère une liste d'émetteurs approuvés par l'application \(RP\) partie utilisatrice.  Le type de l'enregistrement de nom de l'émetteur est spécifié à l'aide de la `type` attribut.  Le `<issuerNameRegistry>` élément peut avoir un ou plusieurs éléments enfants qui fournissent la configuration pour le type spécifié.  Vous fournissez la logique qui traite ces éléments enfants en substituant la <xref:System.IdentityModel.Tokens.IssuerNameRegistry.LoadCustomConfiguration%2A> méthode.  
  
 WIF fournit un seul émetteur nom registre type prêts à l'emploi, la <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> classe.  Cette classe utilise un ensemble de certificats émetteur approuvé qui sont spécifiés dans la configuration.  Il nécessite un élément de configuration enfant, `<trustedIssuers>`, sous lequel la collection de certificats de l'émetteur de confiance est configurée.  Les certificats sont spécifiés à l'aide de la ASN.1 codé de forme de l'empreinte de certificat et est ajouté ou supprimé à partir de la collection à l'aide de confiance `<add>`, `<clear>`, ou `<remove>` éléments.  
  
 Le `<issuerNameRegistry>` élément est représenté par la <xref:System.IdentityModel.Configuration.IssuerNameRegistryElement> classe.  
  
> [!NOTE]
>  Spécifiant le `<issuerNameRegistry>` élément comme un élément enfant de le [\<identityConfiguration\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) élément a été dépréciée, mais est toujours pris en charge pour la compatibilité ascendante.  Paramètres de la `<securityTokenHandlerConfiguration>` élément prévalent sur ceux sur le `<identityConfiguration>` élément.  
  
## Exemple  
 Le code XML suivant montre comment spécifier l'émetteur de la configuration de base de Registre de nom.  
  
```  
<issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
  <trustedIssuers>  
    <add thumbprint="9B74CB … 1EF40D0" name="LocalSTS" />  
  </trustedIssuers>  
</issuerNameRegistry>  
  
```  
  
## Voir aussi  
 <xref:System.IdentityModel.Tokens.IssuerNameRegistry>   
 <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>