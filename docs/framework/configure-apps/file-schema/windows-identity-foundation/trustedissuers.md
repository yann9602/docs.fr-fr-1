---
title: "&lt;trustedIssuers&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d818c917-07b4-40db-9801-8676561859fd
caps.latest.revision: 7
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 7
---
# &lt;trustedIssuers&gt;
Configure la liste des certificats d'émetteur de confiance utilisé par le Registre de nom basé sur la configuration de l'émetteur \(<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>\).  
  
## Syntaxe  
  
```  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration>  
        <issuerNameRegistry>  
          <trustedIssuers>  
            <add thumbprint=xs:string name=xs:string>  
            <clear>  
            <remove thumbprint=xs:string>  
          </trustedIssuers>  
        </issuerNameRegistry>  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
 Aucun  
  
### Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|`<add thumbprint=xs:string name=xs:string>`|Ajoute un certificat à la collection d'émetteurs approuvés.  Le certificat est spécifié avec la `thumbprint` attribut.  Cet attribut est obligatoire et doit contenir le formulaire ASN.1 codée de l'empreinte de certificat.  Le `name` attribut est facultatif et peut être utilisé pour spécifier un nom convivial pour le certificat.|  
|`<clear>`|Efface tous les certificats de la collection d'émetteurs approuvés.|  
|`<remove thumbprint=xs:string>`|Supprime un certificat de la collection d'émetteurs approuvés.  Le certificat est spécifié avec la `thumbprint` attribut.  Cet attribut est obligatoire.|  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\< issuerNameRegistry \>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/issuernameregistry.md)|Configure le Registre de nom de l'émetteur. **Important:**  Le `type` attribut de la `<issuerNameRegistry>` élément doit faire référence à la <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> de classe pour le `<trustedIssuers>` élément doit être valide.|  
  
## Notes  
 Windows Identity Foundation \(WIF\) fournit une implémentation simple de la <xref:System.IdentityModel.Tokens.IssuerNameRegistry> classe prêts à l'emploi, la <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> classe.  Le Registre de nom de configuration émetteur gère une liste d'éditeurs de confiance qui est chargée à partir de la configuration.  La liste associe chaque nom de l'émetteur du certificat X.509 qui est nécessaire pour vérifier la signature de jetons produites par l'émetteur.  La liste des certificats de l'émetteur de confiance est spécifiée sous la `<trustedIssuers>` élément.  Chaque élément dans la liste associe un nom mnémonique de l'émetteur du certificat X.509 qui est nécessaire pour vérifier la signature de jetons produites par cet émetteur.  Certificats de confiance sont spécifiés à l'aide de la ASN.1 codé forme de l'empreinte de certificat et sont ajoutés de la collection à l'aide de `<add>` élément.  Vous pouvez effacer ou supprimer des émetteurs \(certificats\) dans la liste à l'aide de la `<clear>` et `<remove>` éléments.  
  
 Le `type` attribut de la `<issuerNameRegistry>` élément doit faire référence à la <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> de classe pour le `<trustedIssuers>` élément doit être valide.  
  
## Exemple  
 Le code XML suivant montre comment spécifier l'émetteur de la configuration de base de Registre de nom.  
  
```  
<issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
  <trustedIssuers>  
    <add thumbprint="9B74CB2F32 … B1DC01EF40D0" name="LocalSTS" />  
  </trustedIssuers>  
</issuerNameRegistry>  
  
```  
  
## Voir aussi  
 <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>   
 <xref:System.IdentityModel.Tokens.IssuerNameRegistry>