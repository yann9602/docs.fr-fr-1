---
title: "Conventions de sch&#233;ma de configuration de WIF | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f7864356-f72f-4cae-995c-18e0431f8a58
caps.latest.revision: 3
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 3
---
# Conventions de sch&#233;ma de configuration de WIF
Cette rubrique présente les conventions utilisées dans tous les rubriques de configuration de Windows IDENTITY Foundation \(WIF\) et décrit certaines fonctionnalités communes et attributs utilisés dans [\<system.identityModel\>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel.md) les sections et de [\<system.identityModel.services\>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md) .  
  
<a name="BKMK_Modes"></a>   
## Modes  
 La plupart des éléments de configuration de WIF ont un attribut d' `mode` .  Cet attribut contrôle en général la classe est utilisée pour effectuer une partie spécifique de traitement et les éléments de configuration sont autorisés en tant qu'éléments enfants de l'élément actuel.  Une erreur de configuration sera levée si les éléments inclus dans le fichier de configuration sont ignorés en raison de les paramètres d'état.  
  
<a name="BKMK_TimespanValues"></a>   
## Valeurs timespan  
 Où <xref:System.TimeSpan> est utilisé lorsque le type d'un attribut, consultez la méthode d' <xref:System.TimeSpan.Parse%28System.String%29> pour afficher le format autorisé.  Ce format est conforme à la spécification suivant.  
  
```  
[ws][-]{ d | [d.]hh:mm[:ss[.ff]] }[ws]  
```  
  
 Par exemple, « 30 ", « 30.00:00 », « 30,00 : 0h00 » un moyen 30 jours ; et 0h05 «  », « 0h05 : 00 ", « 0.00:05 : 00,00 " tous moyen 5 minutes.  
  
<a name="BKMK_CertificateReferences"></a>   
## Références de certificat  
 Plusieurs références de prise d'éléments à des certificats à l'aide de l'élément d' `<certificateReference>` .  En référençant un certificat, les attributs suivants sont disponibles.  
  
|||  
|-|-|  
|`storeLocation`|Une valeur de l'énumération d' <xref:System.Security.Cryptography.X509Certificates.StoreLocation> : `CurrentUser` ou `CurrentMachine`.|  
|`storeName`|Une valeur de l'énumération d' <xref:System.Security.Cryptography.X509Certificates.StoreName> ; les plus utiles pour ce contexte sont `My` et `TrustedPeople`.|  
|`x509FindType`|Une valeur de l'énumération d' <xref:System.Security.Cryptography.X509Certificates.X509FindType> ; les plus utiles pour ce contexte sont `FindBySubjectName` et `FindByThumbprint`.  Pour éviter la possibilité de l'erreur, il est recommandé que le type d' `FindByThumbprint` soit utilisé dans des environnements de production.|  
|`findValue`|La valeur utilisée pour rechercher le certificat, selon l'attribut d' `x509FindType` .  Pour éviter la possibilité de l'erreur, il est recommandé que le type d' `FindByThumbprint` soit utilisé dans des environnements de production.  Lorsque `FindByThumbPrint` est spécifié, cet attribut prend une valeur qui est la forme de hexadécimal\- chaîne de l'empreinte du certificat ; par exemple, « 97249e1a5fa6bee5e515b82111ef524a4c91583f ».|  
  
<a name="BKMK_CustomTypeReferences"></a>   
## Type personnalisé références  
 Plusieurs types personnalisés de référence des éléments à l'aide de l'attribut d' `type` .  Cet attribut doit spécifier le nom du type personnalisé.  Pour référencer un type de le Global Assembly Cache \(GAC\), un nom fort doit être utilisé.  Pour référencer un type d'un assembly dans le dossier bin, une référence qualifiée simple d'assembly peut être utilisée.  Les types définis dans le répertoire d'App\_Code\/peuvent également être référencés en spécifiant simplement le nom de type sans qualifier l'assembly.  
  
 Les types personnalisés doivent être dérivés du type spécifié et ils doivent fournir un constructeur par défaut d' `public` arguments \(0\).  
  
## Voir aussi  
 [\<system.identityModel\>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel.md)   
 [\<system.identityModel.services\>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md)