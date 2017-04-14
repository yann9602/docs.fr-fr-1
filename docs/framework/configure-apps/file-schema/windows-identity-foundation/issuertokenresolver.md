---
title: "&lt;issuerTokenResolver&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f74392f6-3f5b-4880-bd8a-3a9130d31e65
caps.latest.revision: 9
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 8
---
# &lt;issuerTokenResolver&gt;
Inscrit le résolveur de jeton émetteur qui est utilisé par les gestionnaires dans la collection de gestionnaires de jeton.  Le résolveur de jeton de l'émetteur est utilisé pour résoudre le jeton de signature sur les jetons et les messages entrants.  
  
## Syntaxe  
  
```  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration>  
        <issuerTokenResolver type=xs:string>  
        </issuerTokenResolver>  
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
|type|Spécifie le type du résolveur jeton émetteur.  Doit être soit la <xref:System.IdentityModel.Tokens.IssuerTokenResolver> classe ou un type qui dérive de la <xref:System.IdentityModel.Tokens.IssuerTokenResolver> classe.  Pour plus d'informations sur la façon de spécifier la `type` d'attribut, consultez [Custom Type References](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md#BKMK_CustomTypeReferences).  Obligatoire.|  
  
### Éléments enfants  
 Aucun  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<securityTokenHandlerConfiguration\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|Fournit les gestionnaires de jetons de configuration pour une collection de sécurité.|  
  
## Notes  
 Le résolveur de jeton de l'émetteur est utilisé pour résoudre le jeton de signature sur les jetons et les messages entrants.  Il est utilisé pour récupérer le matériel cryptographique qui est utilisé pour vérifier la signature.  Vous devez spécifier la `type` attribut.  Le type spécifié peut être soit <xref:System.IdentityModel.Tokens.IssuerTokenResolver> ou un type personnalisé qui dérive de la <xref:System.IdentityModel.Tokens.IssuerTokenResolver> classe.  
  
 Certains gestionnaires de jetons permettent de spécifier des paramètres du solveur jeton émetteur dans configuration.  Paramètres de gestionnaires de jetons individuels remplacent celles spécifiées dans la collection de gestionnaires de jeton de sécurité.  
  
> [!NOTE]
>  Spécifiant le `<issuerTokenResolver>` élément comme un élément enfant de le [\<identityConfiguration\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) élément a été dépréciée, mais est toujours pris en charge pour la compatibilité ascendante.  Paramètres de la `<securityTokenHandlerConfiguration>` élément prévalent sur ceux sur le `<identityConfiguration>` élément.  
  
## Exemple  
 Le code XML suivant montre la configuration d'un résolveur de jeton émetteur qui est basé sur une classe personnalisée qui dérive de <xref:System.IdentityModel.Tokens.IssuerTokenResolver>.  Le résolveur token gère un dictionnaire de paires de clés de l'audience qui est initialisé à partir d'un élément de configuration personnalisé \(`<AddAudienceKeyPair>`\) défini pour la classe.  La classe les remplacements de la <xref:System.IdentityModel.Selectors.SecurityTokenResolver.LoadCustomConfiguration%2A> méthode pour traiter cet élément.  La substitution est illustrée dans l'exemple suivant ; Toutefois, les méthodes qu'il appelle ne sont pas affichés par souci de concision.  Pour obtenir un exemple complet, consultez la `CustomToken` exemple.  
  
```  
<issuerTokenResolver type="SimpleWebToken.CustomIssuerTokenResolver, SimpleWebToken">  
  <AddAudienceKeyPair  symmetricKey="wAVkldQiFypTQ+kdNdGWCYCHRcee8XmXxOvgmak8vSY=" audience="http://localhost:19851/" />  
</issuerTokenResolver>  
```  
  
## Exemple  
  
```  
public override void LoadCustomConfiguration(System.Xml.XmlNodeList nodelist)  
{  
    foreach (XmlNode node in nodelist)  
    {  
        XmlDictionaryReader rdr = XmlDictionaryReader.CreateDictionaryReader(new XmlTextReader(new StringReader(node.OuterXml)));  
        rdr.MoveToContent();  
  
        string symmetricKey = rdr.GetAttribute("symmetricKey");  
        string audience = rdr.GetAttribute("audience");  
  
        this.AddAudienceKeyPair(audience, symmetricKey);  
    }  
}  
```  
  
## Voir aussi  
 <xref:System.IdentityModel.Tokens.IssuerTokenResolver>