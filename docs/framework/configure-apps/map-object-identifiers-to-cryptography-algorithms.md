---
title: "Mappage d&#39;identificateurs d&#39;objet &#224; des algorithmes de chiffrement | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "algorithmes de chiffrement"
  - "chiffrement, mapper des identificateurs d'objet"
  - "signatures numériques"
  - "identificateurs, mapper des identificateurs d'objet"
  - "mapper des identificateurs d'objet"
ms.assetid: c9673f81-bf9e-47fd-bc6f-6bc1c1c4c15e
caps.latest.revision: 8
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 8
---
# Mappage d&#39;identificateurs d&#39;objet &#224; des algorithmes de chiffrement
Les signatures numériques garantissent l'impossibilité de falsifier des données lorsque celles\-ci sont transmises d'un programme vers un autre.  En général, une signature numérique est calculée par l'application d'une fonction mathématique au hachage des données à signer.  Lors de la mise en forme d'une valeur de hachage à signer, certains algorithmes de signature numérique ajoutent un OID \(Object Identifier\) ASN.1 en fin de chaîne dans le cadre de l'opération de mise en forme.  Cet OID identifie l'algorithme employé pour calculer le hachage.  Vous pouvez mapper des algorithmes à des identificateurs d'objet afin d'étendre le mécanisme de chiffrement à des algorithmes personnalisés.  L'exemple suivant montre comment mapper un identificateur d'objet à un nouvel algorithme de hachage.  
  
```  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass MyNewHash="MyNewHashClass, MyAssembly  
                  Culture='en', PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
            </cryptoClasses>  
            <nameEntry name="NewHash" class="MyNewHash"/>  
         </cryptoNameMapping>  
         <oidMap>  
            <oidEntry OID="1.3.14.33.42.46"  name="NewHash"/>  
         </oidMap>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
 L'élément [\<oidEntry\>.](../../../docs/framework/configure-apps/file-schema/cryptography/oidentry-element.md) contient deux attributs.  L'attribut **OID** est le numéro d'identification de l'objet.  L'attribut **name** est la valeur de l'attribut **name** de l'élement [\<nameEntry\>.](../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md).  Il doit exister un mappage d'un nom d'algorithme à une classe pour qu'un identificateur d'objet puisse être mappé à un nom simple.  
  
## Voir aussi  
 [Configuration de classes de chiffrement](../../../docs/framework/configure-apps/configure-cryptography-classes.md)   
 [Services de chiffrement](../../../docs/standard/security/cryptographic-services.md)