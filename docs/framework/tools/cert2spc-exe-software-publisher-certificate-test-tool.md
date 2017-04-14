---
title: "Cert2spc.exe (Software Publisher Certificate Test Tool) | Microsoft Docs"
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
  - "SPC"
  - "Software Publisher Certificate Test tool"
  - "Software Publisher Certificate"
  - "Cert2spc.exe"
  - "certificates, Software Publisher's Certificate"
ms.assetid: be434d7d-9c0d-46e7-8392-58a9b542d11d
caps.latest.revision: 21
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 21
---
# Cert2spc.exe (Software Publisher Certificate Test Tool)
L'outil Software Publisher Certificate Test \(Test de certificat d'édition de logiciel\) crée un certificat d'édition de logiciel SPC \(Software Publisher's Certificate\) à partir d'un ou plusieurs certificats X.509.  Cert2spc.exe doit être utilisé à des fins de test uniquement.  Vous pouvez vous procurer un certificat SPC valide auprès d'une autorité de certification comme VeriSign ou Thawte.  Pour plus d'informations sur la création de certificats X.509, consultez [Makecert.exe \(Certificate Creation Tool\)](../Topic/Makecert.exe%20\(Certificate%20Creation%20Tool\).md).  
  
 Cet outil est installé automatiquement avec Visual Studio.  Pour exécuter l'outil, utilisez l'invite de commandes développeur \(ou l'invite de commandes Visual Studio dans Windows 7\).  Pour plus d'informations, consultez [Invites de commandes](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
 À l'invite de commandes, tapez le texte suivant :  
  
## Syntaxe  
  
```  
  
cert2spc cert1.cer | crl1.crl [... certN.cer | crlN.crl] outputSPCfile.spc  
```  
  
#### Paramètres  
  
|Argument|Description|  
|--------------|-----------------|  
|`certN.cer`|Nom d'un certificat X.509 à inclure dans le fichier SPC.  Vous pouvez spécifier plusieurs noms séparés par des espaces.|  
|`crlN.crl`|Nom d'une liste de révocation de certificats à inclure dans le fichier SPC.  Vous pouvez spécifier plusieurs noms séparés par des espaces.|  
|`outputSPCfile.spc`|Nom de l'objet PKCS \#7 qui contiendra les certificats X.509.|  
  
|Option|Description|  
|------------|-----------------|  
|**\/?**|Affiche la syntaxe et les options de commande de l'outil.|  
  
## Exemples  
 La commande suivante crée un fichier SPC à partir de `myCertificate.cer` et le place dans `mySPCFile.spc`.  
  
```  
cert2spc myCertificate.cer mySPCFile.spc  
```  
  
 La commande suivante crée un fichier SPC à partir de `oneCertificate.cer` et `twoCertificate.cer` et le place dans `mySPCFile.spc`.  
  
```  
cert2spc oneCertificate.cer twoCertificate.cer mySPCFile.spc  
```  
  
## Voir aussi  
 [Tools](../../../docs/framework/tools/index.md)   
 [Makecert.exe \(Certificate Creation Tool\)](../Topic/Makecert.exe%20\(Certificate%20Creation%20Tool\).md)   
 [Invites de commandes](../../../docs/framework/tools/developer-command-prompt-for-vs.md)